---
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff3ed7d23272bad1e047ddca46e20b4710644e30
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842601"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
這個介面會表示為指標類型。

## <a name="syntax"></a>語法

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實作者的附註
 符號提供者會實作這個介面來代表指標。

## <a name="notes-for-callers"></a>呼叫端資訊
 使用[QueryInterface](/cpp/atl/queryinterface)若要取得從這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回`FIELD_TYPE_POINTER`。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 上的方法除了`IDebugField`和`IDebugContainerField`介面，這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述指標的目標。|

## <a name="remarks"></a>備註
 在 C /C++，如果使用它來使用陣列標記法指標可以是一個容器。 例如，假設`char *pString`，`pString`的類型指標為`char`。 `pString[3]` 具有型別的一種容器，是一個指向`char`參考該容器的第四個項目。

## <a name="requirements"></a>需求
 標頭： sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)