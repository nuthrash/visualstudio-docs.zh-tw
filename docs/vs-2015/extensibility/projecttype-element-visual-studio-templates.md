---
title: ProjectType 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b01dd370fe5e3d7a5207363c5ab7ec4f2a0254c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388397"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將分類的專案範本，使其出現在中指定的群組**新的專案**或**加入新項目** 對話方塊。  
  
> [!WARNING]
> 支援的專案範本C++開始在 Visual Studio 2012 中。 它們不支援C++在 Visual Studio 2010 和舊版中。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectType>  
  
## <a name="syntax"></a>語法  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 這個值會指定的專案範本類型會建立，而且必須包含下列值之一：  
  
- `CSharp`：指定此範本會建立[!INCLUDE[csprcs](../includes/csprcs-md.md)]專案或項目。  
  
- `VisualBasic`：指定此範本會建立[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]專案或項目。  
  
- `Web`：指定此範本會建立 Web 專案或項目。 如果`ProjectType`項目會包含此值，項目之專案的語言定義於[ProjectSubType 項目 （Visual Studio 範本）](../extensibility/projectsubtype-element-visual-studio-templates.md)。  
  
## <a name="remarks"></a>備註  
 `ProjectType` 是 `TemplateData` 的必要子項目。  
  
 值`ProjectType`項目會指定範本的位置**新增專案**或是**加入新項目** 對話方塊。 比方說，使用範本`ProjectType`的值`CSharp`下方將會出現**Visual C#** 節點中的**新專案** 對話方塊。  
  
 只有 template 子類型可以指定使用[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)項目。  
  
## <a name="example"></a>範例  
 下列範例顯示的專案範本的中繼資料[!INCLUDE[csprcs](../includes/csprcs-md.md)]應用程式。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
</VSTemplate>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [ProjectSubType 元素 (Visual Studio 範本)](../extensibility/projectsubtype-element-visual-studio-templates.md)
