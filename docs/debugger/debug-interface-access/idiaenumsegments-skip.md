---
title: IDiaEnumSegments::Skip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ff4c5d26d875dc098775d0d379e7d12b062801cd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840014"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

略過指定的數目的列舉型別序列中的區段。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]略過列舉序列中的區段數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`如果有沒有更多的區段，以略過。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
