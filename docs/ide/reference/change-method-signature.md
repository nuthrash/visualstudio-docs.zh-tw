---
title: 重構方法簽章
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 89af8235f897858094058981df52d6a3fec8a7d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62791113"
---
# <a name="change-a-method-signature-refactoring"></a>變更方法特徵標記重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您移除或變更方法參數的順序。

**時機：** 您想要移動或移除目前在各種位置中使用的方法參數。

**原因：** 您可以手動移除參數或重新排列其順序，然後尋找對該方法的所有呼叫並逐一變更這些呼叫，但這樣可能會造成錯誤。  這個重構工具將可自動執行此工作。

## <a name="how-to"></a>操作說明

1. 醒目標示要修改的方法名稱或它的其中一個使用方式，或將文字游標放在要修改的方法名稱或它的其中一個使用方式內：

   - C#: 

       ![醒目提示的程式碼 C#](media/changesignature-highlight-cs.png)

   - VB：

       ![醒目提示的程式碼 - Visual Basic](media/changesignature-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按 **CTRL+R**，再按 **CTRL+V**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [變更簽章]。
   - **滑鼠**
      - 選取 [編輯] > [重構] > [移除參數]。
      - 選取 [編輯] > [重構] > [重新排列參數]。
      - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [變更簽章]。

3. 在 [變更簽章] 快顯對話方塊中，您可以使用右邊的按鈕來變更方法簽章：

   ![[變更簽章] 對話方塊](media/changesignature-dialog-cs.png)

   | 按鈕 | 說明
   | ------ | ---
   | **向上/向下** | 將選取的參數在清單中向上和向下移動
   | **移除** | 將選取的參數從清單中移除
   | **還原** | 將所選的已刪除參數還原到清單中

   > [!TIP]
   > 請使用 [預覽參考變更] 核取方塊，以在認可變更之前先[查看將會有的結果](../../ide/preview-changes.md)。

4. 完成時，按 [確定] 按鈕以進行變更。

   - C#: 

      ![變更特徵標記結果 - C#](media/changesignature-result-cs.png)

   - Visual Basic：

      ![變更特徵標記結果 - Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)