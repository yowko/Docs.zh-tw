---
title: '[] 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 948ce238058307631cf0e5a7a5e3d72664233052
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333391"
---
# <a name="-operator-c-reference"></a>[] 運算子 (C# 參考)

中括弧 (`[]`) 通常用於陣列、索引子或指標元素存取。

如需指標元素存取的詳細資訊，請參閱[如何：使用指標存取陣列元素](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md)。

您也可以使用中括弧來指定[屬性](../../programming-guide/concepts/attributes/index.md)：

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a>陣列存取

以下範例將示範如何存取陣列元素：

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

如果陣列索引超出陣列的對應維度界限，就會擲回 <xref:System.IndexOutOfRangeException>。

如上述範例所示，您也會在陣列類型的宣告和陣列執行個體的具現化中使用方括弧。

如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。

## <a name="indexer-access"></a>索引子存取

下列範例使用 .NET<xref:System.Collections.Generic.Dictionary%602> 類型示範索引子存取：

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

索引子可讓您透過與陣列編製索引類似的方式，為使用者定義型別的執行個體編製索引。 與必須是整數的陣列索引不同，索引子引數可以宣告為任何類型。

如需索引子的詳細資訊，請參閱[索引子](../../programming-guide/indexers/index.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

元素存取 `[]` 不是可多載的運算子。 請使用[索引子](../../programming-guide/indexers/index.md)以支援使用使用者定義型別編製索引。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[元素存取](~/_csharplang/spec/expressions.md#element-access)和[指標元素存取](~/_csharplang/spec/unsafe-code.md#pointer-element-access)小節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [陣列](../../programming-guide/arrays/index.md)
- [索引子](../../programming-guide/indexers/index.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [屬性](../../programming-guide/concepts/attributes/index.md)