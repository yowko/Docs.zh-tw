---
title: 預設運算子 - C# 參考
ms.custom: seodec18
description: 使用預設運算子來產生型別的預設值
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 5623cb9dc3790b5bb99635c41cb3f122f4c71d8e
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796937"
---
# <a name="default-operator-c-reference"></a>預設運算子 (C# 參考)

`default` 運算子會產生型別的[預設值](../keywords/default-values-table.md)。 `default` 運算子的引數必須是型別或或型別參數的名稱。

下列範例會示範 `default` 運算子的使用方式：

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

您也可以在 [`switch` 陳述式](../keywords/switch.md)使用 `default` 關鍵字作為預設案例標籤。

## <a name="default-literal"></a>預設常值

從 C# 7.1 開始，當編譯器可以推斷運算式型別時，您可以使用 `default` 常值來產生型別的預設值。 `default` 常值運算式會產生與對`default(T)` 運算式相同的值，其中 `T` 是推斷出來的型別。 在下列任一情況中，您都可以使用 `default` 常值：

- 在指派或初始化變數時。
- 在選擇性方法參數的預設值宣告中。
- 在提供引數值的方法呼叫中。
- 在 `return` 陳述式中，或作為陳述式主體成員中的運算式。

下列範例會示範 `default` 常值的使用方式：

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[預設值運算式](~/_csharplang/spec/expressions.md#default-value-expressions)一節。

如需有關 `default` 常值的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.1/target-typed-default.md) \(英文\)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [預設值表](../keywords/default-values-table.md)
