---
title: 使用效能資料檔案儲存符號資訊 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9d2e8b0414746523d0f76e8266f6463d9c05574
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098881"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>使用效能資料檔案儲存符號資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 整合式開發環境 (IDE) 分析檔案，並打算將 VSP 檔移至不同的電腦，您必須將效能專案設定設為儲存或「序列化」報告檔中的符號。 這樣會增加報告檔的大小。 必須將符號序列化的原因有兩個︰  
  
- 在目標組件從其暫時儲存區的位置遺失之前，將程式碼符號內嵌到效能報表。  
  
- 保留符號以便將效能報表從已分析的電腦攜出，並可在另一部可能有不同符號的電腦上開啟報表進行分析時，輸出相同的資訊。  
  
  **需求**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、[!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  您可以從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 或從命令列將符號序列化︰  
  
- 若要在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 中將符號序列化，請指向功能表列上的 [工具]，然後按一下 [選項]。 在 [選項] 視窗中，選取 [效能工具]，然後選取 [自動序列化符號資訊] 核取方塊。  
  
- 當您儲存報告檔時，PACKSYMBOLS 等同於命令列選項。 若要將符號序列化，輸入 **vsperfreport /summary:all /packsymbols filename.vsp**。  
  
## <a name="troubleshooting-symbol-problems"></a>符號問題疑難排解  
 如果您在自己的程式碼中看不見任何符號，一些常見的可用解決方案如下︰  
  
- 在命令列執行 vsperfreport /debugsympath 以顯示完整的清單，列出分析工具元件載入符號資訊的位置，以及使用的符號檔案是否符合您的專案使用的檔案。  
  
- 請務必在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 中搭配 /PACKSYMBOLS 旗標來執行 vsperfreport，或是在一般效能總管選項中選取序列化符號資訊的選項。  
  
- 如果您已收集類型資料，請將 /SUMMARY:TYPE 加入至 vsperfreport 命令列。  
  
  如果從 Windows 或其他 Microsoft 程式都看不到符號︰  
  
- 請確定您已設定 Windows 符號快取的路徑。 請執行下列其中一項動作來設定符號快取路徑︰  
  
  - 將 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 中的 [偵錯工具] -> [符號] 選項設定為正確的路徑。  
  
  - 將 -symbolpath 選項加入至 VSPerfReport 命令列以納入您的符號。  
  
- 如果您在 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 中看不到任何符號，請確定您已將符號伺服器已正確設定成 ASP 伺服器。  
  
## <a name="repacking-symbols"></a>重新封裝符號  
 如果您想要將符號重新封裝至報表，您可以使用命令列工具 VsPerfReport 來完成這項動作。 請使用以下命令列：  
  
 VsPerfReport -clearpackedsymbols filename.vsp  
  
 VsPerfReport -packsymbols -summary:all filename.vsp  
  
## <a name="see-also"></a>另請參閱  
 [儲存和匯出效能工具資料](../profiling/saving-and-exporting-performance-tools-data.md)   
 [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
