---
title: 幾何圖案的屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b8d848372521baebb48cb5b3924744e88970a728
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941882"
---
# <a name="properties-of-geometry-shapes"></a>幾何圖案的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用幾何圖案，來指定網域類別的執行個體在網域指定語言中的顯示方式。 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 幾何圖案具有下表中所列的屬性。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|填滿色彩|此圖形的填滿色彩。|白皮書|  
|填滿漸層模式|此圖形 （水平、 垂直、 正向對角線、 回溯對角線，或無） 的填滿漸層停駐的模式。|水平|  
|幾何|此圖形 （矩形、 圓角矩形、 橢圓形或圓形） 的幾何。|矩形|  
|有預設的連接點|如果`True`、 圖形會使用上、 下、 左和右連接點產生的設計工具中。|False|  
|外框色彩|此圖形的外框色彩。|黑色|  
|外框虛線樣式|（實線、 虛線、 點、 線、 虛線點點或自訂），此圖形的外框虛線樣式。|實線|  
|外框粗細|此圖形的外框粗細。|0.03125|  
|文字色彩|使用此圖形相關聯的文字裝飾項目的色彩。|黑色|  
|存取修飾詞|類別 （公用或內部） 的存取修飾詞。|Public|  
|自訂屬性|用來將屬性加入至會產生此圖形的來源的程式碼類別。|\<無>|  
|產生雙衍生|如果`True`，將產生的基底類別和部分類別 （以支援透過覆寫自訂）。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，以原始碼提供自訂建構函式。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|描述的繼承來源的程式碼類別圖形從產生的類型 (`none`，`abstract`或`sealed`)。|none|  
|基底幾何圖形|此圖形的基底類別。|(無)|  
|名稱|此圖形的名稱。|目前的名稱|  
|命名空間|此圖形附屬於命名空間。|目前的命名空間|  
|工具提示類型|（固定、 變數或 none） 」 來定義 「 工具提示的方式。 如果固定，則值`Fixed Tooltip Text`屬性做為工具提示; 若變數，然後工具提示中定義的自訂程式碼。|None|  
|注意|這個項目相關聯的非正式附註。|\<無>|  
|初始的高度|此圖形，以英吋的初始高度。|1|  
|初始寬度|此圖形，以英吋的初始寬度。|1.5|  
|當做屬性公開的填滿色彩<br /><br /> 公開的填滿漸層模式<br /><br /> 公開為屬性的 外框色彩<br /><br /> 公開為屬性的 外框虛線樣式<br /><br /> 公開為屬性的外框粗細<br /><br /> 公開 （expose) 的文字色彩|如果`True`，使用者可以設定圖形的所述的屬性。 若要設定這種情況，請以滑鼠右鍵按一下圖形定義，然後按一下**加入已公開**。|False|  
|描述|描述用來產生的設計工具的文件。|\<無>|  
|顯示名稱|將會顯示在產生的設計工具，此圖形的名稱。|\<無>|  
|固定的工具提示文字|用於固定工具提示文字。|\<無>|  
|說明關鍵字|用來編製索引為此圖形的 F1 說明關鍵字。|\<無>|  
  
## <a name="see-also"></a>另請參閱  
 [Domain-Specific Language Tools Glossary](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
