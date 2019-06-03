---
title: stackalloc 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 04/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: c72daa58d2fceb05d9cc9c388a9d2e5dbe062796
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422434"
---
# <a name="stackalloc-c-reference"></a>stackalloc (C# 參考)

`stackalloc` 關鍵字是用來在堆疊上配置記憶體區塊。

```csharp
Span<int> block = stackalloc int[100];
```

將已配置的區塊指派至 <xref:System.Span%601?displayName=nameWithType> (而非 `int*`) 可允許在安全區塊中進行堆疊配置。 不需要 `unsafe` 內容。

## <a name="remarks"></a>備註

關鍵字只適用於區域變數初始設定式。 下列程式碼會導致編譯器錯誤。

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

從 C# 7.3 開始，您可以使用 `stackalloc` 陣列的陣列初始設定式語法。 所有下列宣告都會宣告包含三個元素的陣列，且元素的值是整數 `1`、`2` 和 `3`。 第二個初始化會將記憶體指派至 <xref:System.ReadOnlySpan%601>，指出該記憶體無法被修改。

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

涉及指標類型時，`stackalloc` 需要 [unsafe](unsafe.md) 內容。 如需詳細資訊，請參閱[不安全的程式碼和指標](../../programming-guide/unsafe-code-pointers/index.md)。

`stackalloc` 就像 C 執行階段程式庫中的 [_alloca](/cpp/c-runtime-library/reference/alloca)。

## <a name="examples"></a>範例

下列範例會計算並顯示 Fibonacci 序列中的前 20 個數字。 每個數字都是前兩個數字的總和。 在程式碼中，大小足以包含 20 個類型 `int` 的項目的記憶體區塊會配置於堆疊上，而不是堆積。 區塊的位址會儲存在 `Span``fib` 中。 這個記憶體不會進行記憶體回收，因此不需要固定 (使用 [fixed](fixed-statement.md))。 記憶體區塊的存留期只限於定義它的方法的存留期。 傳回方法之前，無法釋放記憶體。

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

下列範例會將 `stackalloc` 整數陣列初始化為位元遮罩，而且每個項目中設定一個位元。 這示範從 C# 7.3 開始提供的新初始設定式語法：

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>安全性

您應該盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601>，因為 unsafe 程式碼比起其他安全的替代內容來說較不安全。 就算在搭配指標使用的情況下，使用 `stackalloc` 會自動啟用通用語言執行平台 (CLR) 中的緩衝區溢位偵測功能。 如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。

## <a name="c-language-specification"></a>C# 語言規格

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [Unsafe 程式碼和指標](../../programming-guide/unsafe-code-pointers/index.md)
