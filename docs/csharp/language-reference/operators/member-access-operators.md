---
title: 成員存取運算子 - C# 參考
description: 了解可用於存取類型成員的 C# 運算子。
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
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
ms.openlocfilehash: de0715a2ac946fa47f0d83ac8569595e622f0b97
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758079"
---
# <a name="member-access-operators-c-reference"></a>成員存取運算子 (C# 參考)

當您存取類型成員時，可以使用下列運算子：

- [`.` (成員存取)](#member-access-operator-)：可存取命名空間或類型的成員
- [`[]` (陣列項目或索引子存取)](#indexer-operator-)：可存取陣列項目或類型索引子
- [`?.` 和 `?[]` (Null 條件運算子)](#null-conditional-operators--and-)：只有在運算元為非 Null 時，才可執行成員或項目存取作業
- [`()` (引動流程)](#invocation-operator-)：可呼叫存取的方法或叫用委派

## <a name="member-access-operator-"></a>成員存取運算子 .

您會使用 `.` 語彙基元來存取命名空間或類型的成員，如下列範例所示：

- 使用 `.` 來存取命名空間內的巢狀命名空間，如下列 [`using` 指示詞](../keywords/using-directive.md)的範例所示：

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- 使用 `.` 來形成「限定名稱」  以存取命名空間內的類型，如下列程式碼所示：

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  使用 [`using` 指示詞](../keywords/using-directive.md)來使限定名稱的使用為選擇性。

- 使用 `.` 來存取[類型成員](../../programming-guide/classes-and-structs/index.md#members) (靜態及非靜態)，如下列程式碼所示：

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

您也可以使用 `.` 來存取[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。

## <a name="indexer-operator-"></a>索引子運算子 []

中括弧 (`[]`) 通常用於陣列、索引子或指標元素存取。

### <a name="array-access"></a>陣列存取

以下範例將示範如何存取陣列元素：

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

如果陣列索引超出陣列的對應維度界限，就會擲回 <xref:System.IndexOutOfRangeException>。

如上述範例所示，您也會在宣告陣列類型或將陣列執行個體具現化時使用方括弧。

如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。

### <a name="indexer-access"></a>索引子存取

下列範例使用 .NET<xref:System.Collections.Generic.Dictionary%602> 類型示範索引子存取：

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

索引子可讓您透過與陣列編製索引類似的方式，為使用者定義型別的執行個體編製索引。 與必須是整數的陣列索引不同，索引子引數可以宣告為任何類型。

如需索引子的詳細資訊，請參閱[索引子](../../programming-guide/indexers/index.md)。

### <a name="other-usages-of-"></a>[] 的其他用法

如需有關指標元素存取的相關資訊，請參閱[指標相關運算子](pointer-related-operators.md)一文的[指標元素存取運算子 []](pointer-related-operators.md#pointer-element-access-operator-) 一節。

您也可以使用中括弧來指定[屬性](../../programming-guide/concepts/attributes/index.md)：

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Null 條件運算子 ?. 和 ?[]

適用於 C# 6 和更新版本，Null 條件運算子只有在其運算元評估為非 Null 時，才會將成員存取 `?.` 或項目存取 `?[]` 作業套用至該運算元。 如果運算元評估為 `null`，則套用運算子的結果會是 `null`。 Null 條件成員存取運算子 `?.` 也被稱為 Elvis 運算子。

Null 條件運算子會執行最少運算。 換句話說，如果條件式成員或項目存取作業鏈結中的一個作業傳回 `null`，則鏈結的其餘部分不會執行。 在下列範例中，如果 `A` 評估為 `null`，則不會評估 `B`；如果 `A` 或 `B` 評估為 `null`，則不會評估 `C`：

```csharp
A?.B?.Do(C);
A?.B?[C];
```

下列範例示範 `?.` 和 `?[]` 運算子的用法：

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

上述範例也示範 [Null 聯合運算子](null-coalescing-operator.md)的用法。 您可以使用 Null 聯合運算子，在 Null 條件運算的結果為 `null` 時提供用於評估的替代運算式。

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

## <a name="invocation-operator-"></a>引動過程運算子 ()

使用括弧 `()` 來呼叫[方法](../../programming-guide/classes-and-structs/methods.md)或叫用[委派](../../programming-guide/delegates/index.md)。

下列範例示範如何呼叫方法 (使用或不使用引數)，以及叫用委派：

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

當您使用 [`new`](../keywords/new-operator.md) 運算子叫用[建構函式](../../programming-guide/classes-and-structs/constructors.md)時，您也會使用括號。

### <a name="other-usages-of-"></a>() 的其他用法

您也可以使用括號來指定評估運算式中作業的順序。 如需詳細資訊，請參閱[運算子](../../programming-guide/statements-expressions-operators/operators.md)一文的[新增括號](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses)小節。 對於按優先順序層級排序的運算子清單，請參閱 [C# 運算子](index.md)。

叫用轉換運算子的[轉換運算式](invocation-operator.md#cast-expression)也會使用括弧。

## <a name="operator-overloadability"></a>運算子是否可多載

`.` 和 `()` 運算子無法多載。 `[]` 運算子也會視為不可多載的運算子。 請使用[索引子](../../programming-guide/indexers/index.md)以支援使用使用者定義型別編製索引。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [成員存取](~/_csharplang/spec/expressions.md#member-access)
- [項目存取](~/_csharplang/spec/expressions.md#element-access)
- [Null 條件運算子](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [引動流程運算式](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [?? (Null 聯合運算子)](null-coalescing-operator.md)
