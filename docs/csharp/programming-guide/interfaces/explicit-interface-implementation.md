---
title: 明確介面實作 - C# 程式設計指南
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167669"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>明確介面實作 (C# 程式設計手冊)

如果[類別](../../language-reference/keywords/class.md)實作兩個具有相同簽章成員的介面，則在類別上實作該成員會造成這兩個介面都使用該成員進行實作。 在下列範例中，所有對 `Paint` 的呼叫都會叫用相同的方法。 第一個示例定義類型：

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

以下示例調用這些方法：

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

當兩個介面成員不執行相同的函數時，它會導致一個或兩個介面的實現不正確。 可以顯式實現介面成員 — 創建僅通過介面調用且特定于該介面的類成員。 使用介面和句點的名稱命名類成員。 例如：

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

類別成員 `IControl.Paint` 只能透過 `IControl` 介面取得，`ISurface.Paint` 只能透過 `ISurface` 取得。 兩個方法實現都是獨立的，並且兩者都沒有直接在類上可用。 例如：

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

顯式實現還用於解決兩個介面都聲明相同名稱的不同成員（如屬性和方法）的情況。 要實現這兩個介面，類必須對屬性`P`、方法`P`或兩者使用顯式實現，以避免編譯器錯誤。 例如：

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

從[C# 8.0](../../whats-new/csharp-8.md#default-interface-methods)開始，可以為在介面中聲明的成員定義實現。 如果類從介面繼承方法實現，則只能通過介面類別型的引用訪問該方法。 繼承的成員不顯示為公共介面的一部分。 以下示例定義介面方法的預設實現：

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

以下示例調用預設實現：

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

實現`IControl`介面的任何類都可以重寫預設`Paint`方法，也可以作為公共方法重寫，也可以作為明確介面實作重寫。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](../classes-and-structs/index.md)
- [介面](./index.md)
- [繼承](../classes-and-structs/inheritance.md)
