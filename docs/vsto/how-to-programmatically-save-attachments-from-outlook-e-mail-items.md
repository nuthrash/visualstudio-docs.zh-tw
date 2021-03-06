---
title: HOW TO：以程式設計方式儲存附件，從 Outlook 電子郵件項目
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 874f19e0ae4e752a36ce95deab669ab46bfbf038
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419498"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>HOW TO：以程式設計方式儲存附件，從 Outlook 電子郵件項目
  這個範例會在收件匣中收到郵件時，將電子郵件附件儲存至指定的資料夾。

> [!IMPORTANT]
> 這個範例才能運作，只有當您將新增名為的資料夾時，才**TestFileSave** C 目錄的根目錄。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用郵件項目](../vsto/working-with-mail-items.md)
- [如何：以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [如何：以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
