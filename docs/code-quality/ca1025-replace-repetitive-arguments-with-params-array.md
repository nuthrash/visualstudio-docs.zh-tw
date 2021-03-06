---
title: CA1025:以參數陣列取代重複的引數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4a292cb3f3221b36c163c87881fd23db0606399
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779415"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025:以參數陣列取代重複的引數

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 公用類型中的公用或受保護的方法有三個以上的參數和其最後三個參數都是相同類型。

## <a name="rule-description"></a>規則描述
 當引數確切數目未知，而且變數引數都是相同的類型，或可以傳遞做為相同的類型時，請使用參數陣列而不是重複的引數。 例如，<xref:System.Console.WriteLine%2A>方法會提供一般用途的多載接受任意數目的使用參數陣列<xref:System.Object>引數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請以參數陣列取代重複的引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它一律可安全地隱藏這項規則; 一個警告不過，這種設計可能會導致可用性問題。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別。

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]