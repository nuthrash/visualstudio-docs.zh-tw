---
title: HOW TO：安裝視覺化檢視 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726cea8b2e81c53b5f3fff963357946f26b199f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438232"
---
# <a name="how-to-install-a-visualizer"></a>HOW TO：安裝視覺化檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

建立視覺化檢視後，您必須安裝該視覺化檢視，使 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中可以使用它。 安裝視覺化檢視的程序很簡單。  
  
> [!NOTE]
> 在 **存放區**應用程式，僅限標準的文字，支援 HTML、 XML 及 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。  
  
### <a name="to-install-a-visualizer"></a>安裝視覺化檢視  
  
1. 找出包含您已建置之視覺化檢視的 DLL。  
  
2. 將該 DLL 複製至下列其中一個位置：  
  
    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3. 如果要使用 Managed 視覺化檢視進行遠端偵錯，請將 DLL 複製到遠端電腦上的相同路徑中。  
  
4. 重新啟動偵錯工作階段。  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
 [如何：撰寫視覺化檢視](../debugger/how-to-write-a-visualizer.md)
