---
title: CA2230:使用 params 做為變數引數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e2ab764b9a9f30c9e8143267cbdf14ecbb9456e8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943417"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230:必須使用 params 作為變數引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|分類|Microsoft.Usage|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含公用或受保護的方法使用`VarArgs`呼叫慣例。

## <a name="rule-description"></a>規則描述
 `VarArgs`呼叫慣例用於接受各種數目參數的特定方法定義。 方法使用`VarArgs`呼叫慣例不是 Common Language Specification (CLS) 相容，而且可能無法存取跨程式語言。

 在 C# 中，`VarArgs`方法的參數清單的結尾時，呼叫慣例會使用`__arglist`關鍵字。 Visual Basic 不支援`VarArgs`呼叫慣例和 Visual c + + 允許其使用僅在使用橢圓形的 unmanaged 程式碼`...`標記法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，C# 中，使用[params](http://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012)而不是關鍵字`__arglist`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會示範兩種方法，其中一個違反規則，會滿足規則的其中一個。

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [語言獨立性以及與語言無關的元件](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
