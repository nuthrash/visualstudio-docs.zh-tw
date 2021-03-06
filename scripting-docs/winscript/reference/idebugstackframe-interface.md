---
title: IDebugStackFrame 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8f645d6460ff15734348267b5138b1b6edea071
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005874"
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame 介面
代表執行緒堆疊上的邏輯堆疊框架。 呼叫`IDebugStackFrame::QueryInterface`方法，以取得`IDebugExpressionContext`介面，可讓運算式評估和監看式視窗。  
  
 除了繼承自方法`IUnknown`，則`IDebugStackFrame`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|傳回目前的堆疊框架相關聯的程式碼內容。|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|傳回堆疊框架的短或長時間的文字描述。|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|傳回語言簡短或長時間的文字描述。|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|傳回此堆疊框架相關聯的執行緒。|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|傳回目前的框架屬性瀏覽器。|