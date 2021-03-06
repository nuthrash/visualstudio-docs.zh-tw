---
title: 'span:: span 建構函式 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f761e87c1658c11bfdfd93a4f4e22299d88575a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979818"
---
# <a name="spanspan-constructor"></a>span::span 建構函式

初始化 `span` 類別的新執行個體。

## <a name="syntax"></a>語法

```cpp
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>參數

`_Series` 有效的標記系列內容。

`_Format` 複合格式字串，其中包含混合零或多個格式項目的文字，並與引數清單中的物件相對應。

`_Importance` 重要性層級。

`_Category` 分類。

## <a name="requirements"></a>需求

**標頭：** *cvmarkersobj.h*

**命名空間：** Concurrency::diagnostic

## <a name="see-also"></a>另請參閱

- [span 類別](../profiling/span-class.md)