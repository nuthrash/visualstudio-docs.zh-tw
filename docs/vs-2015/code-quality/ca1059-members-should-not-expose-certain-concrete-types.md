---
title: CA1059:成員不應該公開特定的具象類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a78125645dc6369811b4b9e1d7101b7bb4cbba76
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103819"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059:成員不應該公開特定的具象類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見成員是特定的具象類型，或公開特定的具象類型，透過其中一個參數或傳回值。 目前，此規則會回報下列的具象類型的曝光度：

- 型別衍生自<xref:System.Xml.XmlNode?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 具象類型就是具有完整實作 (Implementation) 且因此能加以具現化 (Instantiated) 的類型。 若要允許廣泛使用的成員，用為建議的介面來取代具象型別。 這可讓成員接受任何實作介面的型別，或是使用實作介面的型別所預期的位置。

 下表列出的目標的具象類型和其建議的替代項目。

|具象類型|Replacement|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> 使用介面，以減少從 XML 資料來源的特定實作的成員。|

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將建議的介面中的具象型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它會安全地隱藏此規則的訊息，如果需要特定的具象類型所提供的功能。

## <a name="related-rules"></a>相關的規則
 [CA1011:請考慮將基底類型當做參數傳遞](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
