---
title: IDiaSymbol::get_registerType |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: f1c98ab0-8aef-4a07-a686-28b8a54418ef
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f714e5637776d6a0606246d339d3f9d2ccd9f19a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62835535"
---
# <a name="idiasymbolgetregistertype"></a>IDiaSymbol::get_registerType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取註冊型別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT get_registerType(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]指標`DWORD`保存暫存器型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
