---
title: IDebugPointerObject::SetBytes |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d467b037f4e2affea53a142304507f876630999
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944465"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

設定從一系列的連續位元組所指向的值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwStart`  
 [in]以位元組為單位，從所指向之物件的開始位移。  
  
 `dwCount`  
 [in]若要設定的位元組數目。  
  
 `pBytes`  
 [in]代表新值的位元組陣列。 這個值會儲存成物件，指定位移處開始。  
  
 `pdwBytes`  
 [out]傳回的位元組數目可實際設定。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果使用這個方法的指標，表示這個[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)指向基本型別或簡單基本型別 （也就是可以由簡單的一連串的位元組陣列） 的陣列。 這`IDebugPointerObject`物件不可以是 null 參考 （它必須指向記憶體中的位址）。  
  
## <a name="see-also"></a>另請參閱  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
