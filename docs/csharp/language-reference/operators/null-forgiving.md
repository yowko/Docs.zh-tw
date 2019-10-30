---
title: '! （null-容許）運算子- C# reference'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 21bbf8e1253641317750b911e052ee5ff0a0d063
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036165"
---
# <a name="-null-forgiving-operator-c-reference"></a>! （null-容許）運算子（C#參考）

可在C# 8.0 和更新版本中使用，一元後置 `!` 運算子是 null 容許運算子。 在啟用的[可為 null 注釋內容](../../nullable-references.md#nullable-annotation-context)中，您可以使用 null 容許運算子來宣告參考型別的運算式 `x` 不 `null`： `x!`。 一元前置字元 `!` 運算子是[邏輯負運算子](boolean-logical-operators.md#logical-negation-operator-)。

Null 容許運算子在執行時間沒有任何作用。 它只會影響編譯器的靜態流程分析，方法是變更運算式的 null 狀態。 在執行時間，expression `x!` 會評估為基礎運算式 `x` 的結果。

如需可為 null 的參考型別功能的詳細資訊，請參閱[可為 null 的參考型別](../../nullable-references.md)。

## <a name="examples"></a>範例

Null 容許運算子的其中一個使用案例是測試引數驗證邏輯。 例如，請參考下列類別：

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

使用[MSTest 測試架構](../../../core/testing/unit-testing-with-mstest.md)，您可以在函式中針對驗證邏輯建立下列測試：

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

如果沒有 null 容許運算子，編譯器會針對上述程式碼產生下列警告： `Warning CS8625: Cannot convert null literal to non-nullable reference type`。 藉由使用 null 容許運算子，您可以通知編譯器預期傳遞 `null`，而不應警告相關。

您也可以使用 null 容許運算子，但您一定知道運算式無法 `null`，但編譯器無法管理來辨識這種情況。 在下列範例中，如果 `IsValid` 方法傳回 `true`，則不會 `null` 其引數，而您可以安全地對其進行取值：

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

如果沒有 null 容許運算子，編譯器會為 `p.Name` 程式碼產生下列警告： `Warning CS8602: Dereference of a possibly null reference`。

如果您可以修改 `IsValid` 方法，您可以使用[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)屬性來通知編譯器，當方法傳回 `true`時，無法 `null` `IsValid` 方法的引數：

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

在上述範例中，您不需要使用 null 容許運算子，因為編譯器有足夠的資訊可找出在 `if` 語句內無法 `null` `p`。 如需可讓您提供變數 null 狀態之其他相關資訊的屬性詳細資訊，請參閱[使用屬性升級 api 以定義 null 預期](../../nullable-attributes.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[可為 null 的參考型別規格之草稿](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)的[null-容許運算子](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator)一節。

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [教學課程：使用可為 null 的參考型別進行設計](../../tutorials/nullable-reference-types.md)
