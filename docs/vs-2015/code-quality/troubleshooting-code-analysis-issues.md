---
title: 針對程式碼分析問題進行疑難排解 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: erickson-doug
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 047866f958ebfe6de20d5f7760b72eaab4135ef1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62551464"
---
# <a name="troubleshooting-code-analysis-issues"></a>程式碼分析問題疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題包含下列 Visual Studio 程式碼分析問題的疑難排解資訊。  
  
- [舊版 Visual Studio 不會反映 Visual Studio 2010 規則集變更](#ChildRuleSetChangesInPreviousVersions)  
  
## <a name="ChildRuleSetChangesInPreviousVersions"></a> 舊版 Visual Studio 不會反映 Visual Studio 2010 規則集變更  
 當您在 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 中建立包含子規則集的規則集時，於使用舊版 Visual Studio 的電腦上，子規則集變更可能不會套用至程式碼分析回合。 若要解決此問題，您必須強制重寫父代規則集 (即包含子規則集的規則集)。  
  
1. 在 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 中，開啟父代規則集。  
  
2. 進行變更 (例如新增或移除規則)，然後儲存規則集。  
  
3. 重新開啟規則集，並回復變更，然後重新儲存規則集。  
  
## <a name="see-also"></a>另請參閱  
 [分析應用程式品質](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
