---
title: IDiaStackFrame::get_systemExceptionHandling | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_systemExceptionHandling
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 519602b09ea1adcf00ed534ecb22b4a082018464
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838037"
---
# <a name="idiastackframegetsystemexceptionhandling"></a>IDiaStackFrame::get_systemExceptionHandling
擷取指出系統例外狀況處理是否作用中的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_systemExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]會傳回`TRUE`系統例外狀況處理實際上是這個框架中; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援的屬性。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 系統例外狀況處理亦稱為結構化例外狀況處理。 這不是與相同的工作C++例外狀況處理。

 若要判斷C++例外狀況處理已生效，請呼叫[idiastackframe:: Get_cplusplusexceptionhandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)方法。

## <a name="see-also"></a>另請參閱
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)