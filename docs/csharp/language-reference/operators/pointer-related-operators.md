---
title: 指標相關運算子 - C# 參考
description: 了解使用指標時您可以使用的 C# 運算子。
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 03d6ed19ef01be7712ff2fdde0c1be2a6673e64f
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401436"
---
# <a name="pointer-related-operators-c-reference"></a>指標相關運算子 (C# 參考)

您可以搭配下列運算子來使用指標：

- 一元 [`&` (傳址)](#address-of-operator-) 運算子：取得變數位址
- 一元 [`*` (指標間接)](#pointer-indirection-operator-) 運算子：取得指標指向的變數
- [`->` (成員存取)](#pointer-member-access-operator--) 和 [`[]` (元素存取)](#pointer-element-access-operator-) 運算子
- 算術運算子 [`+`、`-`、`++` 和 `--`](#pointer-arithmetic-operators)
- 比較運算子 [`==`、`!=`、`<`、`>`、`<=` 和 `>=`](#pointer-comparison-operators)

如需指標型別的資訊，請參閱[指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)。

> [!NOTE]
> 任何具有指標的作業都需要 [unsafe](../keywords/unsafe.md) 內容。 包含 unsafe 區塊的程式碼必須使用 [`-unsafe`](../compiler-options/unsafe-compiler-option.md) 編譯器選項編譯。

## <a name="address-of-operator-"></a> 傳址運算子 &amp;

一元 `&` 運算子會傳回其運算元的位址：

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

`&` 運算子的運算元必須是固定的變數。 「固定」  變數是位在不受[記憶體回收行程](../../../standard/garbage-collection/index.md)作業影響之儲存位置的變數。 在前述範例中，區域變數 `number` 是固定的變數，因為它位於堆疊上。 會受到記憶體回收行程影響且位在儲存位置的變數 (例如重新配置)，稱為「可移動」  變數。 物件欄位和陣列元素是可移動變數的範例。 如果以 [fixed](../keywords/fixed-statement.md) 陳述式來「修正」或「釘選」它，則您可取得可移動變數的位址。 取得的地址僅在 `fixed` 陳述式區塊持續期間有效。 下例顯示如何使用 `fixed` 陳述式和 `&` 運算子：

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

您無法取得常數或值的位址。

如需固定和可移動變數的詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[固定和可移動變數](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)一節。

二元 `&` 運算子會計算其布林運算元的[邏輯 AND](boolean-logical-operators.md#logical-and-operator-)或其整數運算元的[位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-)。

## <a name="pointer-indirection-operator-"></a>指標間接運算子 *

一元指標間接運算子 `*` 取得其運算元指向的變數。 它也稱之為取值運算子。 `*` 運算子的運算元必須是指標型別。

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

您不能將 `*` 運算子套用至 `void*` 型別的運算式。

二元 `*` 運算子會計算其數值運算元的[乘積](arithmetic-operators.md#multiplication-operator-)。

## <a name="pointer-member-access-operator--"></a>指標成員存取運算子 ->

`->` 運算子結合[指標間接](#pointer-indirection-operator-)和[成員存取](member-access-operators.md#member-access-operator-)。 亦即，如果 `x` 是 `T*` 型別的指標，而 `y` 是 `T` 的可存取成員，則運算式格式為

```csharp
x->y
```

相當於

```csharp
(*x).y
```

下列範例示範 `->` 運算子的用法：

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

您不能將 `->` 運算子套用至 `void*` 型別的運算式。

## <a name="pointer-element-access-operator-"></a>指標元素存取運算子 []

針對指標型別的運算式 `p`，`p[n]` 格式的指標元素存取會評估為 `*(p + n)`，其中 `n` 必須是可隱含轉換成 `int`、`uint`、`long` 或 `ulong` 的型別。 如需 `+` 運算子搭配指標的行為資訊，請參閱[在指標中加減整數值](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer)一節。

下例示範如何使用指標和 `[]` 運算子存取陣列元素：

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

此範例會使用 [`stackalloc` 運算子](stackalloc.md)配置堆疊上的記憶體區塊。

> [!NOTE]
> 指標元素存取運算子不會檢查超出範圍的錯誤。

型別為 `void*` 的運算式，指標元素存取無法使用 `[]`。

[陣列元素或索引子存取](member-access-operators.md#indexer-operator-)也可以使用 `[]` 運算子。

## <a name="pointer-arithmetic-operators"></a>指標算術運算子

您可以使用指標執行下列算術運算：

- 在指標中加減整數值
- 減去兩個指標
- 遞增或遞減指標

您無法使用 `void*` 型別的指標執行這些運算。

如需支援的數值型別算術運算資訊，請參閱[算術運算子](arithmetic-operators.md)。

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>在指標中加減整數值

針對 `T*` 型別的 `p` 指標和可隱含轉換成 `int`、`uint`、`long` 或 `ulong` 的運算式 `n`，加減定義如下：

- `p + n` 和 `n + p` 運算式都會產生因為將 `n * sizeof(T)` 新增到 `p` 指定位址而得到的 `T*` 型別指標。
- `p - n` 運算式會產生因為從 `p` 指定的位址減去 `n * sizeof(T)` 而得到的 `T*` 型別指標。

[`sizeof` 運算子](../keywords/sizeof.md)取得以位元組為單位的型別大小。

下例示範 `+` 運算子加指標的用法：

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>指標減法

針對 `T*` 型別的兩個指標 `p1` 和 `p2`，運算式 `p1 - p2` 會產生 `p1` 和 `p2` 除以 `sizeof(T)` 所指定的位址間差異。 結果的類型是 `long`。 亦即，`p1 - p2` 會計算為 `((long)(p1) - (long)(p2)) / sizeof(T)`。

下例示範指標減法：

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>指標遞增和遞減

`++` 遞增運算子在其指標運算元中[加](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1。 `--` 遞減運算子從其指標運算元中[減](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1。

這兩個運算子都支援兩種形式：後置 (`p++` 和 `p--`) 及前置 (`++p` 和 `--p`)。 `p++` 和 `p--` 的結果是運算「前」  的 `p` 值。 `++p` 和 `--p` 的結果是運算「後」  的 `p` 值。

下例示範前置和後置遞增運算子的行為：

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>指標比較運算子

您可以使用 `==`、`!=`、`<`、`>`、`<=` 和 `>=` 運算子來比較包括 `void*` 在內之任何指標型別的運算元。 這些運算子會比較兩個運算元指定的位址，如同它們是不帶正負號的整數一樣。

如需這些其他型別運算元的運算子行為資訊，請參閱[等號運算子](equality-operators.md)和[比較運算子](comparison-operators.md)文章。

## <a name="operator-precedence"></a>運算子優先順序

下列清單排列指標相關的運算子，從最高優先順序到最低：

- 後置遞增 `x++` 和遞減 `x--` 運算子以及 `->` 和 `[]` 運算子
- 前置遞增 `++x` 和遞減 `--x` 運算子以及 `&` 和 `*` 運算子
- 加法類 `+` 和 `-` 運算子
- 比較 `<`、`>`、`<=` 和 `>=` 運算子
- 等號 `==` 和 `!=` 運算子

使用括弧 `()` 變更由運算子優先順序強制執行的評估順序。

如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](index.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義的型別無法多載指標相關運算子 `&`、`*`、`->` 和 `[]`。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [固定和可移動變數](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [傳址運算子](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [指標間接](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [指標成員存取](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [指標元素存取](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [指標算術](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [指標遞增和遞減](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [指標比較](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [unsafe 關鍵字](../keywords/unsafe.md)
- [fixed 關鍵字](../keywords/fixed-statement.md)
- [stackalloc 運算子](stackalloc.md)
- [sizeof 運算子](../keywords/sizeof.md)
