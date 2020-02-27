---
title: 繼承 - C# 程式設計指南
ms.date: 02/07/2020
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 448b1695a4afc50f4afa20383e5fda280b9f12e9
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626655"
---
# <a name="inheritance-c-programming-guide"></a>繼承 (C# 程式設計手冊)

繼承是物件導向程式設計的三個主要特性之一，另外兩個是封裝和多型。 繼承可讓您建立新的類別，以重複使用、擴充和修改其他類別中定義的行為。 成員被繼承的類別稱為「基底類別」，而繼承這種成員的類別即稱為「衍生類別」。 衍生類別只能有一個基底類別。 不過，繼承是可轉移的。 如果 `ClassC` 衍生自 `ClassB`，而 `ClassB` 衍生自 `ClassA`，`ClassC` 會繼承 `ClassB` 和 `ClassA`中宣告的成員。

> [!NOTE]
> 結構不支援繼承，但可以實作介面。 如需詳細資訊，請參閱 [介面](../interfaces/index.md)中定義的介面的私用 C++ 專屬實作。

就概念而言，衍生類別是基底類別的特製化項目。 例如，如果您有一個基底類別 `Animal`，您可能會有一個名為 `Mammal` 的衍生類別，以及另一個名為 `Reptile` 的衍生類別。 `Mammal` 是 `Animal`，`Reptile` 也是 `Animal`，但這兩個衍生類別各代表不同的基底類別特製化項目。

介面宣告可能會定義其成員的預設實值。 衍生介面和實作為這些介面的類別會繼承這些執行。 如需預設介面方法的詳細資訊，請參閱語言參考一節中有關[介面](../../language-reference/keywords/interface.md)的文章。

當您將某個類別定義為要從另一個類別衍生時，衍生類別會隱含取得基底類別的所有成員，但建構函式和完成項則除外。 衍生類別會重複使用基類中的程式碼，而不需要重新加以產生。 您可以在衍生類別中新增更多成員。 衍生類別會擴充基類的功能。

下圖顯示 `WorkItem` 類別，代表某些商務程序中的工作項目。 它和所有類別一樣，會衍生自 <xref:System.Object?displayProperty=nameWithType> 並繼承其所有方法。 `WorkItem` 會新增自己的五個成員。 這些成員包括一個函式，因為不會繼承函式。 `ChangeRequest` 類別繼承自 `WorkItem`，並代表特定類型的工作項目。 `ChangeRequest` 會在繼承自 `WorkItem` 和 <xref:System.Object> 的成員中，另外新增兩個成員。 它必須新增自己的建構函式，也會新增 `originalItemID`。 `originalItemID` 屬性可讓 `ChangeRequest` 執行個體與套用變更要求的原始 `WorkItem` 產生關聯。

![顯示類別繼承的圖表](./media/inheritance/class-inheritance-diagram.png)

下列範例示範如何以 C# 表示上圖所示範的類別關聯性。 此範例也會示範 `WorkItem` 如何覆寫 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 虛擬方法，以及 `ChangeRequest` 類別如何繼承方法的 `WorkItem` 實作。 第一個區塊會定義類別：

[!code-csharp[DefineClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#Classes)]

下一個區塊顯示如何使用基底和衍生類別：

[!code-csharp[UseClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#UseClasses)]

## <a name="abstract-and-virtual-methods"></a>抽象和虛擬方法

當基類將方法宣告為[`virtual`](../../language-reference/keywords/virtual.md)時，衍生類別可以使用其本身的執行[`override`](../../language-reference/keywords/override.md)方法。 如果基類將成員宣告為[`abstract`](../../language-reference/keywords/abstract.md)，則在直接繼承自該類別的任何非抽象類別中，都必須覆寫該方法。 如果衍生類別本身就是抽象的，則會繼承抽象成員而不需要進行實作。 抽象和虛擬成員是多型的基礎，而多型是物件導向程式設計的第二個主要特性。 如需詳細資訊，請參閱[多型](./polymorphism.md)。

## <a name="abstract-base-classes"></a>抽象基類

如果您想要防止使用 [new](../../language-reference/keywords/abstract.md) 運算子來直接具現化，您可以將類別宣告為[抽象](../../language-reference/operators/new-operator.md)。 只有在新的類別衍生自它時，才可以使用抽象類別。 抽象類別可以包含一或多個本身宣告為抽象的方法簽章。 這些簽章可指定參數和傳回值，但沒有實作 (方法主體)。 抽象類別不一定要包含抽象成員;不過，如果類別確實包含抽象成員，則類別本身必須宣告為抽象。 不是抽象本身的衍生類別必須提供抽象基類中任何抽象方法的執行。 如需詳細資訊，請參閱[抽象和密封類別以及類別成員](abstract-and-sealed-classes-and-class-members.md)。

## <a name="interfaces"></a>介面

「*介面*」（interface）是定義一組成員的參考型別。 所有實作為該介面的類別和結構都必須實作為該成員集合。 介面可能會定義任何或所有成員的預設實值。 一個類別可以實作多個介面，但只能衍生自單一直接基底類別。

介面是用來定義不一定有「是」關聯性之類別的特定功能。 例如，<xref:System.IEquatable%601?displayProperty=nameWithType> 介面可以由任何類別或結構來執行，以判斷類型的兩個物件是否相等（不過，類型會定義相等）。 <xref:System.IEquatable%601> 不表示基類與衍生類別之間存在相同種類的「is a」關聯性（例如，`Mammal` 是 `Animal`）。 如需詳細資訊，請參閱 [介面](../interfaces/index.md)中定義的介面的私用 C++ 專屬實作。

## <a name="preventing-further-derivation"></a>防止進一步的衍生  

類別可以藉由將本身或成員宣告為[`sealed`](../../language-reference/keywords/sealed.md)，防止其他類別繼承自它或其成員。 如需詳細資訊，請參閱[抽象和密封類別以及類別成員](./abstract-and-sealed-classes-and-class-members.md)。

## <a name="derived-class-hiding-of-base-class-members"></a>基類成員的衍生類別隱藏  

衍生類別可藉由以相同的名稱和簽章宣告基底類別成員，來隱藏這些成員。 [`new`](../../language-reference/keywords/new-modifier.md)修飾詞可以用來明確指出該成員不是基底成員的覆寫。 不需要使用[`new`](../../language-reference/keywords/new-modifier.md) ，但如果未使用[`new`](../../language-reference/keywords/new-modifier.md) ，將會產生編譯器警告。 如需詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](./versioning-with-the-override-and-new-keywords.md)和[了解使用 Override 和 New 關鍵字的時機](./knowing-when-to-use-override-and-new-keywords.md)。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](./index.md)
- [class](../../language-reference/keywords/class.md)
