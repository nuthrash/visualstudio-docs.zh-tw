---
title: MSBuild 12.0 的新功能 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9746b156d2ec959f2ffb5bbff41b3891516d130f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074108"
---
# <a name="what39s-new-in-msbuild-120"></a>MSBuild 12.0 的新功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild 現在是做為 Visual Studio 的一部分安裝，而非 .NET Framework 的一部分。 目前的 MSBuild 版本號碼為 12.0。 如果您想要個別安裝 MSBuild，請從 [MSBuild 下載](http://go.microsoft.com/fwlink/?LinkId=309745)中下載安裝套件。  
  
## <a name="changed-path"></a>已變更路徑  
 MSBuild 現在會直接安裝於 *%ProgramFiles%* 底下，例如 C:\Program Files\MSBuild\\。  
  
## <a name="changed-properties"></a>已變更屬性  
 由於新的版本號碼，以下 MSBuild 屬性已變更：  
  
- 此版本工具的 `MSBuildToolsVersion` 為 12.0。  
  
- 現在 `MSBuildToolsPath` 於 32 位元作業系統上為 %ProgramFiles%\MSBuild\12.0\bin，於 64 位元作業系統上為 %ProgramFiles%\MSBuild\12.0\bin\amd64。  
  
- `ToolsVersion` 值在 32 位元作業系統上位於 HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0，在 64 位元作業系統上位於 HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0。  
  
- `SDK35ToolsPath` 和 `SDK40ToolsPath` 屬性會指向與此版本 Visual Studio 一起封裝的 .NET Framework SDK (例如，適用於 4.X 工具的 8.1A)。  
  
## <a name="new-properties"></a>新屬性  
  
- `MSBuildFrameworkToolsPath` 是新屬性，該屬性在 32 位元作業系統上的值為 %windir%\Microsoft.NET\Framework\v4.0.30319，在 64 位元作業系統上的值為 %windir%\Microsoft.NET\Framework64\v4.0.30319。 這個屬性取代了可用來指向 .NET Framework 工具和公用程式的 `MSBuildToolsPath`。  
  
- `MSBuildToolsPath` 和 `MSBuildFrameworkToolsPath` 擁有 32 位元對等項目，也就是 `MSBuildToolsPath32` 和 `MSBuildFrameworkToolsPath32`，無論使用的是 32 位元或 64 位元的 MSBuild，一律會指向 32 位元位置。

## <a name="see-also"></a>請參閱
[MSBuild](msbuild.md)
