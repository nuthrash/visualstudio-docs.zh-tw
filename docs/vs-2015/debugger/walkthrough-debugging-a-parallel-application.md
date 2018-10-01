---
title: 逐步解說： 偵錯平行應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22a4d8ea3bfe98a034f485be8ceec1004f8fba75
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489593"
---
# <a name="walkthrough-debugging-a-parallel-application"></a>逐步解說：偵錯平行應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[逐步解說： 偵錯平行應用程式](https://docs.microsoft.com/visualstudio/debugger/walkthrough-debugging-a-parallel-application)。  
  
本逐步解說示範如何使用**平行工作**並**平行堆疊**視窗來偵錯平行應用程式。 這些視窗可協助您了解，並確認使用的程式碼的執行階段行為[Task Parallel Library (TPL)](http://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)或[並行執行階段](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)。 本逐步解說提供具有內建中斷點的範例程式碼。 程式碼中斷之後，本逐步解說會示範如何使用**平行工作**並**平行堆疊**視窗來檢查。  
  
 本逐步解說教導下列工作：  
  
-   如何在一個檢視中檢視所有執行緒的呼叫堆疊。  
  
-   如何檢視應用程式中建立之 `System.Threading.Tasks.Task` 執行個體的清單。  
  
-   如何檢閱工作而非執行緒的實際呼叫堆疊。  
  
-   如何瀏覽至程式碼**平行工作**並**平行堆疊**windows。  
  
-   視窗如何透過分組、縮放和其他相關功能來處理比例調整。  
  
## <a name="prerequisites"></a>必要條件  
 本逐步解說假設**Just My Code**已啟用。 在上**工具**功能表上，按一下**選項**，展開**偵錯**節點中，選取**一般**，然後選取 **啟用Just My Code (僅限 Managed)**。 如果未設定這項功能，您仍然可以使用本逐步解說，但結果可能與插圖不同。  
  
## <a name="c-sample"></a>C# 範例  
 如果您使用 C# 範例，本逐步解說也會假設外部程式碼已隱藏。 若要切換是否顯示外部程式碼，以滑鼠右鍵按一下**名稱**的資料表標頭**呼叫堆疊**視窗中，然後選取或清除**顯示外部程式碼**。 如果未設定這項功能，您仍然可以使用本逐步解說，但結果可能與插圖不同。  
  
## <a name="c-sample"></a>C++ 範例  
 如果您使用 C++ 範例，則可以忽略本主題中對於外部程式碼的引述。 外部程式碼只適用於 C# 範例。  
  
## <a name="illustrations"></a>插圖  
 本主題中的插圖是在執行 C# 範例的四核心電腦上錄製。 雖然您可以使用其他組態來完成本逐步解說，但插圖可能與您電腦上所呈現的畫面不同。  
  
## <a name="creating-the-sample-project"></a>建立範例專案  
 本逐步解說中的範例程式碼適用於不執任何動作的應用程式。 目的只是要了解如何使用工具視窗來偵錯平行應用程式。  
  
#### <a name="to-create-the-sample-project"></a>建立範例專案  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。  
  
2.  在 **已安裝的範本** 窗格中，選取 Visual C#、 Visual Basic 或 Visual c + +。 至於 Managed 語言，請確定架構方塊中有顯示 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]。  
  
3.  選取 **主控台應用程式**，然後按一下**確定**。 保留偵錯組態，這是預設值。  
  
4.  在專案中開啟 .cpp、.cs 或 .vb 程式碼檔案。 刪除其內容，建立空白程式碼檔案。  
  
5.  將所選擇語言的下列程式碼貼到空白程式碼檔案中。  
  
 [!code-cpp[Debugger#1](../snippets/cpp/VS_Snippets_Misc/debugger/cpp/beta2_native.cpp#1)]
 [!code-csharp[Debugger#1](../snippets/csharp/VS_Snippets_Misc/debugger/cs/s.cs#1)]
 [!code-vb[Debugger#1](../snippets/visualbasic/VS_Snippets_Misc/debugger/vb/module1.vb#1)]  
  
1.  在 **檔案**功能表上，按一下**全部儲存**。  
  
2.  在 **建置**功能表上，按一下**重建方案**。  
  
     請注意，由於 `Debugger.Break` (C++ 範例中的 `DebugBreak`) 的呼叫有四個，因此，您不需要插入中斷點，只要執行應用程式就會在偵錯工具中斷最多四次。  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>使用平行堆疊視窗：執行緒檢視  
 按一下 [偵錯] 功能表上的 [開始偵錯]。 等待叫用第一個中斷點。  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>檢視單一執行緒的呼叫堆疊  
  
1.  在 **偵錯**功能表上，指向**Windows** ，然後按一下 **執行緒**。 停駐**執行緒**視窗底部的 Visual Studio。  
  
2.  在 **偵錯**功能表上，指向**Windows** ，然後按一下 **呼叫堆疊**。 停駐**呼叫堆疊**底部 Visual Studio 視窗。  
  
3.  按兩下中的執行緒**執行緒**使它成為目前的視窗。 目前執行緒具有黃色箭號。 當您變更目前的執行緒時，它的呼叫堆疊會顯示在**呼叫堆疊**視窗。  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>檢查平行堆疊視窗  
  
1.  在 **偵錯**功能表上，指向**Windows** ，然後按一下 **平行堆疊**。 請確定**執行緒**左上角的方塊中選取。  
  
     藉由使用**平行堆疊** 視窗中，您可以在一個檢視中同時檢視多個呼叫堆疊。 如下圖所示**平行堆疊**視窗上方**呼叫堆疊**視窗。  
  
     ![執行緒平行堆疊 視窗中的檢視](../debugger/media/pdb-walkthrough-1.png "PDB_Walkthrough_1")  
  
     主執行緒的呼叫堆疊會出現在一個方塊中，而其他四個執行緒的呼叫堆疊會一起出現在另一個方塊中。 四個執行緒形成一組是因為它們的堆疊框架共用相同的方法內容，也就是說，它們位於相同的方法中：`A`、`B` 和 `C`。 若要檢視執行緒 Id 和名稱的執行緒共用相同的方塊中，將滑鼠移至標頭 (**4 個執行緒**)。 目前執行緒以粗體顯示，如下圖所示。  
  
     ![顯示執行緒 Id 和名稱的工具提示](../debugger/media/pdb-walkthrough-1a.png "PDB_Walkthrough_1A")  
  
     黃色箭號表示目前執行緒的作用中堆疊框架。 若要取得詳細資訊，請將滑鼠游標停留於箭頭上。  
  
     ![作用中堆疊框架上的工具提示](../debugger/media/pdb-walkthrough-1b.png "PDB_Walkthrough_1B")  
  
     您可以設定要顯示的堆疊框架的詳細資料程度 (**模組名稱**，**參數型別**，**參數名稱**，**參數值**，**行號**並**位元組位移**) 以滑鼠右鍵按一下**呼叫堆疊**視窗。  
  
     方塊周圍的藍色醒目提示表示目前執行緒是該方塊的一部分。 工具提示中也以粗體堆疊框架來表示目前執行緒。 如果您按兩下主執行緒，在 [執行緒] 視窗中的，您可以觀察到中的藍色醒目提示**平行堆疊**視窗會隨之移動。  
  
     ![反白顯示 [平行堆疊] 視窗中的主執行緒](../debugger/media/pdb-walkthrough-1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>繼續執行至第二個中斷點為止  
  
1.  若要繼續執行，直到遇到的第二個中斷點，在**偵錯**功能表上，按一下**繼續**。 下圖顯示第二個中斷點上的執行緒樹狀。  
  
     ![顯示許多分支的 [平行堆疊] 視窗](../debugger/media/pdb-walkthrough-2.png "PDB_Walkthrough_2")  
  
     在第一個中斷點上，四個執行緒都是從 S.A 跳至 S.B，再跳至 S.C 方法。 在仍看到的資訊**平行堆疊** 視窗中，但四個執行緒已更往前。 其中一個繼續執行至 S.D，再執行至 S.E。 另一個繼續執行至 S.F、S.G 和 S.H。 其他兩個繼續執行至 S.I 和 S.J，而在這裡，其中一個跳至 S.K，另一個繼續執行至非使用者外部程式碼。  
  
     您可以暫留於方塊標題上，例如， **1 個執行緒**或是**2 個執行緒**，以查看執行緒的執行緒識別碼。 您可以將滑鼠游標停留於堆疊框架上，以查看執行緒 ID 和其他框架詳細資料。 藍色醒目提示表示目前執行緒，黃色箭號表示目前執行緒的作用中堆疊框架。  
  
     布條圖示 (與藍色和紅色波浪狀線條重疊) 表示非目前執行緒的作用中堆疊框架。 在 [**呼叫堆疊**] 視窗中，按兩下 S.B 來切換框架。 **平行堆疊**視窗使用綠色弧形箭號圖示來表示目前執行緒的目前的堆疊框架。  
  
     在**執行緒** 視窗中，切換執行緒並觀察中的檢視**平行堆疊**視窗隨即更新。  
  
     您可以使用中的捷徑功能表來切換至另一個執行緒，或另一個執行緒，另一個框架**平行堆疊**視窗。 例如，以滑鼠右鍵按一下 S.J，指向**切換至框架**，然後按一下 命令。  
  
     ![平行堆疊執行路徑](../debugger/media/pdb-walkthrough-2b.png "PDB_Walkthrough_2B")  
  
     以滑鼠右鍵按一下 S.C，並指向**切換至框架**。 其中一個命令有核取記號，表示目前執行緒的堆疊框架。 您可以切換至相同執行緒的該框架 (只有綠色箭號會移動)，也可以切換至另一個執行緒 (藍色醒目提示也會移動)。 下圖顯示子功能表。  
  
     ![含有 2 個選項，而目前已選取 J C 上的堆疊功能表](../debugger/media/pdb-walkthrough-3.png "PDB_Walkthrough_3")  
  
     方法內容只有一個堆疊框架相關聯時，方塊標題會顯示**1 個執行緒**並按兩下，可以切換到它。 如果您按兩下的方法內容有 1 個以上關聯的框架，則會自動出現功能表。 隨著您將滑鼠游標停留於方法內容上，請注意右邊的黑色三角形。 按一下該三角形也會顯示捷徑功能表。  
  
     對於具有許多執行緒的大型應用程式，您可能會想要只專注於其中一部分執行緒。 **平行堆疊**視窗可以顯示呼叫堆疊，只針對已標幟的執行緒。 在工具列上，按一下**僅顯示已標幟**清單方塊旁的按鈕。  
  
     ![清空 [平行堆疊] 視窗和工具提示](../debugger/media/pdb-walkthrough-3a.png "PDB_Walkthrough_3A")  
  
     接下來，在**執行緒** 視窗中，旗標的執行緒逐一查看其呼叫堆疊中顯示的方式**平行堆疊**視窗。 若要將執行緒加上旗標，請使用捷徑功能表或執行緒的第一個儲存格。 按一下 **僅顯示已標幟**工具列按鈕，再次以顯示所有執行緒。  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>繼續執行至第三個中斷點為止  
  
1.  若要繼續執行，直到遇到的第三個中斷點，在**偵錯**功能表上，按一下**繼續**。  
  
     當多個執行緒在相同方法中但方法不在呼叫堆疊的開頭時，方法會出現在不同方塊中。 位於目前中斷點的例子有 S.L，其中有三個執行緒，且分別出現在三個方塊中。 按兩下 S.L。  
  
     ![平行堆疊 視窗中的執行路徑](../debugger/media/pdb-walkthrough-3b.png "PDB_Walkthrough_3B")  
  
     請注意，S.L 在其他兩個方塊中是粗體，所以您可以看到它出現在其他地方。 如果您想要查看哪些框架呼叫 s.l 和它呼叫哪些框架，請按一下**切換方法檢視**工具列上的按鈕。 下圖顯示的方法檢視**平行堆疊**視窗。  
  
     ![[平行堆疊] 視窗中的 方法檢視](../debugger/media/pdw-walkthrough-4.png "PDW_Walkthrough_4")  
  
     請注意圖表如何隨選取的方法而轉移，以及它在檢視中間如何放在自己的方塊中。 被呼叫端和呼叫端出現在上方和下方。 按一下 [**切換方法檢視**] 按鈕以結束這個模式。  
  
     捷徑功能表**平行堆疊**視窗還有下列其他項目。  
  
    -   **十六進位顯示**切換十進位和十六進位之間的工具提示中的數字。  
  
    -   **符號載入資訊**並**符號設定**開啟各自的對話方塊。  
  
    -   **移至原始程式碼**並**移至反組譯碼**瀏覽在編輯器中選取的方法。  
  
    -   **顯示外部程式碼**會顯示所有框架，即使它們不在使用者程式碼。 請試著使用它來查看圖表如何展開來容納其他框架 (這些框架可能會因為您沒有它們的符號而呈現暗灰色)。  
  
     當您具有大型圖表並逐步執行至下一個中斷點時，您可能會想要讓檢視自動捲動至目前執行緒的作用中堆疊框架，也就是最先叫用中斷點的執行緒。 在 [**平行堆疊**] 視窗中，請確定**自動捲動到目前堆疊框架**工具列上的按鈕是開啟。  
  
     ![在 [平行堆疊] 視窗中的自動捲動](../debugger/media/pdb-walkthrough-4a.png "PDB_Walkthrough_4A")  
  
2.  您繼續之前，在**平行堆疊**視窗中，捲動到最左邊和最下方。  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>繼續執行至第四個中斷點為止  
  
1.  若要繼續執行，直到遇到的第四個中斷點，在**偵錯**功能表上，按一下**繼續**。  
  
     請注意檢視如何自動捲動至定位。 參數中的執行緒**執行緒** 視窗或切換堆疊框架中**呼叫堆疊**視窗，請注意如何檢視總是自動捲動至正確的框架。 關閉**自動捲動到目前工具框架**選項，並檢視差異。  
  
     **鳥瞰**中的大型圖表也有助於**平行堆疊**視窗。 您所見**鳥瞰檢視**按一下右下角的視窗中，捲軸之間的按鈕，如下圖所示。  
  
     ![小鳥的&#45;[平行堆疊] 視窗中的檢視的眼睛](../debugger/media/pdb-walkthrough-5.png "PDB_Walkthrough_5")  
  
     您可以移動矩形以快速將圖表到處移動。  
  
     另一種往任何方向移動圖表的方式是按一下圖表的空白區域，並拖曳至您要的位置。  
  
     若要放大和縮小圖表，請在移動滑鼠滾輪時按住 CTRL。 或者，按一下工具列的 [縮放] 按鈕，然後使用 [縮放] 工具。  
  
     ![放大平行堆疊 視窗中的堆疊](../debugger/media/pdb-walkthrough-5a.png "PDB_Walkthrough_5A")  
  
     您也可以檢視由上而下的方向，而不是由下往上堆疊，依序按一下**工具**功能表上，按一下**選項**，然後選取或清除下方的選項**偵錯**節點。  
  
2.  在您繼續，在前**偵錯**功能表上，按一下**停止偵錯**結束執行。  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>使用平行工作視窗和平行堆疊視窗的工作檢閱  
 繼續之前，我們建議您完成先前的程序。  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>重新啟動應用程式直到叫用第一個中斷點為止  
  
1.  在上**偵錯**功能表上，按一下**開始偵錯**並等待叫用第一個中斷點。  
  
2.  在 **偵錯**功能表上，指向**Windows** ，然後按一下 **執行緒**。 停駐**執行緒**視窗底部的 Visual Studio。  
  
3.  在 **偵錯**功能表上，指向**Windows**然後按一下**呼叫堆疊**。 停駐**呼叫堆疊**底部 Visual Studio 視窗。  
  
4.  按兩下中的執行緒**執行緒**視窗，以使它成為目前。 目前執行緒具有黃色箭號。 當您變更目前執行緒時，其他視窗會隨之更新。 我們接下來檢查工作。  
  
5.  在 **偵錯**功能表上，指向**Windows** ，然後按一下 **平行工作**。 如下圖所示**平行工作**視窗。  
  
     ![四個執行平行工作 視窗中的工作](../debugger/media/pdw-walkthrough-6.png "PDW_Walkthrough_6")  
  
     對於每一個執行中的工作，您可以讀取其 ID (由名稱相同的屬性傳回)、執行這個工作之執行緒的 ID 和名稱，以及它的位置 (將滑鼠游標停留於工作上會顯示包含整個呼叫堆疊的工具提示)。 此外，在**任務**欄中，您可以看到已傳遞給工作的方法; 也就是說，起始點。  
  
     您可以排序任何資料行。 請注意表示排序資料行和方向的排序圖像。 您也可以將資料行向左或向右拖曳，以重新排列資料行。  
  
     黃色箭號表示目前工作。 您可以按兩下工作或使用捷徑功能表來切換工作。 當您切換工作時，基礎執行緒會變成目前執行緒，而其他視窗也會隨之更新。  
  
     當您手動在兩個工作之間切換時，黃色箭號會移動，但白色箭號仍然會顯示造成偵錯工具中斷的工作。  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>繼續執行至第二個中斷點為止  
  
1.  若要繼續執行，直到遇到的第二個中斷點，在**偵錯**功能表上，按一下**繼續**。  
  
     先前**狀態**資料行顯示所有工作執行，但現在兩個工作正在等候。 工作可能會因為許多不同的原因而受阻。 在 [**狀態**] 欄中，將滑鼠停在等候工作，以了解封鎖的原因。 例如，在下圖中，工作 3 正在等待工作 4。  
  
     ![平行工作 視窗中的兩個等待中工作](../debugger/media/pdb-walkthrough-7.png "PDB_Walkthrough_7")  
  
     工作 4 又在等待指派給工作 2 的執行緒所擁有的監視器。  
  
     ![等待中工作和工作 視窗中的工具提示](../debugger/media/pdb-walkthrough-7a.png "PDB_Walkthrough_7A")  
  
     您可以加上旗標工作中的第一個資料行的旗標，即可**平行工作**視窗。  
  
     您可以使用旗標，以相同的偵錯工作階段中的不同中斷點之間追蹤工作，或篩選呼叫堆疊如下所示的任務**平行堆疊**視窗。  
  
     當您使用**平行堆疊**視窗更早版本，您可以檢視應用程式執行緒。 檢視**平行堆疊**視窗一次，但這次檢視應用程式工作。 做法是選取**任務**在左上方的方塊中。 下圖顯示 [工作檢閱]。  
  
     ![執行緒平行堆疊 視窗中的檢視](../debugger/media/pdb-walkthrough-8.png "PDB_Walkthrough_8")  
  
     中的 [工作] 檢視不會顯示目前未執行工作的執行緒**平行堆疊**視窗。 另外，對於在執行工作的執行緒，某些與工作無關的堆疊框架則會從堆疊的上方和下方被過濾掉。  
  
     檢視**平行工作**視窗一次。 以滑鼠右鍵按一下任何資料行標頭，以查看資料行的捷徑功能表。  
  
     ![平行工作 視窗中的捷徑檢閱功能表](../debugger/media/pdb-walkthrough-8a.png "PDB_Walkthrough_8A")  
  
     您可以使用捷徑功能表來加入或移除資料行。 例如，AppDomain 資料行未選取，所以不會出現在清單中。 按一下 **父**。 **父**欄會顯示不含任何四項工作的值。  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>繼續執行至第三個中斷點為止  
  
1.  若要繼續執行，直到遇到的第三個中斷點，在**偵錯**功能表上，按一下**繼續**。  
  
     新工作 (工作 5) 現在正在執行，而工作 4 現在正在等待。 您可以查看原因暫留在等待中工作**狀態**視窗。 在 **父**資料行中，請注意工作 4 是工作 5 的父代。  
  
     若要更妥善地視覺化父子式關聯性，以滑鼠右鍵按一下**父代**資料行標頭，然後按一下**父子式檢視**。 您應該會看到下圖。  
  
     ![父&#45;平行工作 視窗中的子檢視](../debugger/media/pdb-walkthrough-9.png "PDB_Walkthrough_9")  
  
     請注意工作 4 和工作 5 在相同執行緒上執行。 這項資訊不會顯示在**執行緒**視窗中，看到這裡另一個優點**平行工作**視窗。 若要確認這一點，檢視**平行堆疊**視窗。 請確定您正在檢視**任務**。 按兩下檔案中尋找工作 4 和 5**平行工作**視窗。 當您這樣做，藍色醒目提示**平行堆疊**視窗隨即更新。 您也可以尋找工作 4 和 5 上的掃描工具提示**平行堆疊**視窗。  
  
     ![工作平行堆疊 視窗中的檢視](../debugger/media/pdb-walkthrough-9a.png "PDB_Walkthrough_9A")  
  
     在 [**平行堆疊**] 視窗中，以滑鼠右鍵按一下 S.P，然後**移至執行緒**。 視窗會切換至 [執行緒檢視]，且檢視中會有對應的框架。 您可以在相同執行緒上同時查看這兩項工作。  
  
     ![反白顯示 [執行緒] 檢視中的執行緒](../debugger/media/pdb-walkthrough-9b.png "PDB_Walkthrough_9B")  
  
     這是 [工作] 檢視中的另一個好處**平行堆疊**視窗中，相較於**執行緒**視窗。  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>繼續執行至第四個中斷點為止  
  
1.  若要繼續執行，直到遇到的第三個中斷點，在**偵錯**功能表上，按一下**繼續**。 按一下 **識別碼**資料行標頭，依 ID 排序。 您應該會看到下圖。  
  
     ![四種工作平行堆疊 視窗中的狀態](../debugger/media/pdb-walkthrough-10.png "PDB_Walkthrough_10")  
  
     因為工作 5 已完成，所以不會再出現。 如果您的電腦上不是這樣，也沒有顯示死結，請按 F11 逐步執行一次。  
  
     工作 3 和工作 4 現在正在互相等待，已形成死結。 工作 2 還有 5 個新的子工作已經進入排程準備執行。 排程工作是指已在程式碼中啟動但尚未執行的工作。 因此，其**位置**並**執行緒指派**是空的資料行。  
  
     檢視**平行堆疊**視窗一次。 每一個方塊的標題都有工具提示會顯示執行緒 ID 和名稱。 切換至 [工作] 檢視中**平行堆疊**視窗。 將滑鼠游標停留於標題上，以查看工作 ID 和名稱，以及工作的狀態，如下圖所示。  
  
     ![在 [平行堆疊] 視窗的標題工具提示](../debugger/media/pdb-walkthrough-11.png "PDB_Walkthrough_11")  
  
     您可以依資料行將工作分組。 在 [**平行工作**] 視窗中，以滑鼠右鍵按一下**狀態**資料行標頭，然後按一下**依狀態群組**。 如下圖所示**平行工作**依狀態分組的視窗。  
  
     ![分組平行工作 視窗中的工作](../debugger/media/pdb-walkthrough-12.png "PDB_Walkthrough_12")  
  
     您也可以依其他任何資料行進行分組。 將工作分組可讓您專注於一部分工作。 每一個可摺疊的群組都有一些組成該群組的項目。 您可以快速加上旗標的群組中的所有項目，即可**旗標**右邊的按鈕**摺疊** 按鈕。  
  
     ![分組平行堆疊 視窗中的堆疊](../debugger/media/pdb-walkthrough-12a.png "PDB_Walkthrough_12A")  
  
     最後一項功能**平行工作**視窗來檢查是您以滑鼠右鍵按一下工作時，會顯示快顯功能表。  
  
     ![平行工作 視窗中的快顯功能表](../debugger/media/pdb-walkthrough-12b.png "PDB_Walkthrough_12B")  
  
     視工作的狀態而定，捷徑功能表會顯示不同的命令。 命令可能會包含**複製**，**全選**，**十六進位顯示**，**切換至工作**，**凍結指派執行緒**，**凍結所有執行緒，但這**，以及**解除凍結指派的執行緒**，和**旗標**。  
  
     您可以凍結一項或多項工作的基礎執行緒，也可以凍結指派的執行緒除外的所有執行緒。 凍結的執行緒會以表示**平行工作**視窗，因為它處於**執行緒**視窗中的，以藍色*暫停*圖示。  
  
## <a name="summary"></a>總結  
 本逐步解說示範**平行工作**並**平行堆疊**偵錯工具視窗。 請在使用多執行緒程式碼的實際專案上使用這些視窗。 您可以檢查以 C++、C# 或 Visual Basic 撰寫的平行程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯多執行緒應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [平行程式設計](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [並行執行階段](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [使用 [平行堆疊] 視窗](../debugger/using-the-parallel-stacks-window.md)   
 [使用工作視窗](../debugger/using-the-tasks-window.md)


