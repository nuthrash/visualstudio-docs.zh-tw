---
title: 擴充專案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d31da41e3be73f4e2e036841bfc1d96f4476e856
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912801"
---
# <a name="extend-projects"></a>擴充專案
專案和方案是 Visual Studio 會將程式碼和資源檔組織成編譯和部署單位的方式。 您可以找到有關中專案的詳細資訊[專案 (Visual Studio SDK)](../extensibility/extending-projects.md)。

 您可以建立您自己的專案類型使用 Visual Studio SDK 和 Managed Package Framework 中的專案，您可以在下載[專案的 Managed Package Framework](https://github.com/tunnelvisionlabs/MPFProj10)。 若要了解如何實作自訂專案，請參閱[產生新專案：在幕後，第一部](../extensibility/internals/new-project-generation-under-the-hood-part-one.md)和[產生新專案：在幕後，第二部](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 在本節中的主題描述如何建立自訂專案以及如何管理不同類型的 Visual Studio 方案。

## <a name="in-this-section"></a>本節內容
- [建立基本專案系統，第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)說明如何建立自訂專案系統。

- [建立基本專案系統，第 2 部分](../extensibility/creating-a-basic-project-system-part-2.md)說明如何建立自訂專案系統。

- [將資料儲存在專案檔](../extensibility/saving-data-in-project-files.md)Explains 如何新增至專案 (<em>。</em>proj *） 檔案。

- [在執行階段驗證的專案子類型](../extensibility/verifying-subtypes-of-a-project-at-run-time.md)說明如何在執行階段驗證的專案子類型。

- [新增和移除屬性頁](../extensibility/adding-and-removing-property-pages.md)說明如何自訂您的自訂專案的屬性頁。

- [將屬性加入專案項目](../extensibility/adding-an-attribute-to-a-project-item.md)說明如何將屬性加入自訂專案項目。

- [保存專案項目的屬性](../extensibility/persisting-the-property-of-a-project-item.md)說明如何保存屬性的自訂專案項目。

- [管理通用 Windows 專案](../extensibility/managing-universal-windows-projects.md)說明如何管理通用專案。