---
title: 存取修飾詞 - C# 程式設計手冊
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628224"
---
# <a name="access-modifiers-c-programming-guide"></a>存取修飾詞 (C# 程式設計手冊)

所有類型和類型成員都具有存取範圍層級。 存取範圍層級控制是否可以從元件或其他元件中的其他程式碼使用它們。 當您宣告類型或成員時，請使用下列存取修飾詞來指定其存取範圍：

- [public](../../language-reference/keywords/public.md)：類型或成員可由相同元件中的任何其他程式碼或參考它的另一個元件來存取。
- [私](../../language-reference/keywords/private.md)用：類型或成員只能由相同 `class` 或 `struct`中的程式碼存取。
- [protected](../../language-reference/keywords/protected.md)：類型或成員只能由相同 `class`中的程式碼或衍生自該 `class`的 `class` 存取。
- [內部](../../language-reference/keywords/internal.md)：類型或成員可由相同元件中的任何程式碼存取，但不能由另一個元件存取。
- [protected internal](../../language-reference/keywords/protected-internal.md)：類型或成員可由其宣告所在之元件中的任何程式碼存取，或從另一個元件中的衍生 `class`。
- [私用保護](../../language-reference/keywords/private-protected.md)：類型或成員只能在其宣告元件、相同 `class` 中的程式碼或衍生自該 `class`的類型中存取。

下列範例示範如何指定類型和成員的存取修飾詞︰

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

並非所有的存取修飾詞對所有內容中的所有類型或成員都有效。 在某些情況下，類型成員的存取範圍會受到其包含類型的存取範圍所限制。

## <a name="class-and-struct-accessibility"></a>類別和結構協助工具  

直接在命名空間內宣告的類別和結構（換句話說，不是在其他類別或結構內）可以是 `public` 或 `internal`。 如果未指定任何存取修飾詞，`Internal` 是預設值。  

結構成員（包括嵌套類別和結構）可以 `public`、`internal`或 `private`來宣告。 類別成員（包括嵌套類別和結構）可以是 `public`、`protected internal`、`protected`、`internal`、`private protected`或 `private`。 類別和結構成員（包括嵌套類別和結構）預設具有 `private` 存取。 無法從包含類型外部存取私用的巢狀型別。

衍生類別的存取範圍無法高於其基底類型。 您無法宣告衍生自內部類別 `A`的公用類別 `B`。 如果允許，則會產生 `A` public 的效果，因為 `A` 的所有 `protected` 或 `internal` 成員都可以從衍生類別存取。

您可以使用 `InternalsVisibleToAttribute`，讓特定的其他元件存取您的內部類型。 如需詳細資訊，請參閱 [Friend Assemblies](../../../standard/assembly/friend.md) (Friend 組件)。

## <a name="class-and-struct-member-accessibility"></a>類別和結構成員存取範圍  

您可使用六種存取類型的任一種，宣告類別成員 (包括巢狀類別和結構)。 結構成員不能宣告為 `protected`、`protected internal`或 `private protected`，因為結構不支援繼承。

一般來說，成員的存取範圍不會大於包含它之類型的存取範圍。 不過，如果成員執行介面方法或覆寫在公用基類中定義的虛擬方法，則內部類別的 `public` 成員可能可以從元件外部存取。

任何成員欄位、屬性或事件的類型，都必須至少與成員本身一樣可以存取。 同樣地，任何方法、索引子或委派的傳回型別和參數類型，都必須至少與成員本身一樣可以存取。 例如，除非也 `public``C`，否則您不能有傳回類別 `C` 的 `public` 方法 `M`。 同樣地，如果 `A` 宣告為 `private`，您就不能有 `A` 類型的 `protected` 屬性。

使用者定義的運算子必須一律宣告為 `public` 和 `static`。 如需詳細資訊，請參閱[運算子多載](../../language-reference/operators/operator-overloading.md)。

完成項不能有存取範圍修飾詞。

若要設定 `class` 或 `struct` 成員的存取層級，請將適當的關鍵字新增至成員宣告，如下列範例所示。

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>其他類型

直接在命名空間內宣告的介面可以 `public` 或 `internal`，而且就像類別和結構一樣，介面預設為 `internal` 存取。 預設會 `public` 介面成員，因為介面的目的是要讓其他類型可以存取類別或結構。 介面成員宣告可能包含任何存取修飾詞。 這最適用于靜態方法，以提供類別的所有實作者所需的一般程式。

列舉成員一律 `public`，而且不能套用任何存取修飾詞。

委派的行為類似類別和結構。 根據預設，當直接在命名空間中宣告時，它們會有 `internal` 的存取權，並在進行嵌套時 `private` 存取。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](./index.md)
- [介面](../interfaces/index.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/builtin-types/struct.md)
- [interface](../../language-reference/keywords/interface.md)
