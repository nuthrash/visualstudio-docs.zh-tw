---
title: 具類型資料集與不具類型資料集的比較
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d6a16b8f0752ca2ab063f8bbbaa966836856eb4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565804"
---
# <a name="typed-vs-untyped-datasets"></a>具類型資料集與不具類型資料集的比較
具類型資料集是第一次衍生自基底的資料集<xref:System.Data.DataSet>類別，然後使用 從資訊**Dataset 設計工具**，均會儲存在一個.xsd 檔案，以產生新的強類型 dataset 類別。 從結構描述 （資料表、 資料行等等） 的資訊會產生，並編譯成這個新的資料集類別中，為一組的第一級物件和屬性。 因為具類型資料集繼承自基底<xref:System.Data.DataSet>類別，型別的類別假設所有的功能<xref:System.Data.DataSet>類別，並可接受的執行個體的方法與<xref:System.Data.DataSet>類別做為參數。

 不具類型的資料集，相較之下，有沒有相對應的內建結構描述。 具類型的資料集，與不具類型的資料集包含資料表、 資料行，等等，但這些都顯露只做為集合。 (不過，您手動建立的資料表和其他資料元素中的不具類型的資料集之後，您可以匯出資料集的結構為結構描述使用的資料集<xref:System.Data.DataSet.WriteXmlSchema%2A>方法。)

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>具型別和不具類型資料集的對比資料存取
 具類型資料集的類別具有其屬性對資料表和資料行的實際名稱所在的物件模型。 例如，如果您正在使用具類型資料集，您可以使用如下所示的程式碼參考的資料行：

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 相反地，如果您正在使用不具類型的資料集，是對等的程式碼：

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 具類型的存取不只更方便閱讀，但也完全支援 Visual Studio 中的 IntelliSense**程式碼編輯器**。 除了容易使用，具類型資料集的語法會提供類型檢查在編譯時期，大幅減少在指派值給資料集成員的錯誤的可能性。 如果您變更中的資料行名稱您<xref:System.Data.DataSet>類別，然後編譯您的應用程式中，您會收到建置錯誤。 按兩下的建置錯誤**工作清單**，您可以直接移至該程式行或參考舊的資料行名稱的行程式碼。 存取資料表和資料行中具類型資料集還有稍微快一些在執行階段，因為存取由決定在編譯時期，不是透過在執行階段的集合。

 雖然仍具類型資料集有許多優點，不具類型的資料集是以各種不同的情況下很有用。 最明顯的案例時，會提供資料集沒有結構描述。 這可能是，比方說，如果您的應用程式互動的元件，會傳回資料集，但您無法在預先知道其結構的功能。 同樣地，有時候是當您正在使用沒有靜態、 可預測的結構的資料。 在此情況下，它不適合使用具類型的資料集，因為您必須重新產生每個變更資料結構中的具類型資料集類別。

 一般來說，有許多次時您可能會以動態方式建立資料集，而不需要提供的結構描述。 在此情況下，資料集都是只是一個便利的結構，您可以在其中保留的詳細資訊，只要資料可以表示關聯式方法。 在此同時，您可以利用資料集的功能，例如要序列化的資訊傳遞至另一個處理序，或以寫出 XML 檔案的能力。

## <a name="see-also"></a>另請參閱

- [資料集工具](../data-tools/dataset-tools-in-visual-studio.md)