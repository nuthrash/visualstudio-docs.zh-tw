---
title: 註冊副檔名的動詞命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a260f0458b6278abc6c515b616345463a0cafef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434749"
---
# <a name="register-verbs-for-file-name-extensions"></a>註冊副檔名的動詞命令
與應用程式的檔案名稱副檔名關聯通常會有偏好的動作，當使用者按兩下檔案時，就會發生。 此建議動作連結到動詞，例如開啟時，對應至動作。

 您可以註冊擴充功能使用 Shell 機碼位於與的程式設計識別項 (ProgID) 相關聯的動詞**HKEY_CLASSES_ROOT\{progid} \shell**。 如需詳細資訊，請參閱 <<c0> [ 檔案類型](/windows/desktop/shell/fa-file-types)。

## <a name="register-standard-verbs"></a>註冊標準動詞命令
 作業系統可辨識下列的標準動詞命令：

- 開啟

- 編輯

- 播放

- 的

- 預覽

  可能的話，請註冊一個標準動詞。 最常見的方式是開啟的動詞命令。 只有當沒有清楚的差異開啟檔案，並編輯檔案，請使用編輯動詞命令。 例如，開啟 *.htm*檔案顯示在瀏覽器中，而編輯 *.htm*檔案啟動 HTML 編輯器。 標準動詞命令已當地語系化的作業系統地區設定。

> [!NOTE]
> 註冊時的標準動詞，未設定開啟的索引鍵的預設值。 預設值會包含在功能表上的顯示字串。 作業系統會提供這個標準動詞命令的字串。

 專案檔應該要啟動的新執行個體註冊[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]當使用者在開啟的檔案。 下列範例說明的標準動詞註冊[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]專案。

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 若要在現有的執行個體中開啟檔案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，註冊 DDEEXEC 金鑰。 下列範例說明的標準動詞註冊[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs*檔案。

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>設定預設的動詞命令
 預設的動詞命令是使用者按兩下 Windows 檔案總管中的檔案時所執行的動作。 預設的動詞命令是指定為預設值的指令動詞**HKEY_CLASSES_ROOT\\*progid*\Shell**索引鍵。 如果未不指定任何值，預設的動詞命令是在指定的第一個指令動詞**HKEY_CLASSES_ROOT\\*progid*\Shell**索引鍵清單。

> [!NOTE]
> 如果您想要變更預設的並排顯示部署中的延伸模組的動詞命令，請考慮對安裝與移除的影響。 在安裝期間會覆寫原始的預設值。

## <a name="see-also"></a>另請參閱
- [管理並排顯示檔案關聯](../extensibility/managing-side-by-side-file-associations.md)
