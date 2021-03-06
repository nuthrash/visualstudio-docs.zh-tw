---
title: HOW TO：編輯 XML 檔案
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b25eebad9efc70e4fda45131e232983e81961625
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840365"
---
# <a name="how-to-edit-xml-files"></a>HOW TO：編輯 XML 檔案

XML 編輯器是 XML 檔案的新編輯器。 它可用於獨立 XML 檔案或與 Visual Studio 專案相關的檔案上。 XML 編輯器是具有下列副檔名相關聯： *.config*， *.dtd*， *.xml*， *.xsd*， *.xdr*， *.xsl*， *.xslt*，和 *.vssettings*。 XML 編輯器也會與任何其他檔案類型，其沒有登錄特定編輯器，並包含 XML 或 DTD 內容相關聯的。

> [!NOTE]
> HTML 編輯器可處理 XHTML 文件。

若要編輯的 XML 檔案，按兩下您想要編輯的檔案。

## <a name="add-a-new-xml-file-to-a-project"></a>將新的 XML 檔案加入專案

1. 從**專案**功能表上，選取**加入新項目**。

2. 選取  **XML 檔案**從**範本**窗格。

3. 輸入中的檔案名稱**名稱**欄位，然後按**新增**。

   XML 檔案加入至專案，並在 XML 編輯器中開啟。 檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8" ?>`。

## <a name="add-an-existing-xml-file-to-a-project"></a>將現有的 XML 檔案加入專案

1. 從**專案**功能表上，選取**加入現有項目**。

   **加入現有項目** 對話方塊隨即出現。

2. 選取 XML 檔案並按**新增**。

## <a name="create-a-new-xml-or-xslt-file"></a>建立新的 XML 或 XSLT 檔案

1. 從**檔案**功能表上，選取**新增**。

   **新的檔案** 對話方塊隨即出現。

2. 選取  **XML 檔案**來建立新的 XML 檔案; 或者，選取**XSLT 檔**來建立新的 XSLT 樣式表。

3. 按一下 [開啟]。

## <a name="create-an-empty-project-for-xml-files"></a>建立 XML 檔案的空白專案

::: moniker range="vs-2017"

1. 從**檔案**功能表上，選取**新增** > **專案**。

   [ **新增專案** ] 對話方塊隨即出現。

2. 選取您的選擇，選取的程式碼語言**空專案**。

3. 按一下 [確定] 。

::: moniker-end

::: moniker range=">=vs-2019"

1. 從**檔案**功能表上，選取**新增** > **專案**。

2. 請輸入**空專案**在範本的 搜尋 方塊中選取**空白專案 (.NET Framework)** 範本，然後再按**下一步**。

3. 按一下 [建立] 。

::: moniker-end

4. 將 XML 檔案加入至專案。

   XML 編輯器中尋找您新增至這個專案的結構描述，並使用它們進行驗證，並在任何 XML、 結構描述或您編輯此專案開啟時的 XSLT 檔案中的 IntelliSense。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
- [屬性視窗、 XML 文件屬性](../xml-tools/xml-document-properties-properties-window.md)
- [如何：從 XML 文件建立 XML 結構描述](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)