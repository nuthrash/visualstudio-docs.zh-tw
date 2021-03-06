---
title: 教學課程 3：建立配對遊戲
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 151b9be68b82f2b9fdcb20cd105890914333a2b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821518"
---
# <a name="tutorial-3-create-a-matching-game"></a>教學課程 3：建立配對遊戲

在本教學課程中，您會建置一個配對遊戲，而遊戲玩家必須配對隱藏的圖示。 您將學習如何：

- 在 <xref:System.Collections.Generic.List%601> 物件中儲存物件 (例如圖示)。

- 使用 `foreach` 迴圈 (Visual C#) 或 `For Each` 迴圈 (Visual Basic) 逐一查看清單中的項目。

- 使用參考變數追蹤表單的狀態。

- 建置您可以搭配多個物件使用的事件處理常式來回應事件。

- 讓計時器倒數計時，然後讓計時器於啟動後剛好引發一個事件。

當您完成此教學課程時，您的程式看起來類似下圖所示：

![您在本教學課程中建立的遊戲](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>教學課程的連結

若要下載這個範例的完整版，請參閱[完整的配對遊戲教學課程範例](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) \(英文\)。

> [!NOTE]
> 在本教學課程中，Visual C# 和 Visual Basic 都會涵蓋在內，所以請將焦點放在您正在使用的程式語言專屬資訊。

如果您碰到程式開發的問題，請嘗試發表問題至 MSDN 論壇。 請參閱 [Visual Basic 論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral)和 [Visual C# 論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral)。 此外，其中提供了很好的免費視訊學習資源。 若要深入了解 Visual Basic 中的程式設計，請參閱 [Visual Basic fundamentals:Development for absolute beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Visual Basic 基本概念：適合完全初學者的開發)。 若要深入了解 Visual C# 中的程式設計，請參閱 [C# fundamentals:Development for absolute beginners](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (Visual Basic 基本概念：適合完全初學者的開發)。

## <a name="related-topics"></a>相關主題

|標題|說明|
|-----------|-----------------|
|[步驟 1：建立專案並將資料表新增至表單](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|從建立專案並新增 `TableLayoutPanel` 控制項，讓控制項正確對齊開始。|
|[步驟 2：新增隨機物件和圖示清單](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|加入 `Random` 物件和 `List` 物件，以建立圖示清單。|
|[步驟 3：將隨機圖示指派給每個標籤](../ide/step-3-assign-a-random-icon-to-each-label.md)|將圖示隨機指派給 `Label` 控制項；因此，每個遊戲是不同的。|
|[步驟 4：將 Click 事件處理常式新增至每個標籤](../ide/step-4-add-a-click-event-handler-to-each-label.md)|加入 `Click` 事件處理常式，以變更已按下標籤的色彩。|
|[步驟 5：新增標籤參考](../ide/step-5-add-label-references.md)|加入參考變數，以追蹤已按一下的標籤。|
|[步驟 6：新增計時器](../ide/step-6-add-a-timer.md)|將計時器加入至表單，追蹤遊戲已經過的時間。|
|[步驟 7：讓配對保持可見](../ide/step-7-keep-pairs-visible.md)|如果已選取相符的配對，請讓圖示配對維持可見狀態。|
|[步驟 8：新增驗證玩家是否勝利的方法](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|加入 `CheckForWinner()` 方法以驗證玩家是否贏了。|
|[步驟 9：嘗試其他功能](../ide/step-9-try-other-features.md)|嘗試其他功能，例如變更圖示和色彩、加上格線，以及加入音效。 試著讓戲局變大並調整計時器。|
