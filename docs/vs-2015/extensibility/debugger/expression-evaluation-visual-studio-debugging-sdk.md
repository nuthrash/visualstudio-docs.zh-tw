---
title: 運算式評估 (Visual Studio 偵錯 SDK) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562155"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>運算式評估 (Visual Studio Debugging SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在中斷模式期間 IDE 必須要能夠評估涉及數個變數的程式的簡單運算式。 若要達成此目的，偵錯引擎 (DE) 必須能夠剖析及評估運算式輸入到其中一個 IDE 視窗。  
  
 使用建立運算式[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法並遭到由產生[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面。  
  
 **IDebugExpression2**介面的實作方法 DE 並呼叫其**EvalAsync**方法，以傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) ide，以顯示介面在 IDE 中的運算式評估的結果。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)傳回的結構，可以用來監看式視窗或 [區域變數] 視窗中，輸入運算式的值。  
  
 偵錯封裝或工作階段偵錯管理員 (SDM) 會呼叫[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)或是[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)若要取得[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)表示介面評估的結果。 `IDebugProperty2` 有方法會傳回名稱、 類型和運算式的值。 這項資訊會顯示在各種不同的偵錯工具視窗。  
  
## <a name="using-expression-evaluation"></a>使用運算式評估  
 若要使用運算式的評估版，您必須實作[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法，以及所有的方法[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面下, 表所示。  
  
|方法|描述|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步方式評估運算式。|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步運算式評估。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式來評估運算式。|  
  
 同步和非同步評估要求的實作[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 非同步運算式評估要求實作[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
