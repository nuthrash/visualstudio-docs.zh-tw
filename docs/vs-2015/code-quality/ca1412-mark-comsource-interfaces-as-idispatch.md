---
title: CA1412:ComSource 介面標記為 IDispatch |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 59fec1fddb16296f1238deb5c2f9bbf0c350cdd2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944865"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412:ComSource 介面必須標記為 IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型會標示<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>屬性和至少一個指定的介面不以標示<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>屬性設為`InterfaceIsDispatch`值。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 用來識別類別會公開元件物件模型 (COM) 用戶端的事件介面。 這些介面必須公開為`InterfaceIsIDispatch`讓 Visual Basic 6 COM 用戶端接收事件通知。 根據預設，如果介面不以標示<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>屬性，它會公開為雙重介面。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入或修改<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>屬性，讓其值設定為所指定的所有介面 InterfaceIsIDispatch<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範類別其中一個介面違反規則的位置。

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1408:不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>另請參閱
 [如何：引發由 COM 接收所處理的事件](http://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)[與相互操作 Unmanaged 程式碼](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
