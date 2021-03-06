---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a65b02bc58d300a93cd33ebcdd5f21d1b9665b19
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914142"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
此介面列舉[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。

## <a name="syntax"></a>語法

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面做為其支援的物件參考的一部分，在記憶體中。 支援的參考時，才必須實作這個介面。

## <a name="notes-for-callers"></a>呼叫端資訊
 Visual Studio 呼叫[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugReferenceInfo2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|擷取指定的數目[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)列舉型別序列中的結構。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|略過指定的數目的[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)列舉序列中的結構。|
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|將列舉型別序列重設到開頭。|
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|取得的數目[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)中列舉值的結構。|

## <a name="remarks"></a>備註
 參考是本質上的型別和地址，，而屬性是名稱、 類型和地址。 參考仍然存在，只要參考存在於記憶體中的物件。 請參閱[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)如需詳細資訊。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)