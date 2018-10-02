---
title: 圖形物件表 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64c2cf7af6c7133182d915c62aa763b2d8718c90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498404"
---
# <a name="graphics-object-table"></a>圖形物件表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[圖形物件表](https://docs.microsoft.com/visualstudio/debugger/graphics/graphics-object-table)。  
  
Visual Studio 圖形分析中的 [圖形物件表] 可協助您了解支援您遊戲或應用程式之畫面格的 Direct3D 物件。  
  
 這是 [物件表]：  
  
 ![已建立的應用程式的 Direct3D 物件](../debugger/media/gfx-diag-demo-object-table-orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>了解圖形物件表  
 藉由使用 [物件表]，您可以分析支援轉譯特定畫面格的 Direct3D 物件。 檢查特定物件的屬性和資料，即可找出其轉譯問題 (提早使用其他圖形診斷工具來進行診斷，可以縮小非您預期之物件的清單)。當您發現不當的物件時，您可以使用來加以檢查其類型專屬的視覺效果，例如，您可以使用影像編輯器來檢視紋理，或*緩衝區視覺化檢視*來檢視緩衝區內容。  
  
 [物件表] 支援複製並貼上，讓您可以使用其他工具 (例如 Microsoft Excel) 來檢查其內容。  
  
### <a name="graphics-object-table-format"></a>圖形物件表格式  
 [物件表] 會顯示支援與所選事件相關聯之畫面格的 Direct3D 物件和資源，例如狀態物件、緩衝區、著色器、紋理和其他資源。 物件表會略過在先前畫面格中建立，但未於所擷取的畫面格期間使用的物件。 在後續事件中，將會略過在擷取的畫面格期間被先前事件損毀的物件。 未設定在 D3D10Device 或 D3D11DeviceContext 上的物件會以灰色文字顯示。 物件會以表格格式顯示。  
  
|Column|描述|  
|------------|-----------------|  
|**識別碼**|物件識別碼。|  
|**名稱**|使用 Direct3D 函式 `SetPrivateData` 設定在物件上的應用程式特定資訊 (通常是為了提供物件的其他識別資訊)。|  
|**Type**|物件類型。|  
|**使用中**|針對在擷取的畫面格期間設定在 D3D10Device 或 D3D11DeviceContext 上的物件，會顯示 "*"。<br /><br /> 這會對應至顯示為灰色文字的物件，但會提供資料行項目，可讓您用來協助排序物件表。|  
|**Size**|物件大小 (以位元組為單位)。|  
|**格式**|物件的格式。 例如，紋理物件的格式，或是著色器物件的著色器模型。|  
|**寬度**|紋理物件的寬度。 不會套用到其他物件類型。|  
|**高度**|紋理物件的高度。 不會套用到其他物件類型。|  
|**深度**|3-D 紋理物件的深度。 如果紋理不是 3-D，則該值為 0。 不會套用到其他物件類型。|  
|**Mips**|紋理物件具有的 MIP 層級數目。 不會套用到其他物件類型。|  
|**ArraySize**|紋理陣列中的紋理數目。 範圍是從 1 到目前功能層級所定義的上限。 對於 cube-map，這個值是陣列之 cube-map 數目的 6 倍。|  
|**範例**|每個像素的多重樣本數目。|  
  
## <a name="graphics-object-viewers"></a>圖形物件檢視器  
 若要檢視物件的詳細資料，請在 [物件表] 中選擇其名稱將其開啟。 物件的詳細資料會以不同格式顯示，視物件的類型而定。 例如，使用紋理檢視器來顯示紋理，以及裝置狀態 (例如 D3D11 裝置內容) 會顯示為格式化清單。 不同版本的 Direct3D 利用不同的物件，而且每個版本的最重要物件通常會有特定視覺化檢視。  
  
 以下是紋理檢視器，其顯示 [輸出合併] 管線階段的內容。  
  
 ![顯示輸出合併的紋理預覽](../debugger/media/gfx-diag-texture-preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>D3D12 命令清單  
 在 Direct3D 12 中，命令清單是一個物件，可將命令記錄至命令配置器，以做為單一要求送出給 GPU。 命令清單通常會執行一系列的狀態設定、繪圖、清除和複製命令。 它們特別重要，因為它們是 Direct3D 12 中的慣用轉譯方法，而且可以在畫面格之間重複使用以協助提高效能。 命令清單詳細資料會顯示在新的文件視窗中，內含其專屬索引標籤上呈現之每個管線階段的相關資訊。  
  
### <a name="d3d12-pipeline-state-object-pso"></a>D3D12 管線狀態物件 (PSO)  
 在 Direct3D 12 中，管線狀態物件會代表 GPU 狀態的重要部分 (包括所有目前設定的著色器和特定固定函式狀態物件)。 建立之後，管線狀態物件是不可變的；應用程式僅可透過繫結不同的管線狀態物件來變更管線的組態。 PSO 詳細資料會顯示在新的文件視窗中，內含以階層方式安排管線組態的詳細資料。  
  
### <a name="d3d12-root-signature"></a>D3D12 根簽章  
 在 Direct3D 12 中，根簽章會定義繫結至圖形或計算管線的所有資源，並將命令清單連結至著色器所需的資源。 通常，在應用程式中，圖形會有一個根簽章，而計算會有一個根簽章。 根簽章詳細資料會顯示在新的文件視窗中，內含以階層方式安排根簽章的詳細資料。  
  
### <a name="d3d12-resources"></a>D3D12 資源  
 在 Direct3D 12 中，資源是將資料提供給轉譯管線的 catch-all 物件；這與 Direct3D11 相反，其定義不同類型和維度之資源的許多特定物件。 Direct3D 12 資源可以包含紋理資料、頂點資料、著色器資料等；它們甚至可以代表轉譯目標 (例如深度緩衝區)。 Direct3D 12 資源的詳細資料會顯示在新的文件視窗中；圖形分析會使用資源物件內容的適當檢視器 (如果可以判斷其類型)。 例如，會使用紋理檢視器顯示包含紋理資料的資源物件，就像 D3D11 Texture2D 物件一樣。  
  
### <a name="device-context-object"></a>裝置內容物件  
 在 Direct3D 11 和 Direct3D 10 的裝置內容 (**D3D11 裝置內容**或是**D3D10 裝置**) 物件是特別重要，因為它保存最重要的狀態資訊，而且它會連結到其他目前所設定的狀態物件。 裝置內容詳細資料會顯示在新的文件視窗中，而每種類別的資訊會顯示在其索引標籤上。選取新的事件時裝置內容會變更，以反映目前的裝置狀態。  
  
### <a name="buffer-object"></a>緩衝區物件  
 緩衝區物件詳細資料 (D3D11 緩衝區或 D3D10 緩衝區) 會顯示在新的文件視窗中，其中會顯示表格中的緩衝區內容，並提供介面變更緩衝區內容的顯示方式。 **緩衝資料**表格支援複製並貼上，讓您可以使用其他工具 — 比方說，Microsoft Excel，來檢查其內容。 緩衝區的內容會根據值的解譯**格式**下拉式方塊中，位於上述**緩衝資料**資料表。 在該方塊中，您可以輸入由下表列示之資料類型組成的複合資料格式。 例如，"float int" 會顯示一個結構清單，其中包含 32 位元浮點值，後面接著 32 位元帶正負號的整數值。 您所指定的複合資料格式會新增至下拉式方塊，以供日後使用。  
  
 您也可以切換**顯示位移**核取方塊以隱藏或顯示緩衝區中的每個項目的位移。  
  
|類型|描述|  
|----------|-----------------|  
|**float**|32 位元浮點值。|  
|**float2**|包含兩個 32 位元浮點值的向量。|  
|**float3**|包含三個 32 位元浮點值的向量。|  
|**float4**|包含四個 32 位元浮點值的向量。|  
|**byte**|8 位元帶正負號的整數值。|  
|**2 個位元組**|16 位元帶正負號的整數值。|  
|**4 位元組**|32 位元帶正負號的整數值。 與相同**int**。|  
|**8 位元組**|64 位元帶正負號的整數值。 與相同**int64**。|  
|**請 xbyte**|8 位元的十六進位值。|  
|**x2byte**|16 位元的十六進位值。|  
|**x4byte**|32 位元的十六進位值。 與相同**xint**。|  
|**x8byte**|64 位元的十六進位值。 與相同**xint64**。|  
|**ubyte**|8 位元不帶正負號的整數值。|  
|**u2byte**|16 位元不帶正負號的整數值。|  
|**u4byte**|32 位元不帶正負號的整數值。 與相同**uint**。|  
|**u8byte**|64 位元不帶正負號的整數值。 與相同**uint64**。|  
|**一半**|16 位元浮點值。|  
|**half2**|包含兩個 16 位元浮點值的向量。|  
|**half3**|包含三個 16 位元浮點值的向量。|  
|**half4**|包含四個 16 位元浮點值的向量。|  
|**double**|64 位元浮點值。|  
|**int**|32 位元帶正負號的整數值。 與相同**4 位元組**。|  
|**int64**|64 位元帶正負號的整數值。 與相同**8 位元組**。|  
|**xint**|32 位元的十六進位值。 與相同**x4byte**。|  
|**xint64**|64 位元的十六進位值。 與相同**x8byte**。|  
|**uint**|32 位元不帶正負號的整數值。 與相同**u4byte**。|  
|**uint64**|64 位元不帶正負號的整數值。 與相同**u8byte**。|  
|**bool**|布林 (`true` 或 `false`) 值。 每個布林值會以 32 位元值表示。|  
  
## <a name="see-also"></a>另請參閱  
 [圖形診斷 （偵錯 DirectX 圖形）](../debugger/visual-studio-graphics-diagnostics.md)   
 [逐步解說：因裝置狀態而遺漏的物件](../debugger/walkthrough-missing-objects-due-to-device-state.md)


