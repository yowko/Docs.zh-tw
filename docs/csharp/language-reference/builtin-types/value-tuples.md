---
title: '元組類型-c # 參考'
description: '深入瞭解 c # 元組：可用來將鬆散相關的資料元素分組的輕量資料結構'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: d996c7afecba1b58bfd8337fa444fd71790dd482
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471768"
---
# <a name="tuple-types-c-reference"></a>元組類型 (c # 參考) 

在 c # 7.0 和更新版本中提供， *元組* 功能提供簡潔的語法，以將輕量資料結構中的多個資料元素群組在一起。 下列範例會示範如何宣告元組變數、將它初始化，以及存取其資料成員：

[!code-csharp-interactive[tuple intro](snippets/shared/ValueTuples.cs#Introduction)]

如先前的範例所示，若要定義元組類型，請指定其所有資料成員的類型，並選擇性地指定 [功能變數名稱](#tuple-field-names)。 您無法在元組類型中定義方法，但您可以使用 .NET 提供的方法，如下列範例所示：

[!code-csharp-interactive[tuple methods](snippets/shared/ValueTuples.cs#MethodOnTuples)]

從 c # 7.3 開始，元組類型支援 [等號比較運算子](../operators/equality-operators.md) `==` 和 `!=` 。 如需詳細資訊，請參閱 [元組相等](#tuple-equality) 區段。

元組類型為實 [數值型別](value-types.md);元組元素為公用欄位。 這會讓元組 *可變* 的實值型別。

> [!NOTE]
> 元組功能需要 <xref:System.ValueTuple?displayProperty=nameWithType> 類型和相關的泛型型別 (例如， <xref:System.ValueTuple%602?displayProperty=nameWithType>) ，可在 .net Core 和 .NET Framework 4.7 和更新版本中使用。 若要在以 .NET Framework 4.6.2 或更早版本為目標的專案中使用元組，請將 NuGet 套件新增 [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) 至專案。

您可以定義具有任意大量元素的元組：

[!code-csharp-interactive[large tuple](snippets/shared/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a>元組的使用案例

元組最常見的其中一個使用案例是做為方法傳回型別。 也就是說，您可以將方法結果分組為元組傳回型別，而不是定義[ `out` 方法參數](../keywords/out-parameter-modifier.md)，如下列範例所示：

[!code-csharp-interactive[multiple method outputs](snippets/shared/ValueTuples.cs#MultipleReturns)]

如先前的範例所示，您可以直接使用傳回的元組實例，或在不同的變數中 [解構](#tuple-assignment-and-deconstruction) 它。

您也可以使用元組類型，而不是 [匿名型別](../../programming-guide/classes-and-structs/anonymous-types.md);例如，在 LINQ 查詢中。 如需詳細資訊，請參閱 [在匿名和元組類型之間選擇](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)。

一般而言，您會使用元組來分組鬆散相關的資料元素。 這在私用和內部公用程式方法中通常很有用。 在公用 API 的情況下，請考慮定義 [類別](../keywords/class.md) 或 [結構](struct.md) 類型。

## <a name="tuple-field-names"></a>元組功能變數名稱

您可以在元組初始化運算式或元組類型的定義中，明確指定元組欄位的名稱，如下列範例所示：

[!code-csharp-interactive[explicit field names](snippets/shared/ValueTuples.cs#ExplicitFieldNames)]

從 c # 7.1 開始，如果您未指定功能變數名稱，它可能會從元組初始化運算式中對應的變數名稱推斷，如下列範例所示：

[!code-csharp-interactive[inferred field names](snippets/shared/ValueTuples.cs#InferFieldNames)]

這就是所謂的元組投影初始化運算式。 在下列情況中，不會將變數的名稱投射到元組功能變數名稱：

- 候選名稱是元組類型的成員名稱，例如、 `Item3` `ToString` 或 `Rest` 。
- 候選名稱是另一個元組功能變數名稱（明確或隱含）的複本。

在這些情況下，您可以明確指定欄位的名稱，或依預設名稱存取欄位。

元組欄位的預設名稱是 `Item1` 、 `Item2` 等等 `Item3` 。 您一律可以使用欄位的預設名稱，即使是明確或推斷的功能變數名稱，如下列範例所示：

[!code-csharp-interactive[default field names](snippets/shared/ValueTuples.cs#DefaultFieldNames)]

[元組指派](#tuple-assignment-and-deconstruction) 和 [元組相等比較](#tuple-equality) 不會將欄位名稱列入考慮。

在編譯時期，編譯器會以對應的預設名稱取代非預設的功能變數名稱。 因此，在執行時間無法使用明確指定或推斷的欄位名稱。

## <a name="tuple-assignment-and-deconstruction"></a>元組指派和解構

C # 支援在符合下列兩個條件的元組類型之間進行指派：

- 這兩個元組類型都有相同數目的元素
- 針對每個元組位置，右邊元組專案的型別會與或隱含轉換成對應的左邊元組元素類型。

元組元素值會依照元組專案的順序指派。 元組欄位的名稱會被忽略且未指派，如下列範例所示：

[!code-csharp-interactive[tuple assignment](snippets/shared/ValueTuples.cs#Assignment)]

您也可以使用指派運算子 `=` ，在不同的變數中 *解構* 元組實例。 您可以透過下列其中一種方式來執行此動作：

- 在括弧內明確宣告每個變數的類型：

  [!code-csharp-interactive[specify types of variables](snippets/shared/ValueTuples.cs#DeconstructExplicit)]

- 使用 `var` 括弧外的關鍵字宣告隱含型別變數，並讓編譯器推斷其類型：

  [!code-csharp-interactive[implicitly typed variables](snippets/shared/ValueTuples.cs#DeconstructVar)]

- 使用現有的變數：

  [!code-csharp-interactive[existing variables](snippets/shared/ValueTuples.cs#DeconstructExisting)]

如需解構元組和其他類型的詳細資訊，請參閱 [解構元組和其他類型](../../deconstruct.md)。

## <a name="tuple-equality"></a>元組相等

從 C# 7.3 開始，Tuple 型別支援 `==` 和 `!=` 運算子。 這些運算子會比較左邊運算元的成員與右邊運算元的對應成員（依照元組元素的順序）。

[!code-csharp-interactive[tuple equality](snippets/shared/ValueTuples.cs#TupleEquality)]

如先前的範例所示， `==` 和 `!=` 作業不會考慮元組功能變數名稱。

當滿足下列兩個條件時，可以比較兩個元組：

- 這兩個元組都有相同數目的元素。 例如， `t1 != t2` 如果 `t1` 和 `t2` 具有不同數目的元素，則不會編譯。
- 針對每個元組位置，左側和右邊元組運算元中的對應元素可與 `==` 和 `!=` 運算子比較。 例如，不會進行 `(1, (2, 3)) == ((1, 2), 3)` 編譯，因為 `1` 無法比較 `(1, 2)` 。

和運算子會以最少運算 `==` `!=` 的方式比較元組。 也就是說，當作業符合一對不相等的元素或達到元組的結尾時，就會停止作業。 不過，在進行任何比較之前，會評估 *所有* 元組元素，如下列範例所示：

[!code-csharp-interactive[tuple element evaluation](snippets/shared/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a>元組作為 out 參數

通常，您會將具有[ `out` 參數](../keywords/out-parameter-modifier.md)的方法重構為傳回元組的方法。 不過，在某些情況下， `out` 參數可以是元組類型。 下列範例顯示如何使用元組作為 `out` 參數：

[!code-csharp-interactive[tuple as out parameter](snippets/shared/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a>元組與 `System.Tuple`

由型別所支援的 c # 元組， <xref:System.ValueTuple?displayProperty=nameWithType> 與以類型表示的元組不同 <xref:System.Tuple?displayProperty=nameWithType> 。 主要的差異如下：

- `ValueTuple` 類型是實 [數值型別](value-types.md)。 `Tuple` 類型為 [參考型別](../keywords/reference-types.md)。
- `ValueTuple` 類型是可變動的。 `Tuple` 類型是不可變的。
- 類型的資料成員 `ValueTuple` 為欄位。 類型的資料成員 `Tuple` 為屬性。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱下列功能提案附注：

- [ (也會推斷元組名。元組投影初始化運算式) ](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [對 `==` `!=` 元組類型的支援](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [值類型](value-types.md)
- [在匿名和元組類型之間選擇](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
