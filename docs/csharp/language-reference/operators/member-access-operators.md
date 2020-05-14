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
ms.openlocfilehash: 59e01b17d78032714803629d503a92ba86a20fdc
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394646"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>成員存取運算子和運算式（c # 參考）

當您存取類型成員時，可以使用下列運算子和運算式：

- [ `.` （成員存取）](#member-access-expression-)：若要存取命名空間或類型的成員
- [ `[]` （陣列元素或索引子存取）](#indexer-operator-)：用來存取陣列專案或類型索引子
- [ `?.` 和 `?[]` （null 條件運算子）](#null-conditional-operators--and-)：只有在運算元不是 null 時，才會執行成員或元素存取作業。
- [ `()` （調用）](#invocation-expression-)：呼叫存取的方法或叫用委派
- [ `^` （從 end 開始的索引）](#index-from-end-operator-)：表示元素位置是從序列結尾
- [ `..` （範圍）](#range-operator-)：指定可用於取得序列元素範圍的索引範圍

## <a name="member-access-expression-"></a>成員存取運算式。

您會使用 `.` 語彙基元來存取命名空間或類型的成員，如下列範例所示：

- 使用 `.` 來存取命名空間內的嵌套命名空間，如下列指示詞範例[ `using` ](../keywords/using-directive.md)所示：

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- 使用 `.` 來形成「限定名稱」** 以存取命名空間內的類型，如下列程式碼所示：

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  使用指示詞[，以選擇性 `using` ](../keywords/using-directive.md)地使用限定名稱。

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

下列範例會使用 .NET <xref:System.Collections.Generic.Dictionary%602> 類型來示範索引子存取：

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

在 c # 6 和更新版本中提供，如果運算元評估為非 null，則 null 條件運算子只會將[成員存取](#member-access-expression-)、 `?.` 或專案[存取](#indexer-operator-)、、作業套用 `?[]` 至其運算元，否則會傳回 `null` 。 那是

- 如果 `a` 評估為 `null` ，或的結果 `a?.x` `a?[x]` 為 `null` 。
- 如果 `a` 評估為非 null，或的結果 `a?.x` `a?[x]` 會分別與或的結果相同 `a.x` `a[x]` 。

  > [!NOTE]
  > 如果 `a.x` 或 `a[x]` 擲回例外狀況， `a?.x` 或 `a?[x]` 會針對非 null 擲回相同的例外狀況 `a` 。 例如，如果 `a` 是非 null 陣列實例，而且超出的 `x` 範圍 `a` ，則 `a?[x]` 會擲回 <xref:System.IndexOutOfRangeException> 。

Null 條件運算子會執行最少運算。 換句話說，如果條件式成員或項目存取作業鏈結中的一個作業傳回 `null`，則鏈結的其餘部分不會執行。 在下列範例中，如果 `A` 評估為 `null`，則不會評估 `B`；如果 `A` 或 `B` 評估為 `null`，則不會評估 `C`：

```csharp
A?.B?.Do(C);
A?.B?[C];
```

下列範例示範 `?.` 和 `?[]` 運算子的用法：

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

上述範例也會使用[null 聯合運算子 `??` ](null-coalescing-operator.md)來指定要評估的替代運算式，以防 null 條件運算的結果為 `null` 。

如果 `a.x` 或 `a[x]` 屬於不可為 null 的實值型別 `T` ， `a?.x` 或 `a?[x]` 為對應的[可為 null 實值型](../builtin-types/nullable-value-types.md)別 `T?` 。 如果您需要類型為的運算式 `T` ，請將 null 聯合運算子套用 `??` 至 null 條件運算式，如下列範例所示：

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

在上述範例中，如果您不使用 `??` 運算子，則 `numbers?.Length < 2` 會在 `false` 為時評估為 `numbers` `null` 。

Null 條件成員存取運算子 `?.` 也被稱為 Elvis 運算子。

> [!NOTE]
> 在 c # 8 中， [null 容許運算子](null-forgiving.md)會終止前面的 null 條件運算清單。 例如，運算式會剖析 `x?.y!.z` 為 `(x?.y)!.z` 。 由於這種轉譯， `z` 即使為，也會評估， `x` `null` 這可能會導致 <xref:System.NullReferenceException> 。

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

這是一個安全線程的方法，可確保只會叫用非 null 的 `handler` 。 由於委派實例是不可變的，因此沒有任何執行緒可以變更區域變數所參考的物件 `handler` 。 特別是，如果由另一個執行緒執行的程式碼取消訂閱事件，並在叫用 `PropertyChanged` `PropertyChanged` `null` 之前變成 `handler` ，則所參考的物件將不會 `handler` 受到影響。 `?.`運算子不會多次評估其左邊的運算元，確保在 `null` 驗證為非 null 之後無法將它變更為。

## <a name="invocation-expression-"></a>調用運算式（）

使用括弧 `()` 來呼叫[方法](../../programming-guide/classes-and-structs/methods.md)或叫用[委派](../../programming-guide/delegates/index.md)。

下列範例示範如何呼叫方法 (使用或不使用引數)，以及叫用委派：

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

當您使用 [`new`](new-operator.md) 運算子叫用[建構函式](../../programming-guide/classes-and-structs/constructors.md)時，您也會使用括號。

### <a name="other-usages-of-"></a>() 的其他用法

您也可以使用括弧來調整評估運算式中作業的順序。 如需詳細資訊，請參閱 [C# 運算子](index.md)。

[Cast 運算式](type-testing-and-cast.md#cast-expression) \(其能執行明確類型轉換\) 也會使用括號。

## <a name="index-from-end-operator-"></a>來自 end 運算子 ^ 的索引

在 c # 8.0 和更新版本中提供， `^` 運算子表示從序列結尾的元素位置。 針對長度的序列 `length` ，會 `^n` 指向具有 `length - n` 從序列開頭位移的元素。 例如， `^1` 指向序列的最後一個專案，並 `^length` 指向序列的第一個元素。

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

如上述範例所示，expression 的 `^e` 類型為 <xref:System.Index?displayProperty=nameWithType> 。 在 expression 中 `^e` ，的結果 `e` 必須可以隱含地轉換為 `int` 。

您也可以搭配使用 `^` 運算子與[範圍運算子](#range-operator-)來建立索引的範圍。 如需詳細資訊，請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。

## <a name="range-operator-"></a>範圍運算子.。

在 c # 8.0 和更新版本中提供，運算子會將 `..` 索引範圍的開始和結束指定為其運算元。 左側運算元是範圍的*內含*開頭。 右運算元是範圍的*獨佔*結束。 其中一個運算元可以是從序列開頭或結尾的索引，如下列範例所示：

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

如上述範例所示，expression 的 `a..b` 類型為 <xref:System.Range?displayProperty=nameWithType> 。 在 expression 中 `a..b` ，和的 `a` 結果 `b` 必須可以隱含地轉換為 `int` 或 <xref:System.Index> 。

您可以省略運算子的任何運算元 `..` ，以取得開放式結束範圍：

- `a..`相當於`a..^0`
- `..b`相當於`0..b`
- `..`相當於`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

如需詳細資訊，請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

`.`、 `()` 、 `^` 和 `..` 運算子無法多載。 `[]` 運算子也會視為不可多載的運算子。 請使用[索引子](../../programming-guide/indexers/index.md)以支援使用使用者定義型別編製索引。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [成員存取](~/_csharplang/spec/expressions.md#member-access)
- [項目存取](~/_csharplang/spec/expressions.md#element-access)
- [Null 條件運算子](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [引動流程運算式](~/_csharplang/spec/expressions.md#invocation-expressions)

如需索引和範圍的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-8.0/ranges.md)。

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C # 運算子](index.md)
- [?? (Null 聯合運算子)](null-coalescing-operator.md)
- [:: 運算子](namespace-alias-qualifier.md)
