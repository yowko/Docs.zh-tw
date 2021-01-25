---
title: 存取修飾詞 - C# 程式設計手冊
description: 'C # 中的所有類型和類型成員都具有存取範圍層級，可控制是否可從其他程式碼使用。 請參閱這份存取修飾詞清單。'
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: d800116137e088a54edb221fb4f81ecd47b0278f
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757859"
---
# <a name="access-modifiers-c-programming-guide"></a>存取修飾詞 (C# 程式設計手冊)

所有類型和類型成員都具有存取範圍層級。 存取範圍層級可控制是否可從元件或其他元件中的其他程式碼使用它們。 當您宣告類型或成員時，請使用下列存取修飾詞來指定其存取範圍：

- [public](../../language-reference/keywords/public.md)：類型或成員可由相同元件中的任何其他程式碼或參考它的另一個元件存取。
- [私](../../language-reference/keywords/private.md)用：類型或成員只能由相同或中的程式碼存取 `class` `struct` 。
- [protected](../../language-reference/keywords/protected.md)：類型或成員只能由相同 `class` 或 `class` 衍生自的程式碼存取 `class` 。
- [internal](../../language-reference/keywords/internal.md)：相同元件中的任何程式碼都可以存取類型或成員，但不能存取另一個元件的類型或成員。
- [protected internal](../../language-reference/keywords/protected-internal.md)：類型或成員可以由其宣告之元件中的任何程式碼存取，或從另一個元件的衍生記憶體取 `class` 。
- [私用保護](../../language-reference/keywords/private-protected.md)：類型或成員只能在其宣告元件中，透過相同 `class` 或衍生自該型別的程式碼來存取 `class` 。

下列範例示範如何指定類型和成員的存取修飾詞︰

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

並非所有存取修飾詞對所有內容中的所有類型或成員都有效。 在某些情況下，類型成員的存取範圍會受限於其包含類型的存取範圍。

## <a name="class-and-struct-accessibility"></a>類別和結構存取範圍  

直接在命名空間內宣告的類別和結構 (換句話說，不會嵌套在其他類別或結構中) 可以是 `public` 或 `internal` 。 `internal` 如果未指定存取修飾詞，則為預設值。

結構成員（包括嵌套類別和結構）可以宣告為 `public` 、 `internal` 或 `private` 。 類別成員（包括嵌套類別和結構）可以是 `public` 、 `protected internal` 、 `protected` 、 `internal` 、 `private protected` 或 `private` 。 類別和結構成員（包括嵌套類別和結構） `private` 預設具有存取權。 私用巢狀型別無法從包含類型外部存取。

衍生類別的存取範圍不能比基底類型更大。 您無法宣告 `B` 衍生自內部類別的公用類別 `A` 。 如果允許，則會產生 public 的效果 `A` ，因為所有 `protected` 或 `internal` 成員 `A` 都可以從衍生類別存取。

您可以使用來啟用特定其他元件，以存取您的內部類型 `InternalsVisibleToAttribute` 。 如需詳細資訊，請參閱 [Friend 元件](../../../standard/assembly/friend.md)。

## <a name="class-and-struct-member-accessibility"></a>類別和結構成員存取範圍  

您可使用六種存取類型的任一種，宣告類別成員 (包括巢狀類別和結構)。 結構成員不可以宣告為 `protected` 、 `protected internal` 或， `private protected` 因為結構不支援繼承。

一般情況下，成員的存取範圍不會大於包含它之類型的存取範圍。 但是， `public` 如果成員執行介面方法或覆寫公用基類中所定義的虛擬方法，則可以從元件外部存取內部類別的成員。

任何成員欄位、屬性或事件的類型至少必須可以像成員本身一樣存取。 同樣地，任何方法、索引子或委派的傳回型別和參數類型至少必須可以像成員本身一樣存取。 例如， `public` `M` `C` 除非也是，否則您 `C` 不能有傳回類別的方法 `public` 。 同樣地，如果是宣告為，則您不能具有 `protected` 類型的屬性 `A` `A` `private` 。

使用者定義運算子必須一律宣告為 `public` 和 `static` 。 如需詳細資訊，請參閱[運算子多載](../../language-reference/operators/operator-overloading.md)。

完成項不能有存取範圍修飾詞。

若要設定或成員的存取層級 `class` `struct` ，請在成員宣告中加入適當的關鍵字，如下列範例所示。

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>其他類型

直接在命名空間內宣告的介面可以是 `public` 或 `internal` ，就像類別和結構一樣，介面預設為 `internal` access。 介面成員預設為， `public` 因為介面的用途是讓其他類型存取類別或結構。 介面成員宣告可能包含任何存取修飾詞。 這最適用于靜態方法，以提供類別所有實作者所需的常見實作為。

列舉成員一律為 `public` ，而且不能套用任何存取修飾詞。

委派的行為類似類別和結構。 依預設，當您 `internal` 直接在命名空間內宣告時，它們具有存取權，並 `private` 在進行嵌套時存取。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [類別和結構](./index.md)
- [介面](../interfaces/index.md)
- [私人](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [內部](../../language-reference/keywords/internal.md)
- [受保護](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [結構](../../language-reference/builtin-types/struct.md)
- [interface](../../language-reference/keywords/interface.md)
