---
title: 檢查清單： 建立新的專案類型 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f73462d32e0b047e0b2427646cfc5a3709c5e78a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485552"
---
# <a name="checklist-creating-new-project-types"></a>檢查清單︰建立新的專案類型
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[檢查清單： 建立新的專案類型](https://docs.microsoft.com/visualstudio/extensibility/internals/checklist-creating-new-project-types)。  
  
您必須完成數個工作，以建立新的專案類型。 下列檢查清單提供這些工作的指南。  
  
1.  設計新的專案類型的功能。 如需詳細資訊，請參閱 <<c0> [ 專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)。  
  
2.  判斷哪一個編輯器用於程式碼和其他專案項目。 您可以使用核心或標準的編輯器，或您可以建立並使用專案特定的編輯器。 如需詳細資訊，請參閱 <<c0> [ 建立自訂編輯器和設計師](../../extensibility/creating-custom-editors-and-designers.md)並[如何： 開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)。  
  
3.  判斷您的專案項目都會在的參與的層級**類別檢視**並**物件瀏覽器**。 如需詳細資訊，請參閱 <<c0> [ 支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。  
  
4.  衍生新類別，根據您為您的專案和專案項目之前做的設計決策。  
  
5.  撰寫下列專案類型元件的程式碼：  
  
    -   Project factory，來管理建立新的專案，並開啟現有專案。 如需詳細資訊，請參閱 <<c0> [ 建立專案執行個體所使用 Project Factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。  
  
    -   專案階層架構和命令處理。 如需詳細資訊，請參閱 <<c0> [ 不在組建中： 使用 HierUtil7 專案類別以實作專案類型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)，[專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)，[專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)和[Menucommand 對比。OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)。  
  
    -   專案項目管理，包括加入您的專案**新的專案** 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)並[註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
    -   持續性的專案狀態與個別項目。 如需詳細資訊，請參閱 <<c0> [ 開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。 持續性解決方案的資訊，請參閱 <<c0> [ 解決方案](../../extensibility/internals/solutions.md)。  
  
    -   設定要顯示在 [屬性] 視窗中的獨立屬性。 如需詳細資訊，請參閱 <<c0> [ 擴充屬性](../../extensibility/internals/extending-properties.md)。  
  
    -   若要顯示組態相依屬性的屬性頁中實作時，專案組態屬性。 如需詳細資訊，請參閱 <<c0> [ 管理組態選項](../../extensibility/internals/managing-configuration-options.md)。  
  
    -   列舉部署的輸出。 如需詳細資訊，請參閱 <<c0> [ 輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)。  
  
    -   專案的啟動服務。 如需詳細資訊，請參閱 <<c0> [ 專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)並[專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)。  
  
    -   物件或衍生自類別`IDispatch`，其可供自動化。  
  
    -   XML 命令表 (.vsct) 檔案。 如需詳細資訊，請參閱[Visual Studio Command Table (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
6.  測試、 偵錯，並啟動您的專案類型。  
  
7.  顯示您的專案中**專案**索引標籤**加入參考**對話方塊中，藉由設定`VARIANT_TRUE`做為值`VSHPROPID_ShowProjInSolutionPage`。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 與 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>。  
  
8.  建立 Microsoft Installer (.msi) 檔案，安裝您的 Vspackage。 如需詳細資訊，請參閱 <<c0> [ 使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)，[註冊專案類型](../../extensibility/internals/registering-a-project-type.md)，並[Vspackage](../../extensibility/internals/vspackages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [建立專案類型的時機](../../extensibility/internals/when-to-create-project-types.md)   
 [建立專案類型](../../extensibility/internals/creating-project-types.md)
