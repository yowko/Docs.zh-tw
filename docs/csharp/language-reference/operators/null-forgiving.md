---
description: '!  (null 容許) 運算子-c # 參考'
title: '!  (null 容許) 運算子-c # 參考'
ms.date: 10/11/2019
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: f2eb57bba462d471a041c17024fa7031c2c7f87d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830580"
---
# <a name="-null-forgiving-operator-c-reference"></a>!  (null 容許) 運算子 (c # 參考) 

在 c # 8.0 和更新版本中提供，一元 `!` 後置運算子是 null 容許運算子。 在啟用的 [可為 null 注釋內容](../../nullable-references.md#nullable-annotation-context)中，您可以使用 null 容許運算子來宣告 `x` 參考型別的運算式不是 `null` ： `x!` 。 一元前置 `!` 運算子是 [邏輯負運算子](boolean-logical-operators.md#logical-negation-operator-)。

Null 容許運算子在執行時間不會有任何作用。 它只會變更運算式的 null 狀態，以影響編譯器的靜態流程分析。 在執行時間，運算式會 `x!` 評估為基礎運算式的結果 `x` 。

> [!NOTE]
> 在 c # 8 中，null 容許運算子會終止先前的 [null 條件式](member-access-operators.md#null-conditional-operators--and-) 作業清單。 例如，運算式會剖析 `x?.y!.z` 為 `(x?.y)!.z` 。 由於這種轉譯的緣故， `z` 即使 `x` 為，也會進行評估 `null` ，這樣可能會導致 <xref:System.NullReferenceException> 。

如需可為 null 的參考型別功能的詳細資訊，請參閱 [可為 null 的參考](../builtin-types/nullable-reference-types.md)型別。

## <a name="examples"></a>範例

Null 容許運算子的其中一個使用案例是測試引數驗證邏輯。 例如，請參考下列類別：

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

您可以使用 [MSTest 測試架構](../../../core/testing/unit-testing-with-mstest.md)，在函式中針對驗證邏輯建立下列測試：

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

如果沒有容許運算子，編譯器會針對上述程式碼產生下列警告： `Warning CS8625: Cannot convert null literal to non-nullable reference type` 。 藉由使用 null 容許運算子，您會通知編譯器必須傳遞 `null` ，且不應該收到警告。

當您確定運算式不能是， `null` 但編譯器無法管理來辨識該運算式時，您也可以使用 null 容許運算子。 在下列範例中，如果 `IsValid` 方法傳回 `true` ，則其引數不是， `null` 而且您可以安全地取值：

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

如果沒有容許運算子，編譯器會為程式碼產生下列警告 `p.Name` ： `Warning CS8602: Dereference of a possibly null reference` 。

如果您可以修改 `IsValid` 方法，則可以使用 [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) 屬性來通知編譯器，方法的引數 `IsValid` 不能是方法傳回時的參數 `null` `true` ：

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

在上述範例中，您不需要使用 null 容許運算子，因為編譯器有足夠的資訊可以找出 `p` 不能在 `null` 語句內的資訊 `if` 。 如需可讓您提供變數 null 狀態之其他相關資訊的屬性詳細資訊，請參閱 [使用屬性升級 api 來定義 null 的預期](../attributes/nullable-analysis.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[可為 null 之參考](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)型別規格之草稿的[容許運算子](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator)一節。

## <a name="see-also"></a>請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [教學課程：使用可為 null 的參考型別設計](../../tutorials/nullable-reference-types.md)
