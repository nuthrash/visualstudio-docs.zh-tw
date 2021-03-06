---
title: HOW TO：使用內建可設定色彩的項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d8994270ece639cc7d22a27af6339d525ff3618
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420514"
---
# <a name="how-to-use-built-in-colorable-items"></a>HOW TO：使用內建可設定色彩的項目
使用內建可設定色彩的項目之前，您必須先通知整合式的開發環境 (IDE)，您不會提供您自己自訂色彩項目，在此情況下會<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>物件。 您可以設定語言服務的登錄項目。

## <a name="to-use-built-in-colorable-items"></a>若要使用內建可設定色彩的項目

1. 底下**HKEY_LOCAL_MACHINE\VisualStudio\\< X.Y > \Languages\Language Services\\< 語言名稱\>**，其中\<X.Y > 版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和\<語言名稱 > 是名稱的語言，建立 DWORD 登錄項目值呼叫**RequestStockColors**。

2. 設定**RequestStockColors**登錄項目值要*1*。

    您建立的登錄項目，您的色彩標示器的後<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法可以使用的成員<xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS>來填滿色彩編輯器所使用的屬性陣列中的列舉。

   > [!NOTE]
   > 如果您要提供自訂色彩的項目，請不要設定此登錄項目。 如需詳細資訊，請參閱 <<c0> [ 自訂色彩項目](../../extensibility/internals/custom-colorable-items.md)。

## <a name="see-also"></a>另請參閱
- [自訂編輯器中的語法著色](../../extensibility/syntax-coloring-in-custom-editors.md)
- [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)
- [自訂色彩的項目](../../extensibility/internals/custom-colorable-items.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)