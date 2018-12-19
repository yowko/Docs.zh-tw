---
title: short - C# 參考
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 8c38a4158f627f41d1667eb96478cd499de78772
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238895"
---
# <a name="short-c-reference"></a><span data-ttu-id="3484a-102">short (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3484a-102">short (C# Reference)</span></span>

<span data-ttu-id="3484a-103">`short` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數資料型別。</span><span class="sxs-lookup"><span data-stu-id="3484a-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="3484a-104">類型</span><span class="sxs-lookup"><span data-stu-id="3484a-104">Type</span></span>|<span data-ttu-id="3484a-105">範圍</span><span class="sxs-lookup"><span data-stu-id="3484a-105">Range</span></span>|<span data-ttu-id="3484a-106">大小</span><span class="sxs-lookup"><span data-stu-id="3484a-106">Size</span></span>|<span data-ttu-id="3484a-107">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="3484a-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`short`|<span data-ttu-id="3484a-108">-32,768 到 32,767</span><span class="sxs-lookup"><span data-stu-id="3484a-108">-32,768 to 32,767</span></span>|<span data-ttu-id="3484a-109">帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="3484a-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="3484a-110">常值</span><span class="sxs-lookup"><span data-stu-id="3484a-110">Literals</span></span>

<span data-ttu-id="3484a-111">您可以針對 `short` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="3484a-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="3484a-112">如果整數常值超出 `short` 的範圍 (亦即，如果小於 <xref:System.Int16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="3484a-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="3484a-113">在下列範例中，以十進位、十六進位和二進位常值表示的 1,034 整數，從 [int](int.md) 隱含轉換成 `short` 值。</span><span class="sxs-lookup"><span data-stu-id="3484a-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](int.md) to `short` values.</span></span>

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]

> [!NOTE]
> <span data-ttu-id="3484a-114">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="3484a-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="3484a-115">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="3484a-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="3484a-116">從 C# 7.0 開始，已新增一組功能來提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="3484a-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>

- <span data-ttu-id="3484a-117">C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3484a-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="3484a-118">C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3484a-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="3484a-119">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="3484a-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="3484a-120">一些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="3484a-120">Some examples are shown below.</span></span>

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]

## <a name="compiler-overload-resolution"></a><span data-ttu-id="3484a-121">編譯器多載解析</span><span class="sxs-lookup"><span data-stu-id="3484a-121">Compiler overload resolution</span></span>

<span data-ttu-id="3484a-122">呼叫多載的方法時，必須使用轉型。</span><span class="sxs-lookup"><span data-stu-id="3484a-122">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="3484a-123">例如，請考慮使用下列使用 `short` 和 [int](int.md) 參數的多載方法：</span><span class="sxs-lookup"><span data-stu-id="3484a-123">Consider, for example, the following overloaded methods that use `short` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(short s) {}
```

<span data-ttu-id="3484a-124">使用 `short` 轉型時，可以保證呼叫正確的類型，例如：</span><span class="sxs-lookup"><span data-stu-id="3484a-124">Using the `short` cast guarantees that the correct type is called, for example:</span></span>

```csharp
SampleMethod(5);         // Calling the method with the int parameter
SampleMethod((short)5);  // Calling the method with the short parameter
```

## <a name="conversions"></a><span data-ttu-id="3484a-125">轉換</span><span class="sxs-lookup"><span data-stu-id="3484a-125">Conversions</span></span>

<span data-ttu-id="3484a-126">有一項從 `short` 轉換為 [int](int.md)、[long](long.md)、[float](float.md)、[double](double.md) 或 [decimal](decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="3484a-126">There is a predefined implicit conversion from `short` to [int](int.md), [long](long.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="3484a-127">您不能將較大儲存大小的非常值數字類型隱含轉換為 `short` (如需整數類型的儲存大小，請參閱[整數類型表](integral-types-table.md))。</span><span class="sxs-lookup"><span data-stu-id="3484a-127">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="3484a-128">例如，請考慮使用下列兩個 `short` 變數 `x` 和 `y`：</span><span class="sxs-lookup"><span data-stu-id="3484a-128">Consider, for example, the following two `short` variables `x` and `y`:</span></span>

```csharp
short x = 5, y = 12;
```

<span data-ttu-id="3484a-129">因為指派運算子右側的算術運算式預設會評估為 [int](int.md)，所以下列指派陳述式會產生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="3484a-129">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](int.md) by default.</span></span>

```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

<span data-ttu-id="3484a-130">若要修正這個問題，請使用轉換：</span><span class="sxs-lookup"><span data-stu-id="3484a-130">To fix this problem, use a cast:</span></span>

```csharp
short z  = (short)(x + y);   // Explicit conversion
```

<span data-ttu-id="3484a-131">不過，也可以使用目的地變數具有相同或較大儲存大小的下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="3484a-131">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>

```csharp
int m = x + y;
long n = x + y;
```

<span data-ttu-id="3484a-132">不會從浮點類型隱含地轉換為 `short`。</span><span class="sxs-lookup"><span data-stu-id="3484a-132">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="3484a-133">例如，下列陳述式會在未使用明確轉型的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="3484a-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
short x = 3.0;          // Error: no implicit conversion from double
short y = (short)3.0;   // OK: explicit conversion
```

<span data-ttu-id="3484a-134">如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](float.md) 和 [double](double.md)。</span><span class="sxs-lookup"><span data-stu-id="3484a-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="3484a-135">如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="3484a-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3484a-136">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3484a-136">C# language specification</span></span>

<span data-ttu-id="3484a-137">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[整數型別](~/_csharplang/spec/types.md#integral-types)。</span><span class="sxs-lookup"><span data-stu-id="3484a-137">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="3484a-138">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="3484a-138">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3484a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3484a-139">See also</span></span>

- <xref:System.Int16>
- [<span data-ttu-id="3484a-140">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3484a-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3484a-141">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3484a-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3484a-142">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="3484a-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3484a-143">整數型別表</span><span class="sxs-lookup"><span data-stu-id="3484a-143">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="3484a-144">內建型別表</span><span class="sxs-lookup"><span data-stu-id="3484a-144">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="3484a-145">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="3484a-145">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="3484a-146">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="3484a-146">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)