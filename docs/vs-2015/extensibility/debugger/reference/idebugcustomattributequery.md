---
title: IDebugCustomAttributeQuery |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa9c87065130e0b539e49c314648fa5b3944089b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572331"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
表示在方法或類型的自訂屬性的查詢。

## <a name="syntax"></a>語法

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>方法
 這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|擷取自訂屬性，指定其名稱。|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|判斷指定的自訂屬性所定義。|

## <a name="requirements"></a>需求
 標頭：Sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll