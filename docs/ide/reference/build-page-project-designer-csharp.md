---
title: 專案設計工具、建置頁 (C#)
ms.date: 06/20/2017
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9aa586f5036c4aa2c321f2dda8333ad4342e165
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62791665"
---
# <a name="build-page-project-designer-c"></a>專案設計工具、建置頁 (C#)
您可以使用 [專案設計工具] 的 [建置] 頁面，來指定專案的組建組態屬性。 此頁面只適用於 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案。

若要存取 [建置] 頁面，請在方案總管中選擇專案節點 (而不是 [方案] 節點)。 然後，依序選擇功能表列上的 [檢視] 和 [屬性頁]。 當 [專案設計工具] 出現時，請選擇 [建置] 索引標籤。

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>組態和平台
下列選項可讓您選取要顯示或修改的組態和平台。

> [!NOTE]
> 使用簡化的組建組態時，專案系統會決定要建置偵錯或發行版本。 因此不會顯示這些選項。 如需詳細資訊，請參閱[如何：設定偵錯和版本組態](../../debugger/how-to-set-debug-and-release-configurations.md)。

**組態** 指定要顯示或修改的組態設定。 設定可以是 [使用中 (偵錯)] (這是預設值)、[偵錯]、[發行] 或 [所有組態]。

**平台** 指定要顯示或修改的平台設定。 預設設定為 [使用中 (任何 CPU)]。 您可以使用 [組態管理員] 來變更使用中的平台。 如需詳細資訊，請參閱[如何：建立和編輯組態](../../ide/how-to-create-and-edit-configurations.md)。

## <a name="general"></a>一般
下列選項可讓您設定幾個 C# 編譯器設定。

**其他編譯符號** 指定執行條件式編譯的符號。 請以分號 (";") 分隔符號。 如需詳細資訊，請參閱 [/define (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option)。

**定義 DEBUG 常數** 將 DEBUG 定義為應用程式中所有原始程式碼檔的符號。 選取此選項相當於使用 `/define:DEBUG` 命令列選項。

**定義 TRACE 常數** 將 TRACE 定義為應用程式中所有原始程式碼檔的符號。 選取此選項相當於使用 `/define:TRACE` 命令列選項。

**平台目標** 指定輸出檔設為目標的處理器。 針對任何 32 位元 Intel 相容處理器選擇 [x86]，針對任何 64 位元 Intel 相容處理器選擇 [x64]，針對 ARM 處理器選擇 [ARM]，或選擇 [任何 CPU] 指定可接受任何處理器。 [任何 CPU] 是專案的預設值，因為這可讓應用程式在種類範圍最廣的不同硬體上執行。

如需詳細資訊，請參閱 [/platform (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)。

**偏好 32 位元** 若選取 [Prefer32-bit] \(偏好 32 位元\) 核取方塊，應用程式將在 32 位元與 64 位元的 Windows 上作為 32 位元應用程式執行。 如果清除此核取方塊，應用程式將在 32 位元版本的 Windows 上當作 32 位元應用程式執行，並在 64 位元版本的 Windows 上當作 64 位元應用程式執行。

如果您將應用程式當作 64 位元應用程式執行，則指標大小會加倍，而且可能發生與其他完全為 32 位元之程式庫的相容性問題。 只有在需要超過 4 GB 的記憶體，或 64 位元指令提供明顯效能改善時，執行 64 位元應用程式才有用。

只有在下列所有條件都成立時，才能使用此核取方塊：

- 在 [建置] 頁面上，[平台目標] 清單設定為 [任何 CPU]。

- 在 [應用程式] 頁面上，[輸出類型] 清單指定專案是應用程式。

- 在 [應用程式] 頁面上，[目標 Framework] 清單指定 .NET Framework 4.5。

**允許不安全的程式碼** 允許使用 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) 關鍵字進行編譯的程式碼。 如需詳細資訊，請參閱 [/unsafe (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option)。

**將程式碼最佳化** 啟用或停用由編譯器執行的最佳化，讓您的輸出檔變得更小、更快且更有效率。 如需詳細資訊，請參閱 [/optimize (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option)。

## <a name="errors-and-warnings"></a>錯誤和警告
您可以使用下列設定，為建置流程設定錯誤和警告選項。

**警告層級** 指定顯示編譯器警告的層級。 如需詳細資訊，請參閱 [/warn (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option)。

**隱藏警告** 封鎖編譯器產生一或多個警告的功能。 請以逗號或分號分隔多個警告編號。 如需詳細資訊，請參閱 [/nowarn (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option)。

## <a name="treat-warnings-as-errors"></a>警告視為錯誤
您可以使用下列設定，指定要將哪些警告視為錯誤。 請選取下列其中一個選項，以指出在何種情況下當建置出現警告時要傳回錯誤。 如需詳細資訊，請參閱 [/warnaserror (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)。

**無** 不會將警告視為錯誤。

**特定警告** 將指定警告視為錯誤。 請以逗號或分號分隔多個警告編號。

**全部** 將所有警告視為錯誤。

## <a name="output"></a>Output
您可以使用下列設定，為建置流程設定輸出選項。

**輸出路徑** 指定此專案組態的輸出檔案位置。 在此方塊中輸入建置輸出的路徑，或選擇 [瀏覽] 按鈕以指定路徑。 請注意，路徑是相對的；如果您輸入絕對路徑，它會儲存為相對路徑。 預設路徑為 bin\Debug 或 bin\Release\\。

使用簡化的組建組態時，專案系統會決定要建置偵錯或發行版本。 不論您指定的 [輸出路徑] 為何，[偵錯] 功能表 (F5) 中的 [建置] 命令都會將組建放在偵錯位置。 不過，[建置] 功能表中的 [建置] 命令卻會將其放在您指定的位置。 如需詳細資訊，請參閱[了解組建組態](../../ide/understanding-build-configurations.md)。

**XML 文件檔案** 指定將要在其中處理文件註解之檔案的名稱。 如需詳細資訊，請參閱 [/doc (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)。

**註冊 COM interop** 表示您的受控應用程式將會公開 COM 物件 (COM 可呼叫包裝函式)，讓 COM 物件可與受控應用程式互動。 您必須在 [專案設計工具] 的 [[應用程式]](../../ide/reference/application-page-project-designer-visual-basic.md) 頁面中，將此應用程式的 [輸出類型] 屬性設定為 [類別庫]，才能使用 [註冊 COM Interop] 屬性。 如需您想要加入 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 應用程式並公開為 COM 物件的範例類別，請參閱[範例 COM 類別](/dotnet/csharp/programming-guide/interop/example-com-class)。

**產生序列化組件** 指定編譯器是否會使用 XML 序列化程式產生器工具 (Sgen.exe) 來建立 XML 序列化組件。 如果您已在程式碼中使用該類別將類型序列化，則序列化組件可提升 <xref:System.Xml.Serialization.XmlSerializer> 的啟動效能。 此選項預設為 [自動]，指定只有您已在程式碼中使用 <xref:System.Xml.Serialization.XmlSerializer> 將類型編碼為 XML 時，才會產生序列化組件。 [關閉] 指定不論您的程式碼是否使用 <xref:System.Xml.Serialization.XmlSerializer>，永遠不會產生序列化組件。 **On** 指定永遠會產生序列化組件。 序列化組件將命名為 `TypeName`.XmlSerializers.dll。 如需詳細資訊，請參閱 [XML 序列化程式產生器工具 (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe)。

**進階** 按一下可顯示 [[進階建置設定] 對話方塊 (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md)。

## <a name="see-also"></a>請參閱

- [專案屬性參考](../../ide/reference/project-properties-reference.md)
- [C# 編譯器選項](/dotnet/csharp/language-reference/compiler-options/index)