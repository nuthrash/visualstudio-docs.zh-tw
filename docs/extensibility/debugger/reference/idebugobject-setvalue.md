---
title: IDebugObject::SetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ccfea65f7f24b3d48fc5ec5d68028c72b9b4eece
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872446"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
設定物件的值從一系列連續的位元組。

## <a name="syntax"></a>語法

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

#### <a name="parameters"></a>參數
 `pValue`

 [in]代表新值的位元組陣列。

 `nSize`

 [in]值，以位元組為單位的大小。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 陣列中的值會複製到這[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件，取代任何現有的值。 新值的大小可以大於或小於現有的值。 這`IDebugObject`不能是 null 參考。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)