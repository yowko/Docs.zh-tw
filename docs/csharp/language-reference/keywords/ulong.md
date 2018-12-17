---
title: ulong 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: 97db22612e900658746f40cd117ff941135027a1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235016"
---
# <a name="ulong-c-reference"></a><span data-ttu-id="e50d6-102">ulong (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e50d6-102">ulong (C# Reference)</span></span>

<span data-ttu-id="e50d6-103">`ulong` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數類型。</span><span class="sxs-lookup"><span data-stu-id="e50d6-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="e50d6-104">類型</span><span class="sxs-lookup"><span data-stu-id="e50d6-104">Type</span></span>|<span data-ttu-id="e50d6-105">範圍</span><span class="sxs-lookup"><span data-stu-id="e50d6-105">Range</span></span>|<span data-ttu-id="e50d6-106">大小</span><span class="sxs-lookup"><span data-stu-id="e50d6-106">Size</span></span>|<span data-ttu-id="e50d6-107">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="e50d6-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`ulong`|<span data-ttu-id="e50d6-108">0 到 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="e50d6-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="e50d6-109">不帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="e50d6-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="e50d6-110">常值</span><span class="sxs-lookup"><span data-stu-id="e50d6-110">Literals</span></span>

<span data-ttu-id="e50d6-111">您可以針對 `ulong` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="e50d6-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="e50d6-112">如果整數常值超出 `ulong` 的範圍 (亦即，如果小於 <xref:System.UInt64.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="e50d6-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="e50d6-113">在下列範例中，以十進位、十六進位和二進位常值表示的 7,934,076,125 整數，會指派給 `ulong` 值。</span><span class="sxs-lookup"><span data-stu-id="e50d6-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>

[!code-csharp[ulong](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]

> [!NOTE]
> <span data-ttu-id="e50d6-114">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="e50d6-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="e50d6-115">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="e50d6-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="e50d6-116">從 C# 7.0 開始，已新增一些功能來提升可讀性：</span><span class="sxs-lookup"><span data-stu-id="e50d6-116">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="e50d6-117">C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e50d6-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="e50d6-118">C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e50d6-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="e50d6-119">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="e50d6-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="e50d6-120">一些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="e50d6-120">Some examples are shown below.</span></span>

[!code-csharp[long](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

<span data-ttu-id="e50d6-121">整數常值亦可包含後置詞以表示類型。</span><span class="sxs-lookup"><span data-stu-id="e50d6-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="e50d6-122">`UL` 或 `ul` 後置詞明確地將數值常值識別為 `ulong` 值。</span><span class="sxs-lookup"><span data-stu-id="e50d6-122">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="e50d6-123">如果常值超出 <xref:System.Int64.MaxValue?displayProperty=nameWithType>，則 `L` 後置詞表示 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="e50d6-123">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e50d6-124">如果常值超出 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>，則 `U` 或 `u` 後置詞表示 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="e50d6-124">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e50d6-125">下列範例會使用 `ul` 後置詞來表示長整數：</span><span class="sxs-lookup"><span data-stu-id="e50d6-125">The following example uses the `ul` suffix to denote a long integer:</span></span>

[!code-csharp[ulsuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

<span data-ttu-id="e50d6-126">如果整數常值沒有後置詞，其類型會是下列類型中可表示其值的第一個類型：</span><span class="sxs-lookup"><span data-stu-id="e50d6-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="e50d6-127">int</span><span class="sxs-lookup"><span data-stu-id="e50d6-127">int</span></span>](int.md)
2. [<span data-ttu-id="e50d6-128">uint</span><span class="sxs-lookup"><span data-stu-id="e50d6-128">uint</span></span>](uint.md)
3. [<span data-ttu-id="e50d6-129">long</span><span class="sxs-lookup"><span data-stu-id="e50d6-129">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="e50d6-130">編譯器多載解析</span><span class="sxs-lookup"><span data-stu-id="e50d6-130">Compiler overload resolution</span></span>

<span data-ttu-id="e50d6-131">後置詞的常見用法是搭配呼叫多載方法。</span><span class="sxs-lookup"><span data-stu-id="e50d6-131">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="e50d6-132">例如，請考慮使用下列使用 `ulong` 和 [int](int.md) 參數的多載方法：</span><span class="sxs-lookup"><span data-stu-id="e50d6-132">Consider, for example, the following overloaded methods that use `ulong` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ulong l) {}
```

<span data-ttu-id="e50d6-133">搭配使用後置詞與 `ulong` 參數時，可以保證呼叫正確的類型，例如：</span><span class="sxs-lookup"><span data-stu-id="e50d6-133">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>

```csharp
SampleMethod(5);    // Calling the method with the int parameter
SampleMethod(5UL);  // Calling the method with the ulong parameter
```

## <a name="conversions"></a><span data-ttu-id="e50d6-134">轉換</span><span class="sxs-lookup"><span data-stu-id="e50d6-134">Conversions</span></span>

<span data-ttu-id="e50d6-135">針對從 `ulong` 轉換為 [float](float.md)、[double](double.md) 或 [decimal](decimal.md)，有一項預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="e50d6-135">There is a predefined implicit conversion from `ulong` to [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="e50d6-136">沒有從 `ulong` 轉換為任意整數類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="e50d6-136">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="e50d6-137">例如，下列陳述式會在未明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="e50d6-137">For example, the following statement will produce a compilation error without an explicit cast:</span></span>

```csharp
long long1 = 8UL;   // Error: no implicit conversion from ulong
```

<span data-ttu-id="e50d6-138">有一項從 [byte](byte.md)、[ushort](ushort.md)、[uint](uint.md) 或 [char](char.md) 轉換為 `ulong` 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="e50d6-138">There is a predefined implicit conversion from [byte](byte.md), [ushort](ushort.md), [uint](uint.md), or [char](char.md) to `ulong`.</span></span>

<span data-ttu-id="e50d6-139">同時，沒有從浮點類型轉換為 `ulong` 的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="e50d6-139">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="e50d6-140">例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="e50d6-140">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
ulong x = 3.0;
// OK -- explicit conversion:
ulong y = (ulong)3.0;
```

<span data-ttu-id="e50d6-141">如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](float.md) 和 [double](double.md)。</span><span class="sxs-lookup"><span data-stu-id="e50d6-141">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="e50d6-142">如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="e50d6-142">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e50d6-143">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e50d6-143">C# language specification</span></span>

<span data-ttu-id="e50d6-144">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[整數型別](~/_csharplang/spec/types.md#integral-types)。</span><span class="sxs-lookup"><span data-stu-id="e50d6-144">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="e50d6-145">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="e50d6-145">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="e50d6-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e50d6-146">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="e50d6-147">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e50d6-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e50d6-148">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e50d6-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e50d6-149">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="e50d6-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e50d6-150">整數型別表</span><span class="sxs-lookup"><span data-stu-id="e50d6-150">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="e50d6-151">內建型別表</span><span class="sxs-lookup"><span data-stu-id="e50d6-151">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="e50d6-152">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="e50d6-152">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="e50d6-153">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="e50d6-153">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
