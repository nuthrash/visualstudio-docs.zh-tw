---
title: RemoveDir 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RemoveDir task [MSBuild]
- MSBuild, RemoveDir task
ms.assetid: 7ab214be-26b2-4bcd-9de8-c1b2091c0b74
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70bd6623d86ecfa76d3e09de09a8dcfad3d5da20
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648611"
---
# <a name="removedir-task"></a>RemoveDir 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

移除指定的目錄及其所有檔案和子目錄。  
  
## <a name="parameters"></a>參數  
 下表說明 `RemoveDir` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`Directories`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要刪除的目錄。|  
|`RemovedDirectories`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含已成功刪除的目錄。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會移除 `OutputDirectory` 和 `DebugDirectory` 屬性所指定的目錄。 這些路徑會視為相對於專案目錄。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2005">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
        <DebugDirectory>\Debug\</DebugDirectory>  
    </PropertyGroup>  
  
    <Target Name="RemoveDirectories">  
        <RemoveDir  
            Directories="$(OutputDirectory);$(DebugDirectory)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
