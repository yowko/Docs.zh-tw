---
title: 如何：使用字典儲存事件執行個體 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 03/11/2019
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f8522e499887398402f63c7788bbc6c6c4f57782
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "57845266"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="771f2-102">如何：使用字典儲存事件執行個體 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="771f2-102">How to: use a dictionary to store event instances (C# Programming Guide)</span></span>

<span data-ttu-id="771f2-103">`add` 和 `remove` 自訂事件存取子的用法之一，是在不為每個事件配置欄位的情況下公開許多事件，而是使用 <xref:System.Collections.Generic.Dictionary%602> 執行個體來儲存事件執行個體，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="771f2-103">One use for the `add` and `remove` custom event accessors is to expose many events without allocating a field for each event, but instead using a <xref:System.Collections.Generic.Dictionary%602> instance to store the event instances, as the example below demonstrates.</span></span> <span data-ttu-id="771f2-104">這只有在型別有許多事件，但您預期不會訂閱大多數事件時才有用。</span><span class="sxs-lookup"><span data-stu-id="771f2-104">This is only useful if a type has many events, but you expect that most of the events will not be subscribed to.</span></span>

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

<span data-ttu-id="771f2-105">此實作符合在 C# 語言規格中[新增和移除委派](~/_csharplang/spec/delegates.md#delegate-invocation)的行為。</span><span class="sxs-lookup"><span data-stu-id="771f2-105">This implementation conforms to the behavior for [adding and removing delegates](~/_csharplang/spec/delegates.md#delegate-invocation) in the C# language specification.</span></span>

<span data-ttu-id="771f2-106">請注意，[lock](../../language-reference/keywords/lock-statement.md) 陳述式僅用於使用事件處理常式存取字典。</span><span class="sxs-lookup"><span data-stu-id="771f2-106">Note that the [lock](../../language-reference/keywords/lock-statement.md) statement is used only to *access* the dictionary with event handlers.</span></span> <span data-ttu-id="771f2-107">不要在 `lock` 陳述式的主體內叫用事件處理常式，因為它可能會導致死結或鎖定爭用。</span><span class="sxs-lookup"><span data-stu-id="771f2-107">Don't invoke an event handler inside the body of the `lock` statement, as it could lead to deadlocks or lock contention.</span></span>

## <a name="see-also"></a><span data-ttu-id="771f2-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="771f2-108">See also</span></span>

- [<span data-ttu-id="771f2-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="771f2-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="771f2-110">事件</span><span class="sxs-lookup"><span data-stu-id="771f2-110">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="771f2-111">委派</span><span class="sxs-lookup"><span data-stu-id="771f2-111">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
