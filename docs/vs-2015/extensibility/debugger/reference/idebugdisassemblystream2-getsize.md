---
title: IDebugDisassemblyStream2::GetSize |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6db80ef9c447f9e08a1332348d2212699d01d8e2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941707"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指示這個反組譯碼資料流中取得的大小。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pnSize`  
 [out]傳回大小，指示中。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 從這個方法傳回的值可以用來配置的陣列[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構，然後傳遞給[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
