---
title: 如何：收集 Windows 計數器資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9743fa7defbbf3321636d2ba4799454713a647db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432775"
---
# <a name="how-to-collect-windows-counter-data"></a>如何：收集 Windows 計數器資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 計數器是程式碼剖析期間可以設定的間隔收集的系統效能計數器。 在程式碼剖析工具報告的 [標記] 檢視中，每個收集間隔會有一個標示為 [自動標記] 的資料列。 該資料列包含以該間隔描述效能計數器值的資料行。 若要將分析限制於兩個特定標記之間的時段，請選取標記並按一下滑鼠右鍵，然後從捷徑功能表中選取 [篩選依據]  ->   [標記]。  
  
 **需求**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、[!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 Windows 市集應用程式也需要新的資料收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
### <a name="to-collect-windows-counter-data"></a>收集 Windows 計數器資料  
  
1. 在 [效能總管] 中，以滑鼠右鍵按一下您要為其設定 Windows 計數器的工作階段，然後選取 [屬性]。  
  
2. 在 [屬性頁] 中，按一下 [Windows 計數器]。  
  
3. 選取 [收集 Windows 計數器] 核取方塊。  
  
4. 在 [收集間隔 (毫秒)] 文字方塊中，輸入一段時間。  
  
5. 從 [計數器分類] 下拉式清單選取一個類別。  
  
6. 從 [執行個體] 下拉式清單選取一個執行個體。  
  
7. 選取對應用程式進行程式碼剖析時要使用的計數器。  
  
8. 按一下 [套用]。  
  
## <a name="see-also"></a>請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [效能工作階段屬性](../profiling/performance-session-properties.md)   
 [CPU 和 Windows 計數器](../profiling/cpu-and-windows-counters.md)
