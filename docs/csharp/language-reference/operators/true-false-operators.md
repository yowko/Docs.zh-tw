---
title: true 和 false 運算子 - C# 參考
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 5ccd08a348478902bbbac36e99acf7ffc1fc814b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846210"
---
# <a name="true-and-false-operators-c-reference"></a>true 和 false 運算子 (C# 參考)

運算子`true`返回[bool](../builtin-types/bool.md)值`true`以指示其運算元絕對正確。 運算子`false`返回該`bool`值`true`以指示其運算元絕對為 false。 `true` 和 `false` 運算子並不保證會彼此互補。 也就是說，`true` 和 `false` 運算子可能會針對相同的運算元傳回 `bool` 值 `false`。 如果某個型別會定義這兩個運算子之一，它也必須定義另一個運算子。

> [!TIP]
> 如果需要支援`bool?`三值邏輯（例如，當您使用支援三值布林類型的資料庫時），請使用類型。 C# 能提供搭配 `bool?` 運算元來支援三值邏輯的 `&` 和 `|` 運算子。 如需詳細資訊，請參閱[布林邏輯運算子](boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](boolean-logical-operators.md#nullable-boolean-logical-operators)一節。

## <a name="boolean-expressions"></a>布林運算式

具有已定義 `true` 運算子的型別可以是 [if](../keywords/if-else.md)、[do](../keywords/do.md)、[while](../keywords/while.md) 及 [for](../keywords/for.md) 陳述式，以及[條件運算子 `?:`](conditional-operator.md)中之控制條件運算式的結果型別。 如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[布林運算式](~/_csharplang/spec/expressions.md#boolean-expressions)一節。

## <a name="user-defined-conditional-logical-operators"></a>使用者定義條件式邏輯運算子

如果具有已定義 `true` 和 `false` 運算子的型別會以某種方式[多載](operator-overloading.md)[邏輯 OR 運算子](boolean-logical-operators.md#logical-or-operator-) `|` 或 [邏輯 AND 運算子](boolean-logical-operators.md#logical-and-operator-) `&`，系統便可針對該型別的運算元評估[條件邏輯 OR 運算子](boolean-logical-operators.md#conditional-logical-or-operator-) `||` 或 [條件邏輯 AND 運算子](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`。 如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。

## <a name="example"></a>範例

下列範例顯示同時定義了 `true` 和 `false` 運算子的型別。 類型還重載邏輯 AND 運算子`&`，以便也可以計算`&&`該類型的運算元。

[!code-csharp[true and false operators example](snippets/TrueFalseOperators.cs)]

請注意 `&&` 運算子的最少運算行為。 當 `GetFuelLaunchStatus` 方法傳回 `LaunchStatus.Red` 時，系統並不會評估 `&&` 運算子的右邊運算元。 這是因為 `LaunchStatus.Red` 必然為 false。 然後邏輯 AND 的結果並不取決於右邊運算元的值。 此範例的輸出如下：

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
