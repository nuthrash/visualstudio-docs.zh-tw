---
title: 變更檢視設定，以使用舊版 API |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094121"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>變更檢視設定，以使用舊版 API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

設定核心編輯器功能，例如自動換行、 選取範圍邊界和虛擬空間，可以藉由使用者變更**選項** 對話方塊。 不過，您也可變更這些設定以程式設計的方式。  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>變更設定，以使用舊版 API  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面會公開一組文字編輯器的屬性。 文字檢視包含的屬性 (GUID_EditPropCategory_View_MasterSettings) 的類別，表示文字檢視以程式設計方式變更設定的群組。 檢視設定已變更這種方式之後, 就無法變更在**選項**對話方塊，直到它們重設。  
  
 以下是變更檢視設定的核心編輯器執行個體的一般程序。  
  
1. 呼叫`QueryInterface`上 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) 的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面。  
  
2. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>方法，並指定值的 GUID_EditPropCategory_View_MasterSettings`rguidCategory`參數。  
  
     執行此動作將指標傳回至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面，其中包含一組檢視的強制屬性。 永遠強制在這個群組中的任何設定。 如果設定不屬於此群組中，則它會遵循指定的選項**選項**對話方塊或使用者的命令。  
  
3. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>方法，並指定適當的設定值，在`idprop`參數。  
  
     例如，若要強制自動換行，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>及指定 VSEDITPROPID_ViewLangOpt_WordWrap，值`vt`如`idprop`參數。 在此呼叫中，`vt`是型別 VT_BOOL 的變化和`vt.boolVal`為 VARIANT_TRUE。  
  
## <a name="resetting-changed-view-settings"></a>重設已變更的檢視設定  
 若要重設任何已變更的檢視，核心編輯器執行個體設定，請呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>方法並指定適當的設定值，在`idprop`參數。  
  
 例如，若要允許自動換行自由浮動，您會移除它屬性類別目錄藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>和指定的值是針對 VSEDITPROPID_ViewLangOpt_WordWrap`idprop`參數。  
  
 若要一次移除所有已變更的設定，核心編輯器，請指定 VSEDITPROPID_ViewComposite_AllCodeWindowDefaults，如 vt 值`idprop`參數。 在此呼叫中，vt VT_BOOL 類型的 VARIANT 而且 vt.boolVal 為 VARIANT_TRUE。  
  
## <a name="see-also"></a>另請參閱  
 [在核心編輯器](../extensibility/inside-the-core-editor.md)   
 [使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [選項對話方塊](../ide/reference/options-dialog-box-visual-studio.md)
