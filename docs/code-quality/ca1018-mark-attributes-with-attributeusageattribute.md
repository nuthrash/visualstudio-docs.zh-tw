---
title: CA1018:必須以 AttributeUsageAttribute 標記屬性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4c0aa3fe5c45e34445c49c4b3a5f0abad1e98739
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779333"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018:必須以 AttributeUsageAttribute 標記屬性

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 <xref:System.AttributeUsageAttribute?displayProperty=fullName>屬性不存在於上的自訂屬性。

## <a name="rule-description"></a>規則描述
 當您定義自訂屬性時，它使用標記<xref:System.AttributeUsageAttribute>表示原始程式碼中可以套用自訂屬性的位置。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。 例如，您可以定義屬性，可識別的人，誰負責維護和加強每種類型的程式庫，然後在類型層級一律指派責任。 在此情況下，編譯器應該啟用類別、 列舉和介面上的屬性，但應該在方法、 事件或屬性上啟用。 組織的原則和程序，會決定屬性是否應該啟用組件。

 <xref:System.AttributeTargets?displayProperty=fullName>列舉會定義您可以指定自訂屬性的目標。 如果您省略<xref:System.AttributeUsageAttribute>，您的自訂屬性將會是適用於所有目標，所定義`All`的值<xref:System.AttributeTargets>列舉型別。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請指定目標屬性使用<xref:System.AttributeUsageAttribute>。 請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您應該修正而非訊息但不包括此規則的違規情形。 即使屬性繼承<xref:System.AttributeUsageAttribute>，此屬性應該會出現以簡化程式碼維護。

## <a name="example"></a>範例
 下列範例會定義兩個屬性。 `BadCodeMaintainerAttribute` 不正確地省略<xref:System.AttributeUsageAttribute>陳述式，和`GoodCodeMaintainerAttribute`會正確地實作本節稍早說明的屬性。 請注意，屬性`DeveloperName`所設計規則[ca1019 必須：定義存取子屬性引數](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)，並包含為求完整性。

 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1019： 必須定義存取子屬性引數](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813:避免使用非密封的屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>另請參閱

- [屬性](/dotnet/standard/design-guidelines/attributes)