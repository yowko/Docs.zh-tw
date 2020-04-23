---
title: '! (空寬恕) 運算子 - C# 參考'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: f3d06dec42ba117cd30dbf4d05fa4a6f594e57e5
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82101967"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (空寬恕) 運算子 (C# 參考)

在 C# 8.0 及更高版本中`!`提供,未修復後運算符是空寬恕運算符。 開啟[的空註解中](../../nullable-references.md#nullable-annotation-context), 使用 null 寬容運算符宣告的表示式`x`不是`null`: `x!`。 一元前置字`!`元是[邏輯否定運算子](boolean-logical-operators.md#logical-negation-operator-)。

放棄運算符在運行時不起作用。 它僅透過更改表達式的 null 狀態來影響編譯器的靜態流分析。 在運行時,表達式`x!`計算到基礎表達`x`式 的結果。

有關可空引用類型功能的詳細資訊,請參考[空參考類型](../builtin-types/nullable-reference-types.md)。

## <a name="examples"></a>範例

null 寬容運算子的一個用例是測試參數驗證邏輯。 例如，請參考下列類別：

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

使用[MSTest 測試框架](../../../core/testing/unit-testing-with-mstest.md),可以為建構函式中的驗證邏輯建立以下測試:

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

如果沒有 null 寬容運算子,編譯器將產生上述代碼的以下警告: `Warning CS8625: Cannot convert null literal to non-nullable reference type`。 通過使用 null 寬容運算符,您可以通知編譯器傳遞`null`是預期的,不應被警告。

當您肯定知道表示式不能,`null`但編譯器無法識別這一點時,也可以使用 null 寬容運算符。 在下面的範例中,如果`IsValid`方法傳`true`回 ,則其`null`參數不是 ,您可以安全地取消引用它:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

如果沒有允許的 null 運算子,編譯器將產生`p.Name`以下 代碼`Warning CS8602: Dereference of a possibly null reference`警告: 。

如果可以修改方法,`IsValid`則可以使用[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)屬性通知編譯`IsValid`器,`null``true`當方法傳回 時,該方法的參數不能是 :

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

在前面的範例中,不需要使用 null 寬容運算符,因為編譯器有足夠的資訊來找出`p`語句`null``if`中 不能包含的資訊。 有關允許您提供有關變數的 null 狀態的其他資訊的屬性的詳細資訊,請參閱[使用屬性升級 API 以定義 null 期望值](../attributes/nullable-analysis.md)。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊,請參閱[空引用類型規範草案](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)的[null 寬容運算元](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator)部分。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [教學:具有空引言類型的設計](../../tutorials/nullable-reference-types.md)
