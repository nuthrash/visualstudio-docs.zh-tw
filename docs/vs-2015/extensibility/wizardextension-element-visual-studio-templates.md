---
title: WizardExtension 項目 （Visual Studio 範本） |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7b8a9a788fb2c229791e0ca099e307e6279fd3e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499193"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[WizardExtension 項目 （Visual Studio 範本）](https://docs.microsoft.com/visualstudio/extensibility/wizardextension-element-visual-studio-templates)。  
  
包含自訂範本精靈 的註冊項目。  
  
 \<VSTemplate >  
 ...  
 \<WizardExtension >  
  
## <a name="syntax"></a>語法  
  
```  
<WizardExtension>  
    <Assembly>... </Assembly>  
    <FullClassName>... </FullClassName>  
</WizardExtension>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|必要項目。<br /><br /> 指定的名稱或組件出現在全域組件快取中的強式名稱。 必須有至少一個`Assembly`中的項目`WizardExtension`項目。|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|必要項目。<br /><br /> 實作的類別完整的名稱`IWizard`介面。 必須有至少一個`FullClassName`中的項目`WizardExtension`項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|包含專案範本、 項目範本，或入門套件的所有中繼資料。|  
  
## <a name="remarks"></a>備註  
 `WizardExtension` 是 `VSTemplate` 的選擇性子項目。  
  
## <a name="example"></a>範例  
 下列範例說明的標準專案範本的中繼資料[!INCLUDE[csprcs](../includes/csprcs-md.md)]Windows 應用程式。  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [如何︰搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)
