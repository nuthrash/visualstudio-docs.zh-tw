---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45919c6c9fafceecca2cb53fa9c2c9f43b68e382
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870002"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
取得標題、 易記名稱或此程式的裝載處理序的檔案名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

#### <a name="parameters"></a>參數
 `dwType`

 [in]值，以從[GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)列舉型別。

 `pbstrHostName`

 [out]傳回要求的裝載處理序的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 在典型的實作，這個方法，`dwType`參數會被忽略，並傳回主機電腦的易記名稱。 另一個可能的實作是將傳遞`dwType`參數來呼叫[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)方法來取得名稱。

## <a name="see-also"></a>另請參閱
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)