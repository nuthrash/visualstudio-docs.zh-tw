---
title: 先佔時間 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fd209f65464126650106eb4509cd3de39ad8c25
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54752635"
---
# <a name="preemption-time"></a>先佔時間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

時間軸中的這些區段，會和分類為先佔時間的封鎖時間相關聯。 此分類表示執行緒因為下列原因之一而被切換︰  
  
- 排程器已使用較高優先順序的執行緒取代它。  
  
- 執行緒的執行配量已到期，而其他執行緒已準備好執行。  
  
  在這段期間內，執行緒因為並行視覺化檢視被視作先佔的核心等候原因而被封鎖。 先佔區段會在執行緒被推出邏輯核心時開始，並會在該執行緒繼續執行時結束。  
  
  先佔區段的工具提示會顯示造成先佔的處理序或執行緒名稱。 不過，這不表示接手的處理序或執行緒會在先佔期間全程執行。  
  
## <a name="see-also"></a>請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)
