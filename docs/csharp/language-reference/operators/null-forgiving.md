---
title: '!  (null-容許) 運算子-c # 參考'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: b21b8a1f3c182fdc58d297424e0e70885e209e94
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555145"
---
# <a name="-null-forgiving-operator-c-reference"></a>!  (null-容許) 運算子 (c # 參考) 

適用于 c # 8.0 和更新版本，一元 `!` 後置運算子是 null 容許運算子。 在啟用的[可為 null 注釋內容](../../nullable-references.md#nullable-annotation-context)中，您可以使用 null 容許運算子來宣告 `x` 參考型別的運算式不是 `null` ： `x!` 。 一元前置 `!` 運算子是[邏輯負運算子](boolean-logical-operators.md#logical-negation-operator-)。

Null 容許運算子在執行時間沒有任何作用。 它只會影響編譯器的靜態流程分析，方法是變更運算式的 null 狀態。 在執行時間，expression 會 `x!` 評估為基礎運算式的結果 `x` 。

> [!NOTE]
> 在 c # 8 中，null 容許運算子會終止前面的[null 條件](member-access-operators.md#null-conditional-operators--and-)運算清單。 例如，運算式會剖析 `x?.y!.z` 為 `(x?.y)!.z` 。 由於這種轉譯， `z` 即使為，也會評估， `x` `null` 這可能會導致 <xref:System.NullReferenceException> 。

如需可為 null 的參考型別功能的詳細資訊，請參閱[可為 null 的參考型別](../builtin-types/nullable-reference-types.md)。

## <a name="examples"></a>範例

Null 容許運算子的其中一個使用案例是測試引數驗證邏輯。 例如，請參考下列類別：

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

使用[MSTest 測試架構](../../../core/testing/unit-testing-with-mstest.md)，您可以在函式中針對驗證邏輯建立下列測試：

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

如果沒有 null 容許運算子，編譯器會針對上述程式碼產生下列警告： `Warning CS8625: Cannot convert null literal to non-nullable reference type` 。 藉由使用 null 容許運算子，您可以通知編譯器 `null` 預期傳遞，而不應該收到關於的警告。

當您肯定知道運算式不能是， `null` 但編譯器不會管理來辨識這種情況時，也可以使用 null 容許運算子。 在下列範例中，如果 `IsValid` 方法傳回 `true` ，則其引數不是， `null` 而且您可以安全地進行取值：

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

如果沒有 null 容許運算子，編譯器會為程式碼產生下列警告 `p.Name` ： `Warning CS8602: Dereference of a possibly null reference` 。

如果您可以修改 `IsValid` 方法，您可以使用[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)屬性來通知編譯器，當方法傳回時，方法的引數 `IsValid` 不能是 `null` `true` ：

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

在上述範例中，您不需要使用 null 容許運算子，因為編譯器有足夠的資訊可以找出 `p` 不在 `null` 語句內的 `if` 。 如需可讓您提供變數 null 狀態之其他相關資訊的屬性詳細資訊，請參閱[使用屬性升級 api 以定義 null 預期](../attributes/nullable-analysis.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[可為 null 的參考型別規格之草稿](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)的[null-容許運算子](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [教學課程：使用可為 null 的參考型別進行設計](../../tutorials/nullable-reference-types.md)
