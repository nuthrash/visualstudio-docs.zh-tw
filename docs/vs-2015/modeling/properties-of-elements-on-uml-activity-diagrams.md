---
title: UML 活動圖表元素的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
- activity diagrams, properties
ms.assetid: 9849d45e-65d5-46bd-a319-757e90b7c748
caps.latest.revision: 19
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c50a84f9e3c5425459ea458c3f6bbc282d64b0b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486040"
---
# <a name="properties-of-elements-on-uml-activity-diagrams"></a>UML 活動圖表中的項目屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[UML 活動圖表上的項目屬性](https://docs.microsoft.com/visualstudio/modeling/properties-of-elements-on-uml-activity-diagrams)。  
  
在 UML 活動圖表上，每個項目都具有屬性。 若要查看項目的屬性，以滑鼠右鍵按一下的項目在圖表上或在**UML 模型總管**，然後按一下**屬性**。 屬性會出現在**屬性**視窗。  
  
> [!NOTE]
>  本主題有關 UML 活動圖表上項目的屬性。 如需如何閱讀 UML 活動圖表的詳細資訊，請參閱[UML 活動圖表： 參考](../modeling/uml-activity-diagrams-reference.md)。 如需如何繪製 UML 活動圖表的詳細資訊，請參閱[UML 活動圖表： 指導方針](../modeling/uml-activity-diagrams-guidelines.md)。  
  
## <a name="properties-of-elements"></a>項目屬性  
  
|屬性|預設|項目|描述|  
|--------------|-------------|-------------|-----------------|  
|**名稱**|預設名稱|全部|識別項目。|  
|**限定的名稱**|套件 :: 名稱|全部|唯一識別項目。 前面加上含有該項目之套件的合格名稱。|  
|**工作項目**|0 associated|全部|與此項目相關聯的工作項目數。 若要關聯工作項目，請參閱[連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)。|  
|**描述**|(無)|全部|您可以在這裡設定項目的一般注意事項。|  
|**色彩**|(類型的預設)|全部|圖案的色彩。|  
|**本文**|(無)|動作|詳細地指定動作。|  
|**Language**|(無)|動作|內容中運算式的語言。|  
|**本機後置條件**|(無)|動作、傳送、接受、呼叫行為、呼叫作業|執行結束時必須滿足的條件約束。 藉由動作所達成的目標。|  
|**本機前置條件**|(無)|動作、傳送、接受、呼叫行為、呼叫作業|執行開始前必須滿足的條件約束。|  
|**是同步**|True|呼叫行為、呼叫作業|-如果為 true，此動作會等候到活動終止。|  
|**行為**|(無)|呼叫行為|-叫用的活動。|  
|**作業**|(無)|呼叫作業|-叫用作業。|  
|**會解除封裝處理**|False|接受事件|-如果為 true，可能會有數個具類型的輸出連接，且資料會解除封裝至此。 如果為 False，所有資料會顯示在一個連接上。|  
|**上限**|**\***|物件節點、活動參數|**0**表示傳遞資料時，必須直接沿著流程。<br /><br /> **\*** 表示資料可以儲存在流程中。|  
|**選取項目**|(無)|物件節點、活動參數、輸入連接、輸出連接、物件流程|叫用會篩選資料的處理序。 這個處理序可以在另一個圖表中定義。|  
|**排序**|(無)|物件節點、活動參數、輸入連接、輸出連接|-如何將多個權杖會儲存。|  
|**是控制項**|False|輸入連接、輸出連接|-如果為 true，則這個連接上的流程是控制流程。 如果為 False，則是物件流程。|  
|**Type**|(無)|輸入連接、輸出連接、物件節點、活動參數|層傳輸的物件類型。<br />-類型可以是基本類型，例如整數，或在模型中其他地方定義的分類器。 如果您輸入未定義類型的名稱，它會顯示在**未指定的型別**UML 模型總管 的區段。|  
|**多重性**|1|輸入連接、輸出連接|-可以是單一值或某個範圍`[n..m]`。<br />-下限`n`-動作無法啟動 （適用於輸入的 pin) 或停止 （適用於輸出連接），直到有`n`等候連接的物件。<br />-上限`m`-此動作無法使用或產生多個`m`一次執行中的物件。 * 表示沒有任何限制。|  
|**轉換**|(無)|物件流程|-叫用轉換資料的程序。 這個處理序可以在另一個圖表中定義。|  
|**多點傳送**|False|物件流程|-表示可能會有數個收件者物件或元件。|  
|**是 MultiReceive**|False|物件流程|-表示可能會有數個收件者物件或元件。|  
|**是單一執行**|False|活動圖|-如果設定完成，最多執行一次這個圖表一次。|  
  
## <a name="see-also"></a>另請參閱  
 [UML 活動圖表： 參考](../modeling/uml-activity-diagrams-reference.md)   
 [UML 活動圖表：方針](../modeling/uml-activity-diagrams-guidelines.md)


