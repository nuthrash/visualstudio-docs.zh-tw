---
title: TrackedVCToolTask 類別 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 4a4044416131a27ca313d10d02404094c5f5e219
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938865"
---
# <a name="trackedvctooltask-base-class"></a>TrackedVCToolTask 基底類別

許多工作最終繼承自 <xref:Microsoft.Build.Utilities.Task> 類別和 [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) 類別。 此類別會將數個參數新增至衍生自 [VCToolTask](../msbuild/vctooltask-base-class.md) 的工作。 本文件會列出這些參數。

## <a name="parameters"></a>參數

下表說明 **TrackedVCToolTask** 基底類別的參數。

|參數|說明|
|---------------|-----------------|
|**DeleteOutputOnExecute**|選擇性的 **bool** 參數。|
|**EnableExecuteTool**|選擇性的 **bool** 參數。|
|**ExcludedInputPaths**|選擇性的 **ITaskItem[]** 參數。|
|**MinimalRebuildFromTracking**|選擇性的 **bool** 參數。|
|**PathOverride**|選擇性的 **string** 參數。|
|**PostBuildTrackingCleanup**|選擇性的 **bool** 參數。|
|**RootSource**|選擇性的 **string** 參數。|
|**SkippedExecution**|選擇性的 **bool** 輸出參數。|
|**SourcesCompiled**|選擇性的 **ITaskItem[]** 輸出參數。|
|**TLogCommandFile**|選擇性的 **ITaskItem** 參數。|
|**TLogReadFiles**|選擇性的 **ITaskItem[]** 參數。|
|**TLogWriteFiles**|選擇性的 **ITaskItem[]** 參數。|
|**ToolArchitecture**|選擇性的 **string** 參數。|
|**TrackCommandLines**|選擇性的 **bool** 參數。|
|**TrackFileAccess**|選擇性的 **bool** 參數。|
|**TrackedInputFilesToIgnore**|選擇性的 **ITaskItem[]** 參數。|
|**TrackedOutputFilesToIgnore**|選擇性的 **ITaskItem[]** 參數。|
|**TrackerFrameworkPath**|選擇性的 **string** 參數。|
|**TrackerSdkPath**|選擇性的 **string** 參數。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)<br/>
[工作](../msbuild/msbuild-tasks.md)