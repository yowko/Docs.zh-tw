---
title: int - C# 參考
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 6cabc2c6d4930c5d5fc88e76a17c1a6425ddd1bd
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185775"
---
# <a name="int-c-reference"></a><span data-ttu-id="cb0a6-102">int (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cb0a6-102">int (C# Reference)</span></span>

<span data-ttu-id="cb0a6-103">`int` 表示儲存值的整數型別 (以下表所示的大小和範圍為依據)。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="cb0a6-104">類型</span><span class="sxs-lookup"><span data-stu-id="cb0a6-104">Type</span></span>|<span data-ttu-id="cb0a6-105">範圍</span><span class="sxs-lookup"><span data-stu-id="cb0a6-105">Range</span></span>|<span data-ttu-id="cb0a6-106">大小</span><span class="sxs-lookup"><span data-stu-id="cb0a6-106">Size</span></span>|<span data-ttu-id="cb0a6-107">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="cb0a6-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`int`|<span data-ttu-id="cb0a6-108">-2,147,483,648 至 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="cb0a6-108">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="cb0a6-109">帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="cb0a6-109">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="cb0a6-110">常值</span><span class="sxs-lookup"><span data-stu-id="cb0a6-110">Literals</span></span>

<span data-ttu-id="cb0a6-111">您可以針對 `int` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-111">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="cb0a6-112">如果整數常值超出 `int` 的範圍 (亦即，如果小於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-112">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="cb0a6-113">在下列範例中，以十進位、十六進位和二進位常值表示的 90,946 整數，會指派給 `int` 值。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-113">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]

> [!NOTE]
> <span data-ttu-id="cb0a6-114">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="cb0a6-115">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="cb0a6-116">從 C# 7.0 開始，已新增一組功能來提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>
- <span data-ttu-id="cb0a6-117">C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="cb0a6-118">C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="cb0a6-119">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="cb0a6-120">一些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-120">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]

<span data-ttu-id="cb0a6-121">雖然沒有後置詞可以表示 `int` 類型，但整數常值亦可包含尾碼以表示類型。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-121">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="cb0a6-122">如果整數常值沒有後置詞，其類型會是下列類型中可表示其值的第一個類型：</span><span class="sxs-lookup"><span data-stu-id="cb0a6-122">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
2. [<span data-ttu-id="cb0a6-123">uint</span><span class="sxs-lookup"><span data-stu-id="cb0a6-123">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="cb0a6-124">long</span><span class="sxs-lookup"><span data-stu-id="cb0a6-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="cb0a6-125">ulong</span><span class="sxs-lookup"><span data-stu-id="cb0a6-125">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)

<span data-ttu-id="cb0a6-126">在上述範例中，常值 90946 為 `int` 類型。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-126">In these examples, the literal 90946 is of type `int`.</span></span>

## <a name="conversions"></a><span data-ttu-id="cb0a6-127">轉換</span><span class="sxs-lookup"><span data-stu-id="cb0a6-127">Conversions</span></span>

<span data-ttu-id="cb0a6-128">有一項從 `int` 轉換為 [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-128">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="cb0a6-129">例如：</span><span class="sxs-lookup"><span data-stu-id="cb0a6-129">For example:</span></span>

```csharp
// '123' is an int, so an implicit conversion takes place here:
float f = 123;
```

<span data-ttu-id="cb0a6-130">有一項從 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `int` 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-130">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="cb0a6-131">例如，下列指派陳述式會在並未進行轉換的情況下產生編譯錯誤：</span><span class="sxs-lookup"><span data-stu-id="cb0a6-131">For example, the following assignment statement will produce a compilation error without a cast:</span></span>

```csharp
long aLong = 22;
int i1 = aLong;       // Error: no implicit conversion from long.
int i2 = (int)aLong;  // OK: explicit conversion.
```

<span data-ttu-id="cb0a6-132">另請注意，沒有從浮點類型轉換為 `int` 的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-132">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="cb0a6-133">例如，除非使用明確轉換，否則下列陳述式會產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="cb0a6-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
int x = 3.0;         // Error: no implicit conversion from double.
int y = (int)3.0;    // OK: explicit conversion.
```

<span data-ttu-id="cb0a6-134">如需混合浮點類型和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-134">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cb0a6-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="cb0a6-135">C# Language Specification</span></span>

<span data-ttu-id="cb0a6-136">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[整數型別](~/_csharplang/spec/types.md#integral-types)。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-136">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="cb0a6-137">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb0a6-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb0a6-138">See also</span></span>

- <xref:System.Int32>
- [<span data-ttu-id="cb0a6-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cb0a6-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="cb0a6-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cb0a6-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cb0a6-141">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="cb0a6-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="cb0a6-142">整數型別表</span><span class="sxs-lookup"><span data-stu-id="cb0a6-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="cb0a6-143">內建型別表</span><span class="sxs-lookup"><span data-stu-id="cb0a6-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="cb0a6-144">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="cb0a6-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="cb0a6-145">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="cb0a6-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
