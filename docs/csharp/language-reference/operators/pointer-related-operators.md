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
ms.openlocfilehash: 7eb6666d10c44c342f69c7cfc763feb1b7b98c9d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738607"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="93bab-103">指標相關運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="93bab-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="93bab-104">您可以搭配下列運算子來使用指標：</span><span class="sxs-lookup"><span data-stu-id="93bab-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="93bab-105">一元[`&`(位址)](#address-of-operator-)運算子:取得變數的位址</span><span class="sxs-lookup"><span data-stu-id="93bab-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="93bab-106">單位[`*`(指標間接)](#pointer-indirection-operator-)運算符:獲取指標指向的變數</span><span class="sxs-lookup"><span data-stu-id="93bab-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="93bab-107">(成員存取)[`->`](#pointer-member-access-operator--)和[`[]`(元素存取)](#pointer-element-access-operator-)運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="93bab-108">算數運算子[`+``-`、`++`與`--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="93bab-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="93bab-109">比較運算子[`==``!=`、 `<` `>`、 `<=`、 、 、 、 、 和`>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="93bab-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="93bab-110">如需指標型別的資訊，請參閱[指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="93bab-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="93bab-111">任何具有指標的作業都需要 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="93bab-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="93bab-112">包含不安全塊的代碼必須使用[`-unsafe`](../compiler-options/unsafe-compiler-option.md)編譯器選項進行編譯。</span><span class="sxs-lookup"><span data-stu-id="93bab-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a><span data-ttu-id="93bab-113">位址運算子&amp;</span><span class="sxs-lookup"><span data-stu-id="93bab-113">Address-of operator &amp;</span></span>

<span data-ttu-id="93bab-114">一元 `&` 運算子會傳回其運算元的位址：</span><span class="sxs-lookup"><span data-stu-id="93bab-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](snippets/PointerOperators.cs#AddressOf)]

<span data-ttu-id="93bab-115">`&` 運算子的運算元必須是固定的變數。</span><span class="sxs-lookup"><span data-stu-id="93bab-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="93bab-116">「固定」\*\* 變數是位在不受[記憶體回收行程](../../../standard/garbage-collection/index.md)作業影響之儲存位置的變數。</span><span class="sxs-lookup"><span data-stu-id="93bab-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="93bab-117">在前述範例中，區域變數 `number` 是固定的變數，因為它位於堆疊上。</span><span class="sxs-lookup"><span data-stu-id="93bab-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="93bab-118">會受到記憶體回收行程影響且位在儲存位置的變數 (例如重新配置)，稱為「可移動」\*\* 變數。</span><span class="sxs-lookup"><span data-stu-id="93bab-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="93bab-119">物件欄位和陣列元素是可移動變數的範例。</span><span class="sxs-lookup"><span data-stu-id="93bab-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="93bab-120">如果你"修復"或"pin",你可以得到一個可移動變數的位址,它帶有一個[`fixed`語句](../keywords/fixed-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="93bab-120">You can get the address of a movable variable if you "fix", or "pin", it with a [`fixed` statement](../keywords/fixed-statement.md).</span></span> <span data-ttu-id="93bab-121">獲取的位址僅在`fixed`語句塊內有效。</span><span class="sxs-lookup"><span data-stu-id="93bab-121">The obtained address is valid only inside the block of a `fixed` statement.</span></span> <span data-ttu-id="93bab-122">下面的範例展示如何使用 敘`fixed`述`&`與運算子:</span><span class="sxs-lookup"><span data-stu-id="93bab-122">The following example shows how to use a `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](snippets/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="93bab-123">您無法取得常數或值的位址。</span><span class="sxs-lookup"><span data-stu-id="93bab-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="93bab-124">如需固定和可移動變數的詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[固定和可移動變數](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)一節。</span><span class="sxs-lookup"><span data-stu-id="93bab-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="93bab-125">二元 `&` 運算子會計算其布林運算元的[邏輯 AND](boolean-logical-operators.md#logical-and-operator-)或其整數運算元的[位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-)。</span><span class="sxs-lookup"><span data-stu-id="93bab-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="93bab-126">指標間接運算子 \*</span><span class="sxs-lookup"><span data-stu-id="93bab-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="93bab-127">一元指標間接運算子 `*` 取得其運算元指向的變數。</span><span class="sxs-lookup"><span data-stu-id="93bab-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="93bab-128">它也稱之為取值運算子。</span><span class="sxs-lookup"><span data-stu-id="93bab-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="93bab-129">`*` 運算子的運算元必須是指標型別。</span><span class="sxs-lookup"><span data-stu-id="93bab-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](snippets/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="93bab-130">您不能將 `*` 運算子套用至 `void*` 型別的運算式。</span><span class="sxs-lookup"><span data-stu-id="93bab-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="93bab-131">二元 `*` 運算子會計算其數值運算元的[乘積](arithmetic-operators.md#multiplication-operator-)。</span><span class="sxs-lookup"><span data-stu-id="93bab-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="93bab-132">指標成員存取運算子 -></span><span class="sxs-lookup"><span data-stu-id="93bab-132">Pointer member access operator -></span></span>

<span data-ttu-id="93bab-133">`->` 運算子結合[指標間接](#pointer-indirection-operator-)和[成員存取](member-access-operators.md#member-access-expression-)。</span><span class="sxs-lookup"><span data-stu-id="93bab-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="93bab-134">`x`也就是說,如果是`T*`類型的指標,並且`y`是類型的`T`可訪問成員,則是窗體的運算式</span><span class="sxs-lookup"><span data-stu-id="93bab-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of type `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="93bab-135">相當於</span><span class="sxs-lookup"><span data-stu-id="93bab-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="93bab-136">下列範例示範 `->` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="93bab-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](snippets/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="93bab-137">您不能將 `->` 運算子套用至 `void*` 型別的運算式。</span><span class="sxs-lookup"><span data-stu-id="93bab-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="93bab-138">指標元素存取運算子 []</span><span class="sxs-lookup"><span data-stu-id="93bab-138">Pointer element access operator []</span></span>

<span data-ttu-id="93bab-139">針對指標型別的運算式 `p`，`p[n]` 格式的指標元素存取會評估為 `*(p + n)`，其中 `n` 必須是可隱含轉換成 `int`、`uint`、`long` 或 `ulong` 的型別。</span><span class="sxs-lookup"><span data-stu-id="93bab-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="93bab-140">如需 `+` 運算子搭配指標的行為資訊，請參閱[在指標中加減整數值](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer)一節。</span><span class="sxs-lookup"><span data-stu-id="93bab-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="93bab-141">下例示範如何使用指標和 `[]` 運算子存取陣列元素：</span><span class="sxs-lookup"><span data-stu-id="93bab-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](snippets/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="93bab-142">在前面的範例中,[`stackalloc`表達式](stackalloc.md)在堆疊上分配一個記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="93bab-142">In the preceding example, a [`stackalloc` expression](stackalloc.md) allocates a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="93bab-143">指標元素存取運算子不會檢查超出範圍的錯誤。</span><span class="sxs-lookup"><span data-stu-id="93bab-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="93bab-144">型別為 `void*` 的運算式，指標元素存取無法使用 `[]`。</span><span class="sxs-lookup"><span data-stu-id="93bab-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="93bab-145">可將`[]`運算子用於[數位元素或索引器存取](member-access-operators.md#indexer-operator-)。</span><span class="sxs-lookup"><span data-stu-id="93bab-145">You can also use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="93bab-146">指標算術運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="93bab-147">您可以使用指標執行下列算術運算：</span><span class="sxs-lookup"><span data-stu-id="93bab-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="93bab-148">在指標中加減整數值</span><span class="sxs-lookup"><span data-stu-id="93bab-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="93bab-149">減去兩個指標</span><span class="sxs-lookup"><span data-stu-id="93bab-149">Subtract two pointers</span></span>
- <span data-ttu-id="93bab-150">遞增或遞減指標</span><span class="sxs-lookup"><span data-stu-id="93bab-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="93bab-151">您無法使用 `void*` 型別的指標執行這些運算。</span><span class="sxs-lookup"><span data-stu-id="93bab-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="93bab-152">如需支援的數值型別算術運算資訊，請參閱[算術運算子](arithmetic-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="93bab-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="93bab-153">在指標中加減整數值</span><span class="sxs-lookup"><span data-stu-id="93bab-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="93bab-154">針對 `T*` 型別的 `p` 指標和可隱含轉換成 `int`、`uint`、`long` 或 `ulong` 的運算式 `n`，加減定義如下：</span><span class="sxs-lookup"><span data-stu-id="93bab-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="93bab-155">`p + n` 和 `n + p` 運算式都會產生因為將 `n * sizeof(T)` 新增到 `p` 指定位址而得到的 `T*` 型別指標。</span><span class="sxs-lookup"><span data-stu-id="93bab-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="93bab-156">`p - n` 運算式會產生因為從 `p` 指定的位址減去 `n * sizeof(T)` 而得到的 `T*` 型別指標。</span><span class="sxs-lookup"><span data-stu-id="93bab-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="93bab-157">運算元 獲取類型的大小(以位元組為單位)。 [ `sizeof`](sizeof.md)</span><span class="sxs-lookup"><span data-stu-id="93bab-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="93bab-158">下例示範 `+` 運算子加指標的用法：</span><span class="sxs-lookup"><span data-stu-id="93bab-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](snippets/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="93bab-159">指標減法</span><span class="sxs-lookup"><span data-stu-id="93bab-159">Pointer subtraction</span></span>

<span data-ttu-id="93bab-160">針對 `T*` 型別的兩個指標 `p1` 和 `p2`，運算式 `p1 - p2` 會產生 `p1` 和 `p2` 除以 `sizeof(T)` 所指定的位址間差異。</span><span class="sxs-lookup"><span data-stu-id="93bab-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="93bab-161">結果的類型是 `long`。</span><span class="sxs-lookup"><span data-stu-id="93bab-161">The type of the result is `long`.</span></span> <span data-ttu-id="93bab-162">亦即，`p1 - p2` 會計算為 `((long)(p1) - (long)(p2)) / sizeof(T)`。</span><span class="sxs-lookup"><span data-stu-id="93bab-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="93bab-163">下例示範指標減法：</span><span class="sxs-lookup"><span data-stu-id="93bab-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](snippets/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="93bab-164">指標遞增和遞減</span><span class="sxs-lookup"><span data-stu-id="93bab-164">Pointer increment and decrement</span></span>

<span data-ttu-id="93bab-165">`++` 遞增運算子在其指標運算元中[加](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1。</span><span class="sxs-lookup"><span data-stu-id="93bab-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="93bab-166">`--` 遞減運算子從其指標運算元中[減](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1。</span><span class="sxs-lookup"><span data-stu-id="93bab-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="93bab-167">這兩個運算子都支援兩種形式：後置 (`p++` 和 `p--`) 及前置 (`++p` 和 `--p`)。</span><span class="sxs-lookup"><span data-stu-id="93bab-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="93bab-168">`p++` 和 `p--` 的結果是運算「前」 \*\* 的 `p` 值。</span><span class="sxs-lookup"><span data-stu-id="93bab-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="93bab-169">`++p` 和 `--p` 的結果是運算「後」 \*\* 的 `p` 值。</span><span class="sxs-lookup"><span data-stu-id="93bab-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="93bab-170">下例示範前置和後置遞增運算子的行為：</span><span class="sxs-lookup"><span data-stu-id="93bab-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](snippets/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="93bab-171">指標比較運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-171">Pointer comparison operators</span></span>

<span data-ttu-id="93bab-172">您可以使用 `==`、`!=`、`<`、`>`、`<=` 和 `>=` 運算子來比較包括 `void*` 在內之任何指標型別的運算元。</span><span class="sxs-lookup"><span data-stu-id="93bab-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="93bab-173">這些運算子會比較兩個運算元指定的位址，如同它們是不帶正負號的整數一樣。</span><span class="sxs-lookup"><span data-stu-id="93bab-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="93bab-174">如需這些其他型別運算元的運算子行為資訊，請參閱[等號運算子](equality-operators.md)和[比較運算子](comparison-operators.md)文章。</span><span class="sxs-lookup"><span data-stu-id="93bab-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="93bab-175">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="93bab-175">Operator precedence</span></span>

<span data-ttu-id="93bab-176">下列清單排列指標相關的運算子，從最高優先順序到最低：</span><span class="sxs-lookup"><span data-stu-id="93bab-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="93bab-177">後置遞增 `x++` 和遞減 `x--` 運算子以及 `->` 和 `[]` 運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="93bab-178">前置遞增 `++x` 和遞減 `--x` 運算子以及 `&` 和 `*` 運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="93bab-179">加法類 `+` 和 `-` 運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="93bab-180">比較 `<`、`>`、`<=` 和 `>=` 運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="93bab-181">等號 `==` 和 `!=` 運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="93bab-182">使用括弧 `()` 變更由運算子優先順序強制執行的評估順序。</span><span class="sxs-lookup"><span data-stu-id="93bab-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="93bab-183">有關按優先順序排序的 C# 運算子的完整清單,請參閱[C# 運算符](index.md)一文中的[運算符優先順序](index.md#operator-precedence)部分。</span><span class="sxs-lookup"><span data-stu-id="93bab-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="93bab-184">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="93bab-184">Operator overloadability</span></span>

<span data-ttu-id="93bab-185">使用者定義的型別無法多載指標相關運算子 `&`、`*`、`->` 和 `[]`。</span><span class="sxs-lookup"><span data-stu-id="93bab-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="93bab-186">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="93bab-186">C# language specification</span></span>

<span data-ttu-id="93bab-187">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="93bab-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="93bab-188">固定和可移動變數</span><span class="sxs-lookup"><span data-stu-id="93bab-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="93bab-189">傳址運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="93bab-190">指標間接</span><span class="sxs-lookup"><span data-stu-id="93bab-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="93bab-191">指標成員存取</span><span class="sxs-lookup"><span data-stu-id="93bab-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="93bab-192">指標元素存取</span><span class="sxs-lookup"><span data-stu-id="93bab-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="93bab-193">指標算術</span><span class="sxs-lookup"><span data-stu-id="93bab-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="93bab-194">指標遞增和遞減</span><span class="sxs-lookup"><span data-stu-id="93bab-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="93bab-195">指標比較</span><span class="sxs-lookup"><span data-stu-id="93bab-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="93bab-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93bab-196">See also</span></span>

- [<span data-ttu-id="93bab-197">C# 參考</span><span class="sxs-lookup"><span data-stu-id="93bab-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="93bab-198">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="93bab-199">指標類型</span><span class="sxs-lookup"><span data-stu-id="93bab-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="93bab-200">unsafe 關鍵字</span><span class="sxs-lookup"><span data-stu-id="93bab-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="93bab-201">固定關鍵字</span><span class="sxs-lookup"><span data-stu-id="93bab-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="93bab-202">stackalloc</span><span class="sxs-lookup"><span data-stu-id="93bab-202">stackalloc</span></span>](stackalloc.md)
- [<span data-ttu-id="93bab-203">sizeof 運算子</span><span class="sxs-lookup"><span data-stu-id="93bab-203">sizeof operator</span></span>](sizeof.md)
