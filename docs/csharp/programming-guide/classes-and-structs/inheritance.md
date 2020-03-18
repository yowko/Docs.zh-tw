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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626655"
---
# <a name="inheritance-c-programming-guide"></a>繼承 (C# 程式設計手冊)

繼承是物件導向程式設計的三個主要特性之一，另外兩個是封裝和多型。 繼承使您能夠創建新類，以重用、擴展和修改在其他類中定義的行為。 成員被繼承的類別稱為「基底類別」**，而繼承這種成員的類別即稱為「衍生類別」**。 衍生類別只能有一個基底類別。 不過，繼承是可轉移的。 如果`ClassC`派生`ClassB`自 ，`ClassB`派生自`ClassA`，`ClassC`繼承 中`ClassB`聲明的成員`ClassA`和 。

> [!NOTE]
> 結構不支援繼承，但可以實作介面。 如需詳細資訊，請參閱[介面](../interfaces/index.md)。

就概念而言，衍生類別是基底類別的特製化項目。 例如，如果您有一個基底類別 `Animal`，您可能會有一個名為 `Mammal` 的衍生類別，以及另一個名為 `Reptile` 的衍生類別。 `Mammal` 是 `Animal`，`Reptile` 也是 `Animal`，但這兩個衍生類別各代表不同的基底類別特製化項目。

介面聲明可以為其成員定義預設實現。 這些實現由派生介面和實現這些介面的類繼承。 有關預設介面方法的詳細資訊，請參閱語言參考部分中有關[介面](../../language-reference/keywords/interface.md)的文章。

當您將某個類別定義為要從另一個類別衍生時，衍生類別會隱含取得基底類別的所有成員，但建構函式和完成項則除外。 派生類重用基類中的代碼，而無需重新實現它。 您可以在派生類中添加更多成員。 派生類擴展基類的功能。

下圖顯示 `WorkItem` 類別，代表某些商務程序中的工作項目。 它和所有類別一樣，會衍生自 <xref:System.Object?displayProperty=nameWithType> 並繼承其所有方法。 `WorkItem` 會新增自己的五個成員。 這些成員包括一個建構函式，因為建構函式不是繼承的。 `ChangeRequest` 類別繼承自 `WorkItem`，並代表特定類型的工作項目。 `ChangeRequest` 會在繼承自 `WorkItem` 和 <xref:System.Object> 的成員中，另外新增兩個成員。 它必須新增自己的建構函式，也會新增 `originalItemID`。 `originalItemID` 屬性可讓 `ChangeRequest` 執行個體與套用變更要求的原始 `WorkItem` 產生關聯。

![顯示類別繼承的圖表](./media/inheritance/class-inheritance-diagram.png)

下列範例示範如何以 C# 表示上圖所示範的類別關聯性。 此範例也會示範 `WorkItem` 如何覆寫 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 虛擬方法，以及 `ChangeRequest` 類別如何繼承方法的 `WorkItem` 實作。 第一個塊定義類：

[!code-csharp[DefineClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#Classes)]

下一個塊演示如何使用基類和派生類：

[!code-csharp[UseClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#UseClasses)]

## <a name="abstract-and-virtual-methods"></a>抽象和虛擬方法

當基類將方法聲明為[`virtual`](../../language-reference/keywords/virtual.md)，派生類可以[`override`](../../language-reference/keywords/override.md)具有其自己的實現的方法。 如果基類聲明成員為[`abstract`](../../language-reference/keywords/abstract.md)，則必須在直接從該類繼承的任何非抽象類別中重寫該方法。 如果衍生類別本身就是抽象的，則會繼承抽象成員而不需要進行實作。 抽象和虛擬成員是多型的基礎，而多型是物件導向程式設計的第二個主要特性。 如需詳細資訊，請參閱[多型](./polymorphism.md)。

## <a name="abstract-base-classes"></a>抽象基類

如果您想要防止使用 [new](../../language-reference/operators/new-operator.md) 運算子來直接具現化，您可以將類別宣告為[抽象](../../language-reference/keywords/abstract.md)。 僅當從抽象類別派生出抽象類別時，才能使用抽象類別。 抽象類別可以包含一或多個本身宣告為抽象的方法簽章。 這些簽章可指定參數和傳回值，但沒有實作 (方法主體)。 抽象類別不必包含抽象成員;因此，抽象類別不必包含抽象成員。但是，如果類確實包含抽象成員，則類本身必須聲明為抽象。 不抽象本身的派生類必須為抽象基類中的任何抽象方法提供實現。 有關詳細資訊，請參閱[抽象類別和密封類和類成員](abstract-and-sealed-classes-and-class-members.md)。

## <a name="interfaces"></a>介面

*介面*是定義一組成員的參考型別。 實現該介面的所有類和結構都必須實現該成員集。 介面可以為任何或所有這些成員定義預設實現。 一個類別可以實作多個介面，但只能衍生自單一直接基底類別。

介面用於為不一定具有"是"關係的類定義特定功能。 例如，<xref:System.IEquatable%601?displayProperty=nameWithType>介面可以由任何類或結構實現，以確定類型的兩個物件是否等效（但是類型定義等價）。 <xref:System.IEquatable%601>並不意味著基類和派生類之間存在的相同類型的"是"關係（例如， 是`Mammal`。 `Animal` 如需詳細資訊，請參閱[介面](../interfaces/index.md)。

## <a name="preventing-further-derivation"></a>防止進一步推導  

類可以通過聲明自身或成員為[`sealed`](../../language-reference/keywords/sealed.md)來阻止其他類從它或其任何成員繼承。 有關詳細資訊，請參閱[抽象類別和密封類和類成員](./abstract-and-sealed-classes-and-class-members.md)。

## <a name="derived-class-hiding-of-base-class-members"></a>基類成員的派生類隱藏  

衍生類別可藉由以相同的名稱和簽章宣告基底類別成員，來隱藏這些成員。 修改[`new`](../../language-reference/keywords/new-modifier.md)器可用於顯式指示成員不是要覆蓋基成員。 不需要 使用[`new`](../../language-reference/keywords/new-modifier.md)，但如果不使用，將生成[`new`](../../language-reference/keywords/new-modifier.md)編譯器警告。 如需詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](./versioning-with-the-override-and-new-keywords.md)和[了解使用 Override 和 New 關鍵字的時機](./knowing-when-to-use-override-and-new-keywords.md)。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](./index.md)
- [class](../../language-reference/keywords/class.md)
