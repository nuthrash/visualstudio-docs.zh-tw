---
title: 無法刪除所選取的類別，因為它是用來當做一或多個 DataContext 方法的傳回類型。
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5d63abefc67d54734380e6a1dc7f3364d5400c03
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565416"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>無法刪除所選取的類別，因為它是用來當做一或多個 DataContext 方法的傳回類型。

有一個或多個 <xref:System.Data.Linq.DataContext> 方法的傳回型別是選取的實體類別 (Class)。 刪除實體類別，可做為傳回型別<xref:System.Data.Linq.DataContext>方法會使專案編譯作業失敗。 若要刪除選取的實體類別，請識別使用它的 <xref:System.Data.Linq.DataContext> 方法，並將這些方法的傳回型別設定為不同的實體類別。

若要將 <xref:System.Data.Linq.DataContext> 方法的傳回型別還原成它們原來自動產生的類型，請先從 [方法] 窗格中刪除 <xref:System.Data.Linq.DataContext> 方法，然後再次將物件從**伺服器總管**/**資料庫總管** 拖曳至 **O/R 設計工具**。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 選取 [方法] 窗格中的 <xref:System.Data.Linq.DataContext> 方法，然後檢查 [屬性] 視窗中的 [傳回型別] 屬性，以識別將實體類別用作傳回型別的 <xref:System.Data.Linq.DataContext> 方法。

2. 將**傳回型別**設定為不同的實體類別，或從方法窗格中刪除 <xref:System.Data.Linq.DataContext> 方法。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)