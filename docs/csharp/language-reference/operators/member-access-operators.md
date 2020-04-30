---
title: '成員存取運算子和運算式-c # 參考'
description: 了解可用於存取類型成員的 C# 運算子。
ms.date: 04/17/2020
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
ms.openlocfilehash: 86c8cce79e447bee638e1c5c7cb2fdbc64f630f3
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595893"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>成員存取運算子和運算式（c # 參考）

當您存取類型成員時，可以使用下列運算子和運算式：

- （成員存取）：若要存取命名空間或類型的成員[ `.` ](#member-access-expression-)
- [（陣列元素或索引子存取）：用來存取陣列專案或類型索引子`[]` ](#indexer-operator-)
- [和`?[]` null 條件運算子）：只有在運算元不是 null 時，才會執行成員或元素存取`?.` ](#null-conditional-operators--and-)作業。
- （調用）：呼叫存取的方法或叫用委派[ `()` ](#invocation-expression-)
- [（從 end 開始的索引）：表示元素位置是從序列結尾`^` ](#index-from-end-operator-)
- （範圍）：指定可用於取得序列元素範圍的索引範圍[ `..` ](#range-operator-)

## <a name="member-access-expression-"></a>成員存取運算式。

您會使用 `.` 語彙基元來存取命名空間或類型的成員，如下列範例所示：

- 使用`.`來存取命名空間內的嵌套命名空間，如[ `using`下列指示詞](../keywords/using-directive.md)範例所示：

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- 使用 `.` 來形成「限定名稱」** 以存取命名空間內的類型，如下列程式碼所示：

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  使用指示詞，以選擇性地使用限定名稱。 [ `using` ](../keywords/using-directive.md)

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

下列範例會使用 .NET <xref:System.Collections.Generic.Dictionary%602>類型來示範索引子存取：

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

索引子可讓您透過與陣列編製索引類似的方式，為使用者定義型別的執行個體編製索引。 不同于陣列索引（必須是整數），索引子參數可以宣告為任何類型。

如需索引子的詳細資訊，請參閱[索引子](../../programming-guide/indexers/index.md)。

### <a name="other-usages-of-"></a>[] 的其他用法

如需有關指標元素存取的相關資訊，請參閱[指標相關運算子](pointer-related-operators.md)一文的[指標元素存取運算子 []](pointer-related-operators.md#pointer-element-access-operator-) 一節。

您也可以使用中括弧來指定[屬性](../../programming-guide/concepts/attributes/index.md)：

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Null 條件運算子 ?. 和 ?[]

在 c # 6 和更新版本中提供，如果運算元評估為非 null， `?.`則 null 條件運算子只`?[]`會將[成員存取](#member-access-expression-)、或專案[存取](#indexer-operator-)、、作業套用至其運算元;否則，它會`null`傳回。 那是

- 如果`a`評估為`null`， `a?.x`或`a?[x]`的結果為`null`。
- 如果`a`評估為非 null `a?.x` ，或`a?[x]`的結果會分別與`a.x`或`a[x]`的結果相同。

  > [!NOTE]
  > 如果`a.x`或`a[x]`擲回例外狀況`a?.x` ， `a?[x]`或會針對非 null `a`擲回相同的例外狀況。 `a`例如，如果是非 null 陣列實例，而且`x`超出的範圍`a`， `a?[x]`則會擲回。 <xref:System.IndexOutOfRangeException>

Null 條件運算子會執行最少運算。 換句話說，如果條件式成員或項目存取作業鏈結中的一個作業傳回 `null`，則鏈結的其餘部分不會執行。 在下列範例中，如果 `A` 評估為 `null`，則不會評估 `B`；如果 `A` 或 `B` 評估為 `null`，則不會評估 `C`：

```csharp
A?.B?.Do(C);
A?.B?[C];
```

下列範例示範 `?.` 和 `?[]` 運算子的用法：

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

上述範例也會使用[null 聯合運算子`??` ](null-coalescing-operator.md)來指定要評估的替代運算式，以防 null 條件運算的結果為。 `null`

如果`a.x`或`a[x]`屬於不可為 null 的實值型`T`別`a?.x` ， `a?[x]`或為對應的[可為 null 實值型](../builtin-types/nullable-value-types.md) `T?`別。 如果您需要類型`T`為的運算式，請將 null 聯合運算子`??`套用至 null 條件運算式，如下列範例所示：

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

在`??`上述範例中，如果您不使用運算子， `numbers?.Length < 2`則會在`false`為`numbers` `null`時評估為。

Null 條件成員存取運算子 `?.` 也被稱為 Elvis 運算子。

> [!NOTE]
> 在 c # 8 中，null 條件運算子會以非預期的方式與[null 容許運算子](null-forgiving.md)互動。 例如，運算式`x?.y!.z`會剖析為`(x?.y)!.z`。 由於這種轉譯， `z`即使`x`為`null`，也會評估，這可能會導致<xref:System.NullReferenceException>。

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

這是一個安全線程的方法，可確保只會叫用非`handler` null 的。 由於委派實例是不可變的，因此沒有任何執行緒可以變更`handler`區域變數所參考的值。 特別是，如果由另一個執行緒執行的程式碼取消`PropertyChanged`訂閱事件`PropertyChanged` ， `null`並`handler`在叫用之前變成，則`handler`所參考的值將不會受到影響。 `?.`運算子不會多次評估其左邊的運算元，確保在驗證為非 null 之後無法將它`null`變更為。

## <a name="invocation-expression-"></a>調用運算式（）

使用括弧 `()` 來呼叫[方法](../../programming-guide/classes-and-structs/methods.md)或叫用[委派](../../programming-guide/delegates/index.md)。

下列範例示範如何呼叫方法 (使用或不使用引數)，以及叫用委派：

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

當您使用 [`new`](new-operator.md) 運算子叫用[建構函式](../../programming-guide/classes-and-structs/constructors.md)時，您也會使用括號。

### <a name="other-usages-of-"></a>() 的其他用法

您也可以使用括弧來調整評估運算式中作業的順序。 如需詳細資訊，請參閱 [C# 運算子](index.md)。

[Cast 運算式](type-testing-and-cast.md#cast-expression) \(其能執行明確類型轉換\) 也會使用括號。

## <a name="index-from-end-operator-"></a>來自 end 運算子 ^ 的索引

在 c # 8.0 和更新版本中`^`提供，運算子表示從序列結尾的元素位置。 針對長度`length`的序列， `^n`會指向具有從序列開頭位移`length - n`的元素。 例如， `^1`指向序列的最後一個專案，並`^length`指向序列的第一個元素。

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

如上述範例所示，expression `^e`的<xref:System.Index?displayProperty=nameWithType>類型為。 在 expression `^e`中，的結果`e`必須可以隱含地轉換`int`為。

您也可以搭配使用`^`運算子與[範圍運算子](#range-operator-)來建立索引的範圍。 如需詳細資訊，請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。

## <a name="range-operator-"></a>範圍運算子.。

在 c # 8.0 和更新版本中`..`提供，運算子會將索引範圍的開始和結束指定為其運算元。 左側運算元是範圍的*內含*開頭。 右運算元是範圍的*獨佔*結束。 其中一個運算元可以是從序列開頭或結尾的索引，如下列範例所示：

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

如上述範例所示，expression `a..b`的<xref:System.Range?displayProperty=nameWithType>類型為。 在 expression `a..b`中， `a`和`b`的結果必須可以隱含地轉換`int`為<xref:System.Index>或。

您可以省略`..`運算子的任何運算元，以取得開放式結束範圍：

- `a..`相當於`a..^0`
- `..b`相當於`0..b`
- `..`相當於`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

如需詳細資訊，請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

`.`、 `()`、 `^`和`..`運算子無法多載。 `[]` 運算子也會視為不可多載的運算子。 請使用[索引子](../../programming-guide/indexers/index.md)以支援使用使用者定義型別編製索引。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [成員存取](~/_csharplang/spec/expressions.md#member-access)
- [項目存取](~/_csharplang/spec/expressions.md#element-access)
- [Null 條件運算子](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [引動流程運算式](~/_csharplang/spec/expressions.md#invocation-expressions)

如需索引和範圍的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-8.0/ranges.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C # 運算子](index.md)
- [?? (Null 聯合運算子)](null-coalescing-operator.md)
- [:: 運算子](namespace-alias-qualifier.md)
