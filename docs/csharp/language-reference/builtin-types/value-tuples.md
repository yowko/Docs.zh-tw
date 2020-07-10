---
title: '元組類型-c # 參考'
description: '瞭解 c # 元組：輕量資料結構，可用來將鬆散相關的資料元素分組'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: 3d79ab19117847e2364b154db33a1521416bb3f4
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174986"
---
# <a name="tuple-types-c-reference"></a>元組類型 (c # 參考) 

在 c # 7.0 和更新版本中提供，*元組*功能提供精簡的語法，將多個資料元素群組在輕量資料結構中。 下列範例會示範如何宣告元組變數、將它初始化，以及存取其資料成員：

[!code-csharp-interactive[tuple intro](snippets/ValueTuples.cs#Introduction)]

如上述範例所示，若要定義元組類型，您可以指定其所有資料成員的類型，以及（選擇性地）[功能變數名稱](#tuple-field-names)。 您不能在元組類型中定義方法，但是可以使用 .NET 所提供的方法，如下列範例所示：

[!code-csharp-interactive[tuple methods](snippets/ValueTuples.cs#MethodOnTuples)]

從 c # 7.3 開始，元組類型支援[等號比較運算子](../operators/equality-operators.md) `==` 和 `!=` 。 如需詳細資訊，請參閱「[元組相等](#tuple-equality)」一節。

元組類型為實[數值型別](value-types.md);元組元素是公用欄位。 這可讓元組*可變*的實值型別。

> [!NOTE]
> 元組功能需要 <xref:System.ValueTuple?displayProperty=nameWithType> 類型和相關的泛型型別 (例如， <xref:System.ValueTuple%602?displayProperty=nameWithType>) ，這在 .net Core 和 .NET Framework 4.7 和更新版本中都有提供。 若要在以 .NET Framework 4.6.2 或更早版本為目標的專案中使用元組，請將 NuGet 套件新增 [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) 至專案。

您可以定義具有任意大量元素的元組：

[!code-csharp-interactive[large tuple](snippets/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a>元組的使用案例

元組最常見的其中一個使用案例是做為方法傳回型別。 也就是說，您可以將方法結果群組在元組傳回型別中，而不是定義[ `out` 方法參數](../keywords/out-parameter-modifier.md)，如下列範例所示：

[!code-csharp-interactive[multiple method outputs](snippets/ValueTuples.cs#MultipleReturns)]

如上述範例所示，您可以直接使用傳回的元組實例，或在不同的變數中[解構](#tuple-assignment-and-deconstruction)它。

您也可以使用元組類型，而不是[匿名型別](../../programming-guide/classes-and-structs/anonymous-types.md)。例如，在 LINQ 查詢中。 如需詳細資訊，請參閱[在匿名和元組類型之間選擇](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)。

一般而言，您會使用元組來分組鬆散相關的資料元素。 這通常在私用和內部公用程式方法中很有用。 在公用 API 的案例中，請考慮定義[類別](../keywords/class.md)或[結構](struct.md)類型。

## <a name="tuple-field-names"></a>元組功能變數名稱

您可以在元組初始化運算式中或在元組類型的定義中，明確地指定元組欄位的名稱，如下列範例所示：

[!code-csharp-interactive[explicit field names](snippets/ValueTuples.cs#ExplicitFieldNames)]

從 c # 7.1 開始，如果您未指定功能變數名稱，則可能會從元組初始化運算式中對應變數的名稱推斷，如下列範例所示：

[!code-csharp-interactive[inferred field names](snippets/ValueTuples.cs#InferFieldNames)]

這就是所謂的「元組投影初始化運算式」。 在下列情況中，不會將變數的名稱投射到元組功能變數名稱：

- 候選名稱是元組類型的成員名稱，例如、 `Item3` `ToString` 或 `Rest` 。
- 候選名稱是另一個元組功能變數名稱的複本，不論是明確或隱含。

在這些情況下，您可以明確地指定欄位的名稱，或依預設名稱存取欄位。

元組欄位的預設名稱是 `Item1` 、 `Item2` 等等 `Item3` 。 您可以一律使用欄位的預設名稱，即使是明確指定或推斷功能變數名稱，如下列範例所示：

[!code-csharp-interactive[default field names](snippets/ValueTuples.cs#DefaultFieldNames)]

[元組指派](#tuple-assignment-and-deconstruction)和[元組相等比較](#tuple-equality)不會將功能變數名稱納入考慮。

在編譯時期，編譯器會以對應的預設名稱取代非預設的功能變數名稱。 因此，在執行時間無法使用明確指定或推斷的功能變數名稱。

## <a name="tuple-assignment-and-deconstruction"></a>元組指派和解構

C # 支援在符合下列兩個條件的元組類型之間指派：

- 這兩個元組類型具有相同數目的元素
- 針對每個元組位置，右側元組元素的類型與或隱含轉換成對應的左側元組元素的類型相同。

元組元素值會依照元組元素的順序指派。 元組欄位的名稱會被忽略，而且不會指派，如下列範例所示：

[!code-csharp-interactive[tuple assignment](snippets/ValueTuples.cs#Assignment)]

您也可以使用指派運算子 `=` ，在不同的變數中*解構*元組實例。 您可以透過下列其中一種方式來執行此動作：

- 在括弧內明確宣告每個變數的類型：

  [!code-csharp-interactive[specify types of variables](snippets/ValueTuples.cs#DeconstructExplicit)]

- 使用 `var` 括弧外的關鍵字來宣告隱含類型的變數，並讓編譯器推斷其類型：

  [!code-csharp-interactive[implicitly typed variables](snippets/ValueTuples.cs#DeconstructVar)]

- 使用現有的變數：

  [!code-csharp-interactive[existing variables](snippets/ValueTuples.cs#DeconstructExisting)]

如需解構元組和其他類型的詳細資訊，請參閱[解構元組和其他類型](../../deconstruct.md)。

## <a name="tuple-equality"></a>元組相等

從 C# 7.3 開始，Tuple 型別支援 `==` 和 `!=` 運算子。 這些運算子會比較左邊運算元的成員與右運算元的對應成員，遵循元組元素的順序。

[!code-csharp-interactive[tuple equality](snippets/ValueTuples.cs#TupleEquality)]

如上述範例所示， `==` 和 `!=` 作業並不會將元組功能變數名稱納入考慮。

滿足下列兩個條件時，兩個元組可比較：

- 這兩個元組都有相同數目的元素。 例如， `t1 != t2` 如果 `t1` 和 `t2` 具有不同數目的元素，則不會編譯。
- 針對每個元組位置，左側和右側元組運算元中的對應元素可與 `==` 和 `!=` 運算子比較。 例如，不會 `(1, (2, 3)) == ((1, 2), 3)` 編譯，因為 `1` 無法與比較 `(1, 2)` 。

`==`和 `!=` 運算子會以較低的方式比較元組。 也就是說，當作業符合一對不相等的元素或達到元組的結尾時，作業就會停止。 不過，在進行任何比較之前，會評估*所有*的元組元素，如下列範例所示：

[!code-csharp-interactive[tuple element evaluation](snippets/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a>元組當做 out 參數

通常，您會將具有[ `out` 參數](../keywords/out-parameter-modifier.md)的方法重構為傳回元組的方法。 不過，在某些情況下， `out` 參數可以是元組類型。 下列範例顯示如何使用元組作為 `out` 參數：

[!code-csharp-interactive[tuple as out parameter](snippets/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a>元組 vs`System.Tuple`

以類型支援的 c # 元組 <xref:System.ValueTuple?displayProperty=nameWithType> ，與以類型代表的元組不同 <xref:System.Tuple?displayProperty=nameWithType> 。 主要的差異如下：

- `ValueTuple`類型是實[數值型別](value-types.md)。 `Tuple`類型是[參考型別](../keywords/reference-types.md)。
- `ValueTuple`類型是可變動的。 `Tuple`類型是不可變的。
- 類型的資料成員 `ValueTuple` 是欄位。 類型的資料成員 `Tuple` 為屬性。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱下列功能建議事項：

- [ (也要推斷元組名。元組投影初始化運算式) ](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [支援 `==` `!=` 元組類型的和](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [實值型別](value-types.md)
- [在匿名和元組類型之間選擇](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
