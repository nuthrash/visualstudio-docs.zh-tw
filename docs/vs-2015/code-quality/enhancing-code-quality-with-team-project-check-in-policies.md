---
title: 強化與 Team 專案簽入原則的程式碼品質 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 31859128aed64ec6a1182f085685b2e82e485f84
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437064"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>使用 Team 專案簽入原則強化程式碼品質
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您使用 Team Foundation 版本控制 (TFVC) 時，您可以建立 Team 專案的簽入原則。 強制執行會得到較佳程式碼和較有效的團體開發的做法。 簽入原則是在 Team 專案層級設定的規則，而且會在允許程式碼簽入之前，於開發人員電腦上強制執行。  
  
 您可以指定這些 Team 專案簽入原則：  
  
- **建置**:需要，必須新簽入之前修復在建置期間所建立的建置中斷。  
  
- **變更集註解**:需要使用者在簽入變更時，會提供註解。  
  
- **程式碼分析**:需要簽入之前執行程式碼分析。  
  
- **工作項目**:需要一或多個工作項目要與此簽入相關聯。  
  
> [!IMPORTANT]
> 若要使用簽入原則，您必須連接到 [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)]。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|支援內容|  
|----------|------------------------|  
|**建立和使用簽入原則：** 使用 Team 專案設定建立簽入原則[!INCLUDE[esprscc](../includes/esprscc-md.md)]。|[品質嚴格把關](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**建立並使用程式碼分析簽入原則：** 您可以選擇從一組標準的程式碼分析規則，或者您可以建立一組自訂。|[建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>相關工作  
  
|工作|支援內容|  
|----------|------------------------|  
|**設定您的開發環境：** 您可以建立或修改程式碼之前，您必須設定您的開發和測試環境使用適當的原始程式碼。 如果使用資料庫，也必須有其離線表示的存取權限。|[設定開發環境](http://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**在開發過程中使用程式碼分析：** 小組成員在其開發電腦上執行程式碼分析。 在 Visual Studio 中，開發人員會針對個別程式碼專案設定並執行程式碼分析回合、檢視及分析回合中找到的問題，以及建立警告的工作項目。|[分析應用程式品質](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**建立及執行單元測試：** 單元測試提供開發人員和測試人員快速的方法，以查看方法的類別中的邏輯錯誤C#，Visual Basic.NET 和C++專案。 您只要建立一次單元測試，就可以在每次原始程式碼變更時執行，以確定沒有導入任何錯誤。|[對程式碼進行單元測試](../test/unit-test-your-code.md)|  
|**追蹤工作項目和缺失：** 您可以使用工作項目來追蹤和管理您的工作和資訊，關於您的 team 專案。 工作項目是資料庫記錄， [!INCLUDE[esprfound](../includes/esprfound-md.md)] 用來追蹤指派和工作進度。 您可以使用不同類型的工作項目來追蹤不同類型的工作，例如客戶需求、產品錯誤及開發工作。|[追蹤工作和管理工作流程&#91;重新導向&#93;](http://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>外部資源  
  
### <a name="guidance"></a>指引  
 [測試 for Continuous Delivery with Visual Studio 2012 – 第 2 章：單元測試：測試內部](http://go.microsoft.com/fwlink/?LinkID=255188)
