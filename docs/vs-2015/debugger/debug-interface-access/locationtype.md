---
title: LocationType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28bcaa626797313f6ea68a17da33ef9ea192a856
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943548"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

表示在符號中所包含的位置資訊的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>項目  
 `LocIsNull`  
 無法使用位置資訊。  
  
 `LocIsStatic`  
 位置是靜態的。  
  
 `LocIsTLS`  
 位置是在執行緒區域儲存區。  
  
 `LocIsRegRel`  
 位置是暫存器的相對位置。  
  
 `LocIsThisRel`  
 位置是`this`-相對。  
  
 `LocIsEnregistered`  
 位置是在暫存器。  
  
 `LocIsBitField`  
 位置是在位元欄位。  
  
 `LocIsSlot`  
 位置是 Microsoft Intermediate Language (MSIL) 位置。  
  
 `LocIsIlRel`  
 位置是 MSIL 相對。  
  
 `LocInMetaData`  
 位置是在中繼資料。  
  
 `LocIsConstant`  
 位置是常數值。  
  
 `LocTypeMax`  
 這個列舉型別中的位置類型數目。  
  
## <a name="remarks"></a>備註  
 可用的屬性來[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)介面取決於映像檔中的符號的位置。 如需詳細資訊，請參閱 <<c0> [ 符號位置](../../debugger/debug-interface-access/symbol-locations.md)。  
  
 這個列舉型別中的值會傳回呼叫[idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)
