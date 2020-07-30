---
title: 介面 - C# 程式設計手冊
description: 'C # 中的介面包含非抽象類別或結構必須執行的一組相關功能的定義。'
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 4485a9f8e3581aa80ed65221258dc40310b3a695
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303045"
---
# <a name="interfaces-c-programming-guide"></a>介面 (C# 程式設計手冊)

「介面」（interface）包含非抽象[類](../../language-reference/keywords/class.md)或[結構](../../language-reference/builtin-types/struct.md)必須執行之相關功能群組的定義。 介面可能會定義 `static` 方法，其必須有實作為。 從 c # 8.0 開始，介面可能會定義成員的預設實值。 介面可能不會宣告實例資料，例如欄位、自動實作為屬性或類似屬性的事件。

例如，您可以藉由使用介面，在類別中包含多個來源的行為。 這項功能在 C# 中是很重要的，因為語言不支援類別的多重繼承。 此外，如果您要模擬結構繼承，則必須使用介面，因為它們實際上無法繼承自另一個結構或類別。

您可以使用[interface](../../language-reference/keywords/interface.md)關鍵字來定義介面，如下列範例所示。

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

介面的名稱必須是有效的 c #[識別碼名稱](../inside-a-program/identifier-names.md)。 依慣例，介面名稱的開頭是大寫的|capital `I`。

任何實作 <xref:System.IEquatable%601> 介面的類別或結構，必須包含 <xref:System.IEquatable%601.Equals%2A> 方法的定義，該方法符合介面指定的簽章。 如此一來，您可以倚賴實作 `IEquatable<T>` 的類別，以包含 `Equals` 方法，類別的執行個體可以使用該方法判斷它是否等於相同類別的另一個執行個體。

的定義 `IEquatable<T>` 不會提供的實作為 `Equals` 。 類別或結構可以執行多個介面，但類別只能繼承自單一類別。

如需抽象類別的詳細資訊，請參閱[抽象和密封類別以及類別成員](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。

介面可以包含實例方法、屬性、事件、索引子，或這四個成員類型的任何組合。 介面可以包含靜態的函式、欄位、常數或運算子。 如需範例的連結，請參閱[相關章節](./index.md#BKMK_RelatedSections)。 介面不能包含實例欄位、實例函數或完成項。 介面成員預設是公用的。

若要實作介面成員，實作類別的對應成員必須是公用、非靜態，且具有與介面成員相同的名稱和簽章。

當類別或結構實作為介面時，類別或結構必須為介面宣告但未提供預設實作為的所有成員提供執行。 不過，如果基底類別實作介面，則衍生自基底類別的任何類別都會繼承該實作。

下列範例會示範 <xref:System.IEquatable%601> 介面的實作。 實作類別 `Car` 必須提供 <xref:System.IEquatable%601.Equals%2A> 方法的實作。

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

類別的屬性與索引子可以針對介面中定義的屬性或索引子定義額外的存取子。 例如，介面可能會宣告具有 [get](../../language-reference/keywords/get.md) 存取子的屬性。 實作介面的類別可以宣告具有 `get` 和 [set](../../language-reference/keywords/set.md) 存取子的相同屬性。 不過，如果屬性或索引子使用明確的實作，則存取子必須相符。 如需明確實作的詳細資訊，請參閱[明確介面實作](explicit-interface-implementation.md)和[介面屬性](../classes-and-structs/interface-properties.md)。

介面可以繼承自一或多個介面。 衍生的介面會繼承其基底介面中的成員。 實衍生介面的類別必須實作為衍生介面中的所有成員，包括衍生介面之基底介面的所有成員。 該類別可以隱含地轉換成衍生介面或其任何基底介面。 類別可能透過基底類別包含介面多次，繼承或透過其他介面繼承的介面。 不過，類別只能提供介面實作一次，而且只有在類別將介面宣告為類別 (`class ClassName : InterfaceName`) 定義的一部分時。 如果因為您繼承實作介面的基底類別而繼承介面，則基底類別會提供介面成員的實作。 不過，衍生的類別可以實作任何虛擬介面成員，而不使用繼承的實作。 當介面宣告方法的預設執行時，任何執行該介面的類別都會繼承該執行。 介面中定義的實作為虛擬，而執行中的類別可能會覆寫該執行。

基底類別也可以使用虛擬成員來實作介面成員。 在此情況下，衍生的類別可以藉由覆寫虛擬成員來變更介面行為。 如需虛擬成員的詳細資訊，請參閱[多型](../classes-and-structs/polymorphism.md)。

## <a name="interfaces-summary"></a>介面摘要

介面具有下列屬性：

- 介面通常類似于只有抽象成員的抽象基類。 任何實作介面的類別或結構必須實作它的所有成員。 （選擇性）介面可以定義其部分或所有成員的預設實值。 如需詳細資訊，請參閱[預設介面方法](../../tutorials/default-interface-methods-versions.md)。
- 介面無法直接具現化。 其成員是由實作介面的任何類別或結構實作。
- 類別或結構可以實作多個介面。 類別可以繼承基底類別，也會實作一或多個介面。

## <a name="related-sections"></a><a name="BKMK_RelatedSections"></a>相關章節

- [介面屬性](../classes-and-structs/interface-properties.md)  
- [介面中的索引子](../indexers/indexers-in-interfaces.md)  
- [如何實作介面事件](../events/how-to-implement-interface-events.md)
- [類別和結構](../classes-and-structs/index.md)  
- [繼承](../classes-and-structs/inheritance.md)  
- [介面](../../language-reference/keywords/interface.md)
- [方法](../classes-and-structs/methods.md)  
- [Polymorphism](../classes-and-structs/polymorphism.md)  
- [抽象和密封類別以及類別成員](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [屬性](../classes-and-structs/properties.md)  
- [事件](../events/index.md)  
- [索引子](../indexers/index.md)
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [繼承](../classes-and-structs/inheritance.md)
- [識別碼名稱](../inside-a-program/identifier-names.md)
