---
title: true 和 false 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 0a75566fdb6222157ecda12a50fd78e22f92fcb4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245729"
---
# <a name="true-and-false-operators-c-reference"></a>true 和 false 運算子 (C# 參考)

`true` 運算子傳回 [bool](bool.md) 值 `true` 以指出運算元必然為 true。 `false` 運算子傳回 `bool` 值 `true` 以指出運算元必然為 false。 `true` 和 `false` 運算子並不保證會彼此互補。 也就是說，`true` 和 `false` 運算子可能會針對相同的運算元傳回 `bool` 值 `false`。 如果某個型別會定義這兩個運算子之一，它也必須定義另一個運算子。

如果具有已定義 `true` 和 `false` 運算子的型別會以某種方式[多載](operator.md)[邏輯 OR 運算子](../operators/or-operator.md) `|` 或 [邏輯 AND 運算子](../operators/and-operator.md) `&`，系統便可針對該型別的運算元評估[條件邏輯 OR 運算子](../operators/conditional-or-operator.md) `||` 或 [條件邏輯 AND 運算子](../operators/conditional-and-operator.md) `&&`。 如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。

具有已定義 `true` 運算子的型別可以是 [if](if-else.md)、[do](do.md)、[while](while.md) 及 [for](for.md) 陳述式，以及[條件運算子 `?:`](../operators/conditional-operator.md)中之控制條件運算式的結果型別。 如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[布林運算式](~/_csharplang/spec/expressions.md#boolean-expressions)一節。

> [!TIP]
> 如果您需要支援三值邏輯 (例如使用支援三值邏輯型別的資料庫時)，請使用 `bool?` 型別。 如需詳細資訊，請參閱[使用可為 Null 的型別](../../programming-guide/nullable-types/using-nullable-types.md)一文的 [bool? 型別](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type)一節。

下列範例顯示同時定義了 `true` 和 `false` 運算子的型別。 此外，它還多載邏輯 AND 運算子 `&`，使得系統也能針對該型別的運算元評估 `&&` 運算子。

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

請注意 `&&` 運算子的最少運算行為。 當 `GetFuelLaunchStatus` 方法傳回 `LaunchStatus.Red` 時，系統並不會評估 `&&` 運算子的第二個運算元。 這是因為 `LaunchStatus.Red` 必然為 false。 然後邏輯 AND 的結果並不取決於第二個運算元的值。 此範例的輸出如下：

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [C# 運算子](../operators/index.md)
- [`true` 常值](true-literal.md)
- [`false` 常值](false-literal.md)