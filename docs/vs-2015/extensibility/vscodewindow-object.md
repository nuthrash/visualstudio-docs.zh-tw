---
title: VSCodeWindow Object | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1711b1409e42d431ad34badf82cff68e5a9bad75
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62421898"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼視窗是一種特殊的文件視窗，通常可以包含一或多個文字檢視，<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>物件。  
  
 在架構上，程式碼視窗會在視窗框架內的文件視窗。 在功能上，程式碼視窗只是文件視窗以及額外的功能。 在多重文件介面 (MDI) 模式中，程式碼視窗會是 MDI 子框架。 如需詳細資訊，請參閱 <<c0> [ 使用舊版 API 的自訂程式碼 Windows](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)。  
  
 下表包含中的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>物件。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供一般存取機制，來找出全域唯一識別碼 (GUID) 識別服務。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|表示多個文件介面 (MDI) 子系包含一個或多個程式碼檢視。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填滿視窗框架。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [圖形編輯](http://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
