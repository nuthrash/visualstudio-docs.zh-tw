---
title: UsedCommand 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50cac2607a27443ef5a24ce00f34425ca418c513
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62798414"
---
# <a name="usedcommand-element"></a>UsedCommand 項目
可讓 VSPackage 也可以存取另一個.vsct 檔案中定義的命令。 例如，如果您的 VSPackage 會使用標準**複製**命令，可定義[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]shell 中，您可以將命令加入功能表或工具列而不需要重新實作它。

## <a name="syntax"></a>語法

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要項。 識別命令的 GUID 識別碼組的 GUID。|
|id|必要項。 識別命令的 GUID 識別碼組識別碼。|
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|群組 UsedCommand 元素，而且其他 UsedCommands 分組。|

## <a name="remarks"></a>備註
 將命令新增至`<UsedCommands>`元素，VSPackage 會通知[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage，需要此命令的環境。 您應該加入`<UsedCommand>`封裝需要的任何命令的項目可能不會包含於所有版本的 Visual Studio 的設定。 例如，如果您的封裝呼叫特定視覺效果的命令C++，無法使用的 Visual Web Developer 使用者命令，除非您將包含`<UsedCommand>`命令的項目。

## <a name="example"></a>範例

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>另請參閱
- [UsedCommands 元素](../extensibility/usedcommands-element.md)
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)