---
title: 逐步解說：顯示成對大括弧 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caaafd0143d3b09a51518ee5f54a02b06dbf10aa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084930"
---
# <a name="walkthrough-displaying-matching-braces"></a>逐步解說：顯示成對大括弧
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以實作語言為基礎的功能，例如由定義要比對，在大括的號和時插入號是其中一個大括號，然後將文字標記標記新增至對稱的括號比對的大括號。 您可以定義大括號內容中的一種語言，或您可以定義您自己的檔案名稱擴充功能和內容類型，並將標籤套用到只是該類型，或您可以將標記套用至現有的內容類型 （例如 「 文字 」）。 下列逐步解說示範如何套用至"text"的內容類型的標籤進行比對的大括號。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1. 建立編輯器分類器專案。 將方案命名為 `BraceMatchingTest`。  
  
2. 將編輯器分類器項目範本加入專案。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3. 刪除現有類別檔案。  
  
## <a name="implementing-a-brace-matching-tagger"></a>實作大括號比對標記者  
 若要取得大括號反白顯示類似於 Visual Studio 中使用的效果，您可以實作的標記者類型的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。 下列程式碼示範如何定義任何層級的巢狀大括號組標記。 在此範例中，在大括號配對 []。 []，和{}標記者建構函式，但在完整的語言實作相關的大括號配對會定義語言規格中定義。  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>若要實作大括號比對標記者  
  
1. 將類別檔案並將它命名為括號對稱。  
  
2. 匯入下列命名空間。  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. 定義類別`BraceMatchingTagger`繼承自<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型別的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. 新增 [文字] 檢視中，來源緩衝區中，和目前的快照集點，以及一組大括號組的屬性。  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. 在標記者建構函式中，設定屬性，並檢視變更事件訂閱<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>。 在此範例中，為方便說明，對稱的括號中也會定義建構函式。  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. 做為一部分<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>實作中，宣告 TagsChanged 事件。  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. 事件處理常式更新目前插入號位置的`CurrentChar`屬性並引發 TagsChanged 事件。  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. 實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法來比對括號是當目前字元是左大括號或前一個字元與右大括號，如同 Visual Studio 時。 找到相符項目時，這個方法會具現化兩個標記，一個用於左大括號，一個用於右大括號。  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. 下列的私用方法尋找對稱的括號，在任何層級的巢狀結構。 第一種方法會尋找符合的開啟字元關閉字元：  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. 下列 helper 方法會尋找開啟符合關閉字元的字元：  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>實作大括號比對標記者提供者  
 除了實作標記者，您必須也實作，並匯出的標記者提供者。 在此情況下，提供者的內容類型是"text"。 這表示大括號比對會出現在所有類型的文字檔案，但更完整的實作適用於大括號比對，只以特定的內容類型。  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>若要實作的大括號比對標記者提供者  
  
1. 宣告的標記者提供者繼承自<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>、 BraceMatchingTaggerProvider，將它命名，並將它與匯出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>為"text"，<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. 實作<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>BraceMatchingTagger 具現化的方法。  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試此程式碼，建置 BraceMatchingTest 方案，並在實驗執行個體中執行它。  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>若要建置和測試 BraceMatchingTest 解決方案  
  
1. 建置方案。  
  
2. 當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3. 建立文字檔案，並輸入一些文字，其中包含對稱的括號。  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. 當您插入號左大括號之前時，該括號和關閉對稱的大括號應該會反白顯示。 當您將游標右大括號之後時，該括號和相符的左大括號應該會反白顯示。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
