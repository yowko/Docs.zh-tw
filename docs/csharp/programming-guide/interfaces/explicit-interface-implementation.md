---
title: 明確介面實作 - C# 程式設計指南
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628146"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>明確介面實作 (C# 程式設計手冊)

如果[類別](../../language-reference/keywords/class.md)實作兩個具有相同簽章成員的介面，則在類別上實作該成員會造成這兩個介面都使用該成員進行實作。 在下列範例中，所有對 `Paint` 的呼叫都會叫用相同的方法。 第一個範例會定義類型：

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

下列範例會呼叫方法：

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

當兩個介面成員未執行相同的函式時，會導致其中一個或兩個介面的實作為不正確。 您可以明確地實作為介面成員，建立只透過介面呼叫且專屬於該介面的類別成員。 將類別成員命名為介面的名稱和句點。 例如：

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

類別成員 `IControl.Paint` 只能透過 `IControl` 介面取得，`ISurface.Paint` 只能透過 `ISurface` 取得。 這兩種方法都是分開的，而且都無法直接在類別上使用。 例如：

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

明確的執行也可用來解決兩個介面各自宣告相同名稱的不同成員（例如屬性和方法）的情況。 若要同時執行這兩個介面，類別必須針對屬性 `P`或方法 `P`（或兩者）使用明確的執行，以避免編譯器錯誤。 例如：

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

如果類別繼承介面的方法執行，則只能透過介面類別型的參考來存取該方法。 繼承的成員不會顯示為公用介面的一部分。 下列範例會定義介面方法的預設實值：

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

下列範例會叫用預設的實值：

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

任何實 `IControl` 介面的類別，都可以覆寫預設的 `Paint` 方法（做為公用方法），或做為明確介面的執行。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](../classes-and-structs/index.md)
- [介面](./index.md)
- [繼承](../classes-and-structs/inheritance.md)
