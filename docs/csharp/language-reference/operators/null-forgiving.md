---
title: '! （null-容許）運算子- C# reference'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291722"
---
# <a name="-null-forgiving-operator-c-reference"></a>! （null-容許）運算子（C#參考）

可在C# 8.0 和更新版本中使用，一元後置 `!` 運算子是 null 容許運算子。 在啟用的[可為 null 注釋內容](../../nullable-references.md#nullable-annotation-context)中，您可以使用 null 容許運算子來宣告參考型別的運算式 `x` 不是 null： `x!`。 一元前置字元 `!` 運算子是[邏輯負運算子](boolean-logical-operators.md#logical-negation-operator-)。

Null 容許運算子在執行時間沒有任何作用。 它只會影響編譯器的靜態流程分析，方法是變更運算式的 null 狀態。 在執行時間，expression `x!` 會評估為基礎運算式 `x` 的結果。

如需可為 null 的參考型別功能的詳細資訊，請參閱[可為 null 的參考型別](../../nullable-references.md)。

## <a name="examples"></a>範例

Null 容許運算子的其中一個使用案例是測試引數驗證邏輯。 例如，請參考下列類別：

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

使用[MSTest 測試架構](../../../core/testing/unit-testing-with-mstest.md)，您可以在函式中針對驗證邏輯建立下列測試：

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

如果沒有 null 容許運算子，編譯器會針對上述程式碼產生下列警告： `Warning CS8625: Cannot convert null literal to non-nullable reference type`。 使用 null 容許運算子時，您可以讓編譯器知道預期傳遞 `null`，而不應該收到關於的警告。

當您肯定知道運算式不能 `null`，但編譯器不會管理來辨識這一點時，您也可以使用 null 容許運算子。 在下列範例中，如果 `IsValid` 方法傳回 `true`，其引數不會 `null`，而您可以安全地進行取值：

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

如果沒有 null 容許運算子，編譯器會為 `p.Name` 程式碼產生下列警告： `Warning CS8602: Dereference of a possibly null reference.`。

如果您可以修改 `IsValid` 方法，您可以使用[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)屬性，讓編譯器知道當方法傳回 `true` 時，@no__t 2 方法的引數不能 `null`：

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

在上述範例中，您不需要使用 null-容許運算子，因為編譯器有足夠的資訊可發現 `p` 不能在 `if` 語句內 `null`。 如需可讓您指定變數之 null 狀態的其他資訊之屬性的詳細資訊，請參閱[使用屬性升級 api 以定義 null 預期](../../nullable-attributes.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [教學課程：以可為 null 的參考型別設計 @ no__t-0
