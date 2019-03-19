---
title: 繼承 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 9ad7253fb9efc891e1f0fdea118e1fe7bde6a857
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "58125911"
---
# <a name="inheritance-c-programming-guide"></a>繼承 (C# 程式設計手冊)

繼承是物件導向程式設計的三個主要特性之一，另外兩個是封裝和多型。 繼承可讓您建立新類別以重複使用、擴充和修改其他類別中定義的行為。 成員被繼承的類別稱為「基底類別」，而繼承這種成員的類別即稱為「衍生類別」。 衍生類別只能有一個基底類別。 不過，繼承是可轉移的。 如果 ClassC 衍生自 ClassB，而 ClassB 衍生自 ClassA，則 ClassC 會繼承在 ClassB 和 ClassA 中宣告的所有成員。  
  
> [!NOTE]
>  結構不支援繼承，但可以實作介面。 如需詳細資訊，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。  
  
 就概念而言，衍生類別是基底類別的特製化項目。 例如，如果您有一個基底類別 `Animal`，您可能會有一個名為 `Mammal` 的衍生類別，以及另一個名為 `Reptile` 的衍生類別。 `Mammal` 是 `Animal`，`Reptile` 也是 `Animal`，但這兩個衍生類別各代表不同的基底類別特製化項目。  
  
 當您將某個類別定義為要從另一個類別衍生時，衍生類別會隱含取得基底類別的所有成員，但建構函式和完成項則除外。 因此，衍生類別可以重複使用基底類別中的程式碼，而不需要重新實作。 您可以在衍生類別中新增更多成員。 透過這種方式，衍生類別等於是擴充了基底類別的功能。  
  
 下圖顯示 `WorkItem` 類別，代表某些商務程序中的工作項目。 它和所有類別一樣，會衍生自 <xref:System.Object?displayProperty=nameWithType> 並繼承其所有方法。 `WorkItem` 會新增自己的五個成員。 由於不會繼承建構函式，因此這些成員會包含一個建構函式。 `ChangeRequest` 類別繼承自 `WorkItem`，並代表特定類型的工作項目。 `ChangeRequest` 會在繼承自 `WorkItem` 和 <xref:System.Object> 的成員中，另外新增兩個成員。 它必須新增自己的建構函式，也會新增 `originalItemID`。 `originalItemID` 屬性可讓 `ChangeRequest` 執行個體與套用變更要求的原始 `WorkItem` 產生關聯。  
  
 ![顯示類別繼承的圖表](./media/inheritance/class-inheritance-diagram.png)  
  
 下列範例示範如何以 C# 表示上圖所示範的類別關聯性。 此範例也會示範 `WorkItem` 如何覆寫 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 虛擬方法，以及 `ChangeRequest` 類別如何繼承方法的 `WorkItem` 實作。  
  
 [!code-csharp[csProgGuideInheritance#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#49)]  
  
## <a name="abstract-and-virtual-methods"></a>抽象和虛擬方法  
 當基底類別將方法宣告為[虛擬](../../../csharp/language-reference/keywords/virtual.md)時，衍生類別可以使用自己的實作來[覆寫](../../../csharp/language-reference/keywords/override.md)該方法。 如果基底類別將成員宣告為[抽象](../../../csharp/language-reference/keywords/abstract.md)，則在所有直接繼承自該類別的非抽象類別中，都必須覆寫該方法。 如果衍生類別本身就是抽象的，則會繼承抽象成員而不需要進行實作。 抽象和虛擬成員是多型的基礎，而多型是物件導向程式設計的第二個主要特性。 如需詳細資訊，請參閱[多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)。  
  
## <a name="abstract-base-classes"></a>抽象基底類別  
 如果您想要使用 [new](../../../csharp/language-reference/keywords/new.md) 關鍵字來防止直接具現化，您可以將類別宣告為[抽象](../../../csharp/language-reference/keywords/abstract.md)。 如果這麼做，只有在新類別衍生自此類別時，才能使用此類別。 抽象類別可以包含一或多個本身宣告為抽象的方法簽章。 這些簽章可指定參數和傳回值，但沒有實作 (方法主體)。 抽象類別不需要包含抽象成員；但如果某個類別包含抽象成員，則該類別本身必須宣告為抽象。 本身不是抽象的衍生類別，必須為來自抽象基底類別的所有抽象方法提供實作。 如需詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
## <a name="interfaces"></a>介面  
 「介面」是一種參考型別，某些方面與只包含抽象成員的抽象基底類別類似。 當類別實作介面時，必須為介面的所有成員提供實作。 一個類別可以實作多個介面，但只能衍生自單一直接基底類別。  
  
 介面可用來為不一定有「是」關聯性的類別，定義其特定功能。 例如，所有必須啟用用戶端程式碼的類別或結構，都可以實作 <xref:System.IEquatable%601?displayProperty=nameWithType> 介面來判斷屬於該類型的兩個物件是否對等 (不過其類型會定義等價)。 <xref:System.IEquatable%601> 不表示基底類別和衍生類別之間存在「是」這類的關聯性 (例如 `Mammal` 是 `Animal`)。 如需詳細資訊，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。  
  
## <a name="preventing-further-derivation"></a>防止進一步衍生  
 將類別本身或其成員宣告為[密封](../../../csharp/language-reference/keywords/sealed.md)，即可防止其他類別繼承該類別，或繼承其任何成員。 如需詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
## <a name="derived-class-hiding-of-base-class-members"></a>衍生類別隱藏基底類別成員  
 衍生類別可藉由以相同的名稱和簽章宣告基底類別成員，來隱藏這些成員。 您可以使用 [new](../../../csharp/language-reference/keywords/new.md) 修飾詞，明確指示成員不是用於基底成員的覆寫。 您不一定要使用 [new](../../../csharp/language-reference/keywords/new.md)，但如果未使用 [new](../../../csharp/language-reference/keywords/new.md)，則會產生編譯器警告。 如需詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)和[了解使用 Override 和 New 關鍵字的時機](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)
- [class](../../../csharp/language-reference/keywords/class.md)
- [struct](../../../csharp/language-reference/keywords/struct.md)
