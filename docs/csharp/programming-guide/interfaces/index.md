---
title: 介面 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 30c44b9f98bcc61d54b8103b6b40d14fd35715f4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589187"
---
# <a name="interfaces-c-programming-guide"></a>介面 (C# 程式設計手冊)

介面包含[類別](../../language-reference/keywords/class.md)或 [struct](../../language-reference/keywords/struct.md) 可實作的一組相關功能定義。
  
例如，您可以藉由使用介面，在類別中包含多個來源的行為。 這項功能在 C# 中是很重要的，因為語言不支援類別的多重繼承。 此外，如果您要模擬結構繼承，則必須使用介面，因為它們實際上無法繼承自另一個結構或類別。  
  
您會使用 [interface](../../language-reference/keywords/interface.md) 關鍵字來定義介面， 如下列範例所示。  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

結構的名稱必須是有效的 C# [識別碼名稱](../inside-a-program/identifier-names.md)。 依慣例，介面名稱的開頭是大寫的|capital `I`。

任何實作 <xref:System.IEquatable%601> 介面的類別或結構，必須包含 <xref:System.IEquatable%601.Equals%2A> 方法的定義，該方法符合介面指定的簽章。 如此一來，您可以倚賴實作 `IEquatable<T>` 的類別，以包含 `Equals` 方法，類別的執行個體可以使用該方法判斷它是否等於相同類別的另一個執行個體。  
  
`IEquatable<T>` 的定義不提供 `Equals` 的實作。 介面只會定義簽章。 如此一來，在 C# 中的介面類似於抽象類別，其中的所有方法都是抽象的。 不過，類別或結構可以實作多個介面，但類別只會繼承單一類別抽象或不繼承。
  
如需抽象類別的詳細資訊，請參閱[抽象和密封類別以及類別成員](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
介面可以包含方法、屬性、事件、索引子，或以上四個成員類型的組合。 如需範例的連結，請參閱[相關章節](./index.md#BKMK_RelatedSections)。 介面不能包含常數、欄位、運算子、執行個體建構函式、完成項或類型。 介面成員會自動變成公用，且它們不能包含任何存取修飾詞。 成員也不能是 [static](../../language-reference/keywords/static.md)。  
  
若要實作介面成員，實作類別的對應成員必須是公用、非靜態，且具有與介面成員相同的名稱和簽章。  
  
當類別或結構實作介面時，類別或結構必須提供介面定義之所有成員的實作。 介面本身不提供功能讓類別或結構可以如同繼承基底類別功能一般繼承。 不過，如果基底類別實作介面，則衍生自基底類別的任何類別都會繼承該實作。  
  
下列範例會示範 <xref:System.IEquatable%601> 介面的實作。 實作類別 `Car` 必須提供 <xref:System.IEquatable%601.Equals%2A> 方法的實作。  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
類別的屬性與索引子可以針對介面中定義的屬性或索引子定義額外的存取子。 例如，介面可能會宣告具有 [get](../../language-reference/keywords/get.md) 存取子的屬性。 實作介面的類別可以宣告具有 `get` 和 [set](../../language-reference/keywords/set.md) 存取子的相同屬性。 不過，如果屬性或索引子使用明確的實作，則存取子必須相符。 如需明確實作的詳細資訊，請參閱[明確介面實作](explicit-interface-implementation.md)和[介面屬性](../classes-and-structs/interface-properties.md)。  

介面可以繼承自其他介面。 類別可能透過基底類別包含介面多次，繼承或透過其他介面繼承的介面。 不過，類別只能提供介面實作一次，而且只有在類別將介面宣告為類別 (`class ClassName : InterfaceName`) 定義的一部分時。 如果因為您繼承實作介面的基底類別而繼承介面，則基底類別會提供介面成員的實作。 不過，衍生的類別可以實作任何虛擬介面成員，而不使用繼承的實作。  
  
基底類別也可以使用虛擬成員來實作介面成員。 在此情況下，衍生的類別可以藉由覆寫虛擬成員來變更介面行為。 如需虛擬成員的詳細資訊，請參閱[多型](../classes-and-structs/polymorphism.md)。  
  
## <a name="interfaces-summary"></a>介面摘要

介面具有下列屬性：  

- 介面類似只有抽象成員的抽象基底類別。 任何實作介面的類別或結構必須實作它的所有成員。
- 介面無法直接具現化。 其成員是由實作介面的任何類別或結構實作。
- 介面可以包含事件、索引子、方法和屬性。
- 介面不包含方法的實作。
- 類別或結構可以實作多個介面。 類別可以繼承基底類別，也會實作一或多個介面。

## <a name="in-this-section"></a>本節內容

[明確介面實作](explicit-interface-implementation.md)  
 說明如何建立介面特定的類別成員。  
  
 [如何：明確實作介面成員](how-to-explicitly-implement-interface-members.md)  
 提供如何明確實作介面成員的範例。  
  
 [如何：明確實作兩個介面的成員](how-to-explicitly-implement-members-of-two-interfaces.md)  
 提供如何透過繼承明確實作介面成員的範例。  
  
## <a name="BKMK_RelatedSections"></a> 相關章節

- [介面屬性](../classes-and-structs/interface-properties.md)  
- [介面中的索引子](../indexers/indexers-in-interfaces.md)  
- [如何：實作介面事件](../events/how-to-implement-interface-events.md)  
- [類別和結構](../classes-and-structs/index.md)  
- [繼承](../classes-and-structs/inheritance.md)  
- [方法](../classes-and-structs/methods.md)  
- [多型](../classes-and-structs/polymorphism.md)  
- [抽象和密封類別以及類別成員](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [屬性](../classes-and-structs/properties.md)  
- [事件](../events/index.md)  
- [索引子](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>精選書籍章節

[了解 C# 3.0：掌握 C# 3.0 的基本概念](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)中的[介面](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29)

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [繼承](../classes-and-structs/inheritance.md)
- [識別碼名稱](../inside-a-program/identifier-names.md)
