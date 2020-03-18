---
title: 存取修飾詞 - C# 程式設計手冊
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628224"
---
# <a name="access-modifiers-c-programming-guide"></a>存取修飾詞 (C# 程式設計手冊)

所有類型和類型成員都有協助工具級別。 協助工具級別控制它們是否可以從程式集中的其他代碼或其他程式集使用。 在聲明類型或成員時，請使用以下訪問修改器指定其可訪問性：

- [公共](../../language-reference/keywords/public.md)：類型或成員可以由同一程式集中的任何其他代碼或引用它的其他程式集訪問。
- [私有](../../language-reference/keywords/private.md)： 類型或成員只能由同`class`一或`struct`中的代碼訪問。
- [受保護](../../language-reference/keywords/protected.md)： 類型或成員只能由同`class`一中的代碼或`class`派生自 該`class`的代碼訪問。
- [內部](../../language-reference/keywords/internal.md)：類型或成員可以由同一程式集中的任何代碼訪問，但不能從其他程式集訪問。
- [受保護的內部](../../language-reference/keywords/protected-internal.md)：類型或成員可以由聲明它的程式集中的任何代碼訪問，也可以從派生於另一個程式集`class`中訪問。
- [私有受保護](../../language-reference/keywords/private-protected.md)： 類型或成員只能在其聲明程式集內、通過相同`class`代碼或派生自該`class`類型的代碼進行訪問。

下列範例示範如何指定類型和成員的存取修飾詞︰

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

並非所有訪問修改器對所有上下文中的所有類型或成員都有效。 在某些情況下，類型成員的可訪問性受其包含類型的可訪問性的限制。

## <a name="class-and-struct-accessibility"></a>類和結構可訪問性  

直接在命名空間內聲明的類和結構（換句話說，不嵌套在其他類或結構中）可以是或`public``internal`。 `Internal`如果未指定訪問修改器，則為預設值。  

可以聲明 結構成員（包括嵌套類和結構），可以聲明`public`、`internal`或`private`。 類成員（包括嵌套`public`類和結構）可以是 、、、、、、、`internal``private protected``private``protected internal``protected`或 。 預設情況下，類和結構成員（包括嵌套類和結構）具有`private`存取權限。 私有巢狀型別無法從包含類型外部訪問。

派生類的可訪問性不能大於其基本類型。 不能聲明派生自內部類的公共類`B``A`。 如果允許，它會產生`A`公開的效果，因為派生`protected``internal``A`類的所有成員都可以訪問。

可以使用 啟用特定的其他程式集來訪問內部類型`InternalsVisibleToAttribute`。 有關詳細資訊，請參閱[好友程式集](../../../standard/assembly/friend.md)。

## <a name="class-and-struct-member-accessibility"></a>類和結構成員可訪問性  

您可使用六種存取類型的任一種，宣告類別成員 (包括巢狀類別和結構)。 不能將結構成員聲明為`protected`，`protected internal`或`private protected`因為結構不支援繼承。

通常，成員的可訪問性不大於包含該成員的類型的可訪問性。 但是，如果`public`成員實現介面方法或重寫公共基類中定義的虛擬方法，則內部類的成員可以從程式集外部訪問。

任何成員欄位、屬性或事件的類型必須至少與成員本身一樣可訪問。 同樣，任何方法、索引子或委託的返回類型和參數類型必須至少與成員本身一樣可訪問。 例如`public`，除非`M``C``C`也是`public`，否則不能有返回類的方法。 同樣，如果`protected``A`聲明為`private`，則不能具有類型的`A`屬性。

使用者定義的運算子必須始終聲明為`public`和`static`。 如需詳細資訊，請參閱[運算子多載](../../language-reference/operators/operator-overloading.md)。

終結者不能具有協助工具修改器。

要設置`class`或`struct`成員的存取層級，向成員聲明添加相應的關鍵字，如以下示例所示。

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>其他類型

直接在命名空間中聲明的介面可以是`public`，`internal`並且，就像類和結構一樣，介面預設訪問`internal`。 預設情況下，介面`public`成員是因為介面的目的是使其他類型的類型能夠訪問類或結構。 介面成員聲明可以包括任何訪問修改器。 這對於靜態方法最有用，用於提供類的所有實現者所需的常見實現。

枚舉成員始終`public`為 ，並且不能應用訪問修改器。

委派的行為類似類別和結構。 預設情況下，它們在命名`internal`空間內直接聲明時具有存取權限，在`private`嵌套時具有存取權限。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](./index.md)
- [介面](../interfaces/index.md)
- [私人](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [內部](../../language-reference/keywords/internal.md)
- [保護](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/builtin-types/struct.md)
- [介面](../../language-reference/keywords/interface.md)
