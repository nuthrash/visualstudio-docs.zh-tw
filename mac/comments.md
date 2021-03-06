---
title: 註解化程式碼
description: 本文描述如何使用 Visual Studio for Mac 原始檔編輯器中的註解
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 1f792e5ba670854e4a3a9ce703212d18c16e5512
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62984027"
---
# <a name="comments"></a>註解

對程式碼進行偵錯或實驗時，暫時或長期註解程式碼區塊可能很有用。

若要將整個程式碼區塊標記為註解：

* 選取程式碼，然後從操作功能表選取 [切換行註解]

OR

* 在選取的程式碼上使用 `cmd + /` 按鍵繫結關係。

這些方法可用來註解和取消註解程式碼區段。 在 C# 檔案中，可以新增其他行註解層級，這可讓您註解和取消註解程式碼區域，同時仍保留實際註解：

![多層級註解](media/source-editor-image8.png)

對於未來可能會與程式碼進行互動的開發人員，註解也可用來記錄程式碼。 這些通常是以多行註解的形式進行，而多行註解則使用下列方式新增在每個語言中：

**C#**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>另請參閱

- [將程式碼標記為註解 (Windows 上的 Visual Studio)](/visualstudio/ide/quickstart-editor#comment-out-code)