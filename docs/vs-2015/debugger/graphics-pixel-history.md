---
title: 圖形像素歷史記錄 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 614977aef83092c64071524e33507848c34bf442
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420080"
---
# <a name="graphics-pixel-history"></a>圖形像素歷史記錄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 圖形診斷工具中的 [圖形像素歷史記錄] 視窗可幫助您了解在遊戲或應用程式的畫面格期間，Direct3D 事件對特定像素有何影響。  
  
 這是 [像素歷史記錄] 視窗：  
  
 ![包含在其歷程記錄中的三個 Direct3D 事件的像素。](../debugger/media/gfx-diag-demo-pixel-history-orientation.png "gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>了解 [像素歷史記錄] 視窗  
 使用 [像素歷史記錄]，即可分析在畫面格期間，Direct3D 事件對轉譯目標的特定像素有何影響。 您可以找出特定 Direct3D 事件的呈現問題，即使後續事件 (或相同事件中的後續基本項目) 繼續變更像素的最終色彩值也一樣。 例如，像素的呈現可能不正確，然後被另一個半透明的像素遮住，導致其色彩在畫面格緩衝區中混合在一起。 如果您只有呈現目標的最後內容可以引導您，這種問題會很難診斷。  
  
 [像素歷史記錄] 視窗會顯示所選取畫面格整個過程的完整像素歷史記錄。 視窗頂端的 [最終畫面格緩衝區] 會顯示寫入畫面格結尾之畫面格緩衝區的色彩，並附有像素的其他資訊，例如其來自哪個畫面格，以及其螢幕座標。 此區域也包含 [呈現 Alpha] 核取方塊。 選取此核取方塊時，[最終畫面格緩衝區] 色彩和中繼色彩值會以透明模式顯示在棋盤圖樣上方。 如果清除此核取方塊，則會忽略色彩值的 Alpha 色板。  
  
 視窗底部顯示有機會影響的像素色彩的事件，並伴隨 [初始] 和 [最終] 虛擬事件，以表示畫面格緩衝區中像素的初始和最終色彩值。 初始色彩值是由變更像素色彩的第一個事件 (通常是 `Clear` 事件) 決定。 像素的記錄中一定會有這兩個虛擬事件，即使沒有受到其他任何事件影響也一樣。 當其他事件有機會影響像素時，會顯示在 [初始] 與 [最終] 事件之間。 事件可以展開，以顯示其詳細資料。 針對這種清除呈現目標的簡單事件，事件的效果只是色彩值。 像繪製呼叫這種比較複雜的事件，就會產生一或多個可能影響像素色彩的基本項目。  
  
 事件繪製的基本項目可以從其基本類型和索引，以及物件的基本項目總數來識別。 例如，像 [(6214) 中的第 (1456) 個三角形] 這樣的識別項，表示基本項目對應至由 6214 個三角形組成之物件中的第 1456 個三角形。 每個基本識別項的左邊都會有一個圖示，摘要說明該基本項目對像素的效果。 影響像素色彩的基本項目會以填滿結果色彩的圓角矩形來表示。 被排除對像素色彩有影響的基本項目，則會以指出像素被排除原因的圖示來表示。 本文稍後的[基本項目排除](../debugger/graphics-pixel-history.md#exclusion)一節會說明這些圖示。  
  
 您可以展開每個基本項目來檢查像素著色器輸出如何與現有的像素色彩合併，而產生結果色彩。 從這裡您也可以檢查或偵錯與基本項目相關聯的像素著色器程式碼，而且您可以進一步展開頂點著色器節點，以檢查頂點著色器輸入。  
  
### <a name="exclusion"></a> 基本項目排除  
 如果基本項目被排除會影響像素色彩，被排除的原因有很多。 每個原因會以下表中所描述的圖示來表示：  
  
|圖示|排除的原因|  
|----------|--------------------------|  
|![深度測試失敗圖示。](../debugger/media/vsg-hist-icon-failed-depth.png "vsg_hist_icon_failed_depth")|像素因為深度測試失敗而被排除。|  
|![剪式測試失敗圖示。](../debugger/media/vsg-hist-icon-failed-scissor.png "vsg_hist_icon_failed_scissor")|像素因為剪式測試失敗而被排除。|  
|![樣板測試失敗圖示。](../debugger/media/vsg-hist-icon-failed-stencil.png "vsg_hist_icon_failed_stencil")|像素因為樣板測試失敗而被排除。|  
  
### <a name="draw-call-exclusion"></a>繪製呼叫排除  
 如果繪製呼叫中的所有基本項目都因為測試失敗而被排除會影響呈現目標，則該繪製呼叫無法展開，而且旁邊會顯示對應至排除原因的圖示。 繪製呼叫排除的原因類似基本項目排除的原因，而且它們的圖示也很類似。  
  
### <a name="viewing-and-debugging-shader-code"></a>檢視及偵錯著色器程式碼  
 您可以檢查和偵錯頂點、輪廓、網域、幾何和像素著色器的程式碼，方法是使用與著色器相關聯之基本項目下方的控制項。  
  
##### <a name="to-view-a-shaders-source-code"></a>檢視著色器的原始程式碼  
  
1. 在 [圖形像素歷程記錄] 視窗中，找出與您要檢查之著色器對應的繪製呼叫，並將其展開。  
  
2. 在您剛剛展開的繪製呼叫下，選取可示範您感興趣問題的基本項目，並將其展開。  
  
3. 在您感興趣的基本項目下，遵循著色器標題連結；例如，遵循 [頂點著色器 obj:30] 連結檢視頂點著色器原始程式碼。  
  
    > [!TIP]
    > 物件編號 **obj:30** 可在整個圖形分析器介面中識別此著色器 (例如在物件資料表和管線階段視窗中)。  
  
##### <a name="to-debug-a-shader"></a>偵錯著色器  
  
1. 在 [圖形像素歷程記錄] 視窗中，找出與您要檢查之著色器對應的繪製呼叫，並將其展開。  
  
2. 然後，在您剛剛展開的繪製呼叫下，選取可示範您感興趣問題的基本項目，並將其展開。  
  
3. 在您感興趣的基本項目下，選擇 [開始偵錯]。 這個 HLSL 偵錯工具進入點預設為對應基本項目的第一個著色器引動過程，也就是著色器所處理的第一個像素或頂點。 只有一個與基本項目相關聯的像素，但線條和三角形有多個頂點著色器引動過程。  
  
     若要偵錯特定頂點的頂點著色器引動過程，請展開 VertexShader 標題連結，並找出您感興趣的頂點，然後選擇旁邊的 [開始偵錯]。  
  
### <a name="links-to-graphics-objects"></a>圖形物件連結  
 若要了解像素歷史記錄中的圖形事件，您可能需要發生事件時的裝置狀態相關資訊，或是事件參考之 Direct3D 物件的相關資訊。 針對像素歷程記錄中的每個事件，[圖形像素歷程記錄] 都會提供「當時-目前」(then-current) 裝置狀態的連結，以及相關物件的連結。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：因裝置狀態而遺漏的物件](../debugger/walkthrough-missing-objects-due-to-device-state.md)   
 [逐步解說：針對因著色而產生的顯示錯誤進行偵錯](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)
