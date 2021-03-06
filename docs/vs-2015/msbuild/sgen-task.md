---
title: SGen 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2741dc6e3e08f8c7f7ee2e28bcf2d8df1613f10e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647235"
---
# <a name="sgen-task"></a>SGen 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

針對指定組件中的型別建立 XML 序列化組件。 此工作會包裝 XML 序列化程式產生器工具 (Sgen.exe)。 如需詳細資訊，請參閱 [XML 序列化程式產生器工具 (Sgen.exe)](http://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6)。  
  
## <a name="parameters"></a>參數  
 下表說明 `SGen` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`BuildAssemblyName`|必要的 `String` 參數。<br /><br /> 產生序列化程式碼的組件。|  
|`BuildAssemblyPath`|必要的 `String` 參數。<br /><br /> 用來產生序列化程式碼之組件的路徑。|  
|`DelaySign`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即表示您想要完整的簽署組件。 如果是 `false`，則表示您只想將公開金鑰放置於組件中。<br /><br /> 除非與 `KeyFile` 或 `KeyContainer` 參數搭配使用，否則此參數沒有任何作用。|  
|`KeyContainer`|選擇性的 `String` 參數。<br /><br /> 指定保留金鑰組的容器。 這樣會藉由將公開金鑰插入組件資訊清單中的方式簽署組件。 然後工作將會使用私密金鑰簽署最終組件。|  
|`KeyFile`|選擇性的 `String` 參數。<br /><br /> 指定用來簽署組件的金鑰組或公開金鑰。 編譯器會將公開金鑰插入組件資訊清單中，然後使用私密金鑰簽署最終組件。|  
|`Platform`|選擇性的 `String` 參數。<br /><br /> 取得或設定用來產生輸出組件的編譯器平台。 此參數可以具有 `x86`、`x64` 或 `anycpu` 的值。 預設為 `anycpu`。|  
|`References`|選擇性的 `String[]` 參數。<br /><br /> 指定要求 XML 序列化的型別所參考的組件。|  
|`SdkToolsPath`|選擇性的 `String` 參數。<br /><br /> 指定 SDK 工具 (例如 resgen.exe) 的路徑。|  
|`SerializationAssembly`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含所產生的序列化組件。|  
|`SerializationAssemblyName`|選擇性的 `String` 參數。<br /><br /> 指定所產生序列化組件的名稱。|  
|`ShouldGenerateSerializer`|必要的 `Boolean` 參數。<br /><br /> 如果為 `true`，SGen 工作應該產生序列化組件。|  
|`Timeout`|選擇性的 `Int32` 參數。<br /><br /> 指定時間量 (以毫秒為單位)，在此時間量之後會終止工作可執行檔。 預設值是 `Int.MaxValue`，表示沒有逾時期間。|  
|`ToolPath`|選擇性的 `String` 參數。<br /><br /> 指定位置，工作會從該位置載入基礎可執行檔 (sgen.exe)。 如果未指定這個參數，工作會使用 SDK 安裝路徑，對應於執行 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 之架構的版本。|  
|`Types`|選擇性的 `String[]` 參數。<br /><br /> 取得或設定產生序列化程式碼特定型別的清單。 SGen 只會針對那些型別產生序列化程式碼。|  
|`UseProxyTypes`|必要的 `Boolean` 參數。<br /><br /> 如果為 `true`，SGen 工作只會為 XML Web 服務 Proxy 型別產生序列化程式碼。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。 如需這些其他參數的清單及其說明，請參閱 [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)
