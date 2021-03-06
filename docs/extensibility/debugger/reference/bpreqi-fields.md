---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25b95e2934de9d09ef9541162b05920a04f645bd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723041"
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
指定要擷取中斷點要求的相關資訊。

## <a name="syntax"></a>語法

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="members"></a>成員
初始化/使用 BPREQI_BPLOCATION `bpLocation` （中斷點位置） 欄位[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)或是[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。

初始化/使用 BPREQI_LANGUAGE`guidLanguage`欄位`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。

初始化/使用 BPREQI_PROGRAM`pProgram`欄位`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。

初始化/使用 BPREQI_PROGRAMNAME`bstrProgramName`欄位`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。

初始化/使用 BPREQI_THREAD`pThread`欄位`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。

初始化/使用 BPREQI_THREADNAME`bstrThreadName`欄位`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。

初始化/使用 BPREQI_PASSCOUNT`bpPassCount`欄位`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。

初始化/使用 BPREQI_CONDITION `bpCondition` （中斷點條件） 欄位`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。

初始化/使用 BPREQI_FLAGS`dwFlags`欄位`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。

BPREQI_ALLOLDFIELDS 初始化/使用所有欄位的`BP_REQUEST_INFO`結構。

初始化/使用 BPREQI_VENDOR`guidVendor`欄位`BP_REQUEST_INFO2`結構。

初始化/使用 BPREQI_CONSTRAINT`bstrConstraint`欄位`BP_REQUEST_INFO2`結構。

初始化/使用 BPREQI_TRACEPOINT`bstrTracepoint`欄位`BP_REQUEST_INFO2`結構。

BPREQI_ALLFIELDS 指定所有欄位`BP_REQUEST_INFO2`結構。

## <a name="remarks"></a>備註
作為引數[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)並[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)方法，來指定哪些欄位[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)並[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構會進行初始化。

這些旗標也可用來表示欄位`BP_REQUEST_INFO`和`BP_REQUEST_INFO2`結構會使用和有效時傳回每個結構。

這些值可能會合併的位元`OR`。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
