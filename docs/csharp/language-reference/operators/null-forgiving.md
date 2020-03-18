---
title: '! （空寬恕） 運算子 - C# 引用'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 36bfa46cebd2b35c4985dfc23dbe84f8f5dc9201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846289"
---
# <a name="-null-forgiving-operator-c-reference"></a>! （空寬恕） 運算子 （C# 參考）

在 C# 8.0 及更高版本中提供，未`!`修復後運算子是空寬恕運算子。 在啟用[的空注釋上下文中](../../nullable-references.md#nullable-annotation-context)，使用 null 寬容運算子聲明參考型別的運算式`x`不是`null`： `x!`。 一元首碼`!`運算子是[邏輯否定運算子](boolean-logical-operators.md#logical-negation-operator-)。

放棄運算子在運行時不起作用。 它僅通過更改運算式的 null 狀態來影響編譯器的靜態流分析。 在運行時，運算式`x!`計算到基礎運算式`x`的結果。

有關可空參考型別功能的詳細資訊，請參閱[空參考型別](../../nullable-references.md)。

## <a name="examples"></a>範例

null 寬容運算子的一個用例是測試參數驗證邏輯。 例如，請參考下列類別：

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

使用[MSTest 測試框架](../../../core/testing/unit-testing-with-mstest.md)，可以為建構函式中的驗證邏輯創建以下測試：

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

如果沒有 null 寬容運算子，編譯器將生成上述代碼的以下警告： `Warning CS8625: Cannot convert null literal to non-nullable reference type`。 通過使用 null 寬容運算子，您可以通知編譯器傳遞`null`是預期的，不應被警告。

當您肯定知道運算式不能，`null`但編譯器無法識別這一點時，也可以使用 null 寬容運算子。 在下面的示例中，如果`IsValid`方法返回`true`，則其參數不是`null`，您可以安全地取消引用它：

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

如果沒有允許的 null 運算子，編譯器將生成以下`p.Name`代碼警告： `Warning CS8602: Dereference of a possibly null reference`。

如果可以修改方法，`IsValid`則可以使用[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)屬性通知編譯器，當`IsValid`方法返回`null``true`時，該方法的參數不能是 ：

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

在前面的示例中，不需要使用 null 寬容運算子，因為編譯器有足夠的資訊來找出`p`語句`null`中`if`不能包含的資訊。 有關允許您提供有關變數的 null 狀態的其他資訊的屬性的詳細資訊，請參閱[使用屬性升級 API 以定義 null 期望值](../../nullable-attributes.md)。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊，請參閱[空參考型別規範草案](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)的[null 寬容運算子](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator)部分。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [教程：具有空參考型別的設計](../../tutorials/nullable-reference-types.md)
