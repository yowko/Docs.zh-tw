---
title: 成員存取運算子與表示式 - C# 引用
description: 了解可用於存取類型成員的 C# 運算子。
ms.date: 03/31/2020
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: a132e527deadcffb4826c1965987fc09da470a09
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635307"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>成員存取運算子與表示式(C# 引用)

存取類型成員時,可以使用以下運算子和表示式:

- (成員存取):存取命名空間或類型[`.`](#member-access-expression-)的成員
- [(陣列元素或索引器存取): 存取陣列元素或類型`[]`索引器](#indexer-operator-)
- [與`?[]`條件運算子:僅在操作數為非空時執行成員或元素`?.`](#null-conditional-operators--and-)存取操作
- (呼叫) :呼叫被存取的方法或呼[`()`](#invocation-expression-)叫委託
- [(索引從末尾):指示元素位置來自序列的末尾`^`](#index-from-end-operator-)
- (範圍):指定可用於取得序列元素範圍的索引範圍[`..`](#range-operator-)

## <a name="member-access-expression-"></a>成員存取式 .

您會使用 `.` 語彙基元來存取命名空間或類型的成員，如下列範例所示：

- 使用`.`命名空間中的嵌套命名空間,例如[`using`以下指令](../keywords/using-directive.md)範例的範例 :

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- 使用 `.` 來形成「限定名稱」** 以存取命名空間內的類型，如下列程式碼所示：

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  使用[`using`指令](../keywords/using-directive.md)使限定名稱的使用成為可選名稱。

- 使用 `.` 來存取[類型成員](../../programming-guide/classes-and-structs/index.md#members) (靜態及非靜態)，如下列程式碼所示：

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

您也可以使用 `.` 來存取[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。

## <a name="indexer-operator-"></a>索引子運算子 []

中括弧 (`[]`) 通常用於陣列、索引子或指標元素存取。

### <a name="array-access"></a>陣列存取

以下範例將示範如何存取陣列元素：

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

如果陣列索引超出陣列的對應維度界限，就會擲回 <xref:System.IndexOutOfRangeException>。

如上述範例所示，您也會在宣告陣列類型或將陣列執行個體具現化時使用方括弧。

如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。

### <a name="indexer-access"></a>索引子存取

下面的範例使用 .NET<xref:System.Collections.Generic.Dictionary%602>類型來展示索引器存取:

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

索引子可讓您透過與陣列編製索引類似的方式，為使用者定義型別的執行個體編製索引。 與陣列索引(必須整數)不同,索引器參數可以聲明為任何類型的索引器參數。

如需索引子的詳細資訊，請參閱[索引子](../../programming-guide/indexers/index.md)。

### <a name="other-usages-of-"></a>[] 的其他用法

如需有關指標元素存取的相關資訊，請參閱[指標相關運算子](pointer-related-operators.md)一文的[指標元素存取運算子 []](pointer-related-operators.md#pointer-element-access-operator-) 一節。

您也可以使用中括弧來指定[屬性](../../programming-guide/concepts/attributes/index.md)：

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Null 條件運算子 ?. 和 ?[]

在 C# 6 和更高版本中可用,null 條件運算元`?.`僅當該 操作`?[]`數計算為非 null 時,才會將[成員訪問](#member-access-expression-)、或[元素存取](#indexer-operator-)操作應用於其操作數;否則,它將返回`null`。 那是

- 如果`a`計算到`null`,`a?.x``a?[x]`結果`null`為 。
- 如果`a`計算為`a?.x`非空,則`a?[x]`或的結果`a.x`與`a[x]`或的結果相同。

  > [!NOTE]
  > 如果`a.x``a[x]`或引發異常`a?.x`,`a?[x]`或將為非`a`null 引發相同的異常。 例如,`a`如果是非空陣列實體,並且`x`超出的邊界`a`,`a?[x]`則將引發<xref:System.IndexOutOfRangeException>。

Null 條件運算子會執行最少運算。 換句話說，如果條件式成員或項目存取作業鏈結中的一個作業傳回 `null`，則鏈結的其餘部分不會執行。 在下列範例中，如果 `A` 評估為 `null`，則不會評估 `B`；如果 `A` 或 `B` 評估為 `null`，則不會評估 `C`：

```csharp
A?.B?.Do(C);
A?.B?[C];
```

下列範例示範 `?.` 和 `?[]` 運算子的用法：

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

前面的範例還使用[null 合併運算`??`符](null-coalescing-operator.md)指定一個替代運算式,以計算 null`null`條件操作的結果為 時計算的運算式。

如果`a.x``a[x]`或非空數型態`T``a?.x`,`a?[x]`或是一個[非空白型態 。](../builtin-types/nullable-value-types.md)`T?` 如果需要類型`T`表示式,請將空合併運算子`??`應用於 null 條件表示式,如下例所示:

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

在`??`前面的範例中,如果不使用運算子,請`numbers?.Length < 2`計算到`false`時`numbers`為`null`。

Null 條件成員存取運算子 `?.` 也被稱為 Elvis 運算子。

### <a name="thread-safe-delegate-invocation"></a>安全執行緒委派引動流程

使用 `?.` 運算子來檢查委派是否為非 Null，然後以安全執行緒方式叫用它 (例如當您[引發事件](../../../standard/events/how-to-raise-and-consume-events.md)時)，如下列程式碼所示：

```csharp
PropertyChanged?.Invoke(…)
```

該程式碼等同於您用於 C# 5 或舊版的下列程式碼：

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a>呼叫表示式 ()

使用括弧 `()` 來呼叫[方法](../../programming-guide/classes-and-structs/methods.md)或叫用[委派](../../programming-guide/delegates/index.md)。

下列範例示範如何呼叫方法 (使用或不使用引數)，以及叫用委派：

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

當您使用 [`new`](new-operator.md) 運算子叫用[建構函式](../../programming-guide/classes-and-structs/constructors.md)時，您也會使用括號。

### <a name="other-usages-of-"></a>() 的其他用法

您也可以使用括弧來調整評估運算式中作業的順序。 如需詳細資訊，請參閱 [C# 運算子](index.md)。

[Cast 運算式](type-testing-and-cast.md#cast-operator-) \(其能執行明確類型轉換\) 也會使用括號。

## <a name="index-from-end-operator-"></a>來自終端運算子索引 |

在 C# 8.0`^`及更高 版本中可用,運算符指示序列末尾的元素位置。 對於長度`length`序列`^n`, 指向具有序列開頭`length - n`偏移 的元素。 例如,`^1`指向序列的最後一個元素,`^length`並指向序列的第一個元素。

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

如前面的示例所示,表達式`^e`是類型<xref:System.Index?displayProperty=nameWithType>。 在表示式`^e`中,必須`e`將的結果隱式轉換`int`為 。

您還可以使用運算子`^`與[範圍運算子](#range-operator-)一起建立一系列索引。 有關詳細資訊,請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。

## <a name="range-operator-"></a>範圍運算子 ..

在 C# 8.0`..`及更高 版本中提供,運算符指定一系列索引的開始和結束作為其操作數。 左側操作數是範圍的*包容性*開始。 右側操作數是範圍的*獨佔*端。 其中任一操作數可以是序列開頭或末尾的索引,如下例所示:

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

如前面的示例所示,表達式`a..b`是類型<xref:System.Range?displayProperty=nameWithType>。 在表示式`a..b`中,`a``b`與 的結果必須隱式`int`<xref:System.Index>轉換為 或 。

您可以省略`..`運算子的任何操作數以取得開放式範圍:

- `a..`等效於`a..^0`
- `..b`等效於`0..b`
- `..`等效於`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

有關詳細資訊,請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

不能`.``()`重`^`載`..`、 和運算子。 `[]` 運算子也會視為不可多載的運算子。 請使用[索引子](../../programming-guide/indexers/index.md)以支援使用使用者定義型別編製索引。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [成員存取](~/_csharplang/spec/expressions.md#member-access)
- [項目存取](~/_csharplang/spec/expressions.md#element-access)
- [Null 條件運算子](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [引動流程運算式](~/_csharplang/spec/expressions.md#invocation-expressions)

有關索引和範圍的詳細資訊,請參閱[功能建議註釋](~/_csharplang/proposals/csharp-8.0/ranges.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [?? (Null 聯合運算子)](null-coalescing-operator.md)
- [:: 運算子](namespace-alias-qualifier.md)
