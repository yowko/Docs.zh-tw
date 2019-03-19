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
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>如何：使用字典儲存事件執行個體 (C# 程式設計手冊)

`add` 和 `remove` 自訂事件存取子的用法之一，是在不為每個事件配置欄位的情況下公開許多事件，而是使用 <xref:System.Collections.Generic.Dictionary%602> 執行個體來儲存事件執行個體，如下列範例所示。 這只有在型別有許多事件，但您預期不會訂閱大多數事件時才有用。

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

此實作符合在 C# 語言規格中[新增和移除委派](~/_csharplang/spec/delegates.md#delegate-invocation)的行為。

請注意，[lock](../../language-reference/keywords/lock-statement.md) 陳述式僅用於使用事件處理常式存取字典。 不要在 `lock` 陳述式的主體內叫用事件處理常式，因為它可能會導致死結或鎖定爭用。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [事件](../../../csharp/programming-guide/events/index.md)
- [委派](../../../csharp/programming-guide/delegates/index.md)
