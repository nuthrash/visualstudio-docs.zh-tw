---
title: IDebugDocumentText 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8878e1ce6e9ad05fc94b134a2e71847b67d578d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008611"
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText 介面
存取純文字版的偵錯文件。 這個介面會使用下列慣例：  
  
- 字元位置和行號是以零為起始。  
  
- 字元位置代表字元位移。它們不代表位元組或字組位移。 為 Win32，字元位置會是 Unicode 位移。  
  
  除了繼承自方法`IDebugDocument`，則`IDebugDocumentText`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|傳回文件的屬性。|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|傳回文件中的行數和字元數。|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|傳回對應到一行的第一個字元的字元位置。|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|傳回指定的字元位置的行號，並選擇性地對應之行內的字元位移。|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|擷取字元和/或字元相關聯的屬性中的字元位置範圍。|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|傳回對應至文件內容的字元位置範圍。|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|建立文件內容物件，對應至提供的字元位置範圍。|