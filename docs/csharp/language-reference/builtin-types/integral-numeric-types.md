---
title: 整數的數字型別 - C# 參考
description: 了解每個整數數字型別的範圍、儲存體大小和用法。
ms.date: 10/22/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: c255711e4b165fdca27d50c6bd0f2debfe15ae25
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773859"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="e5e44-103">整數的數字型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e5e44-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="e5e44-104">**整數數字型別**是**簡單型別**的子集，且可使用[*常值*](#integer-literals)初始化。</span><span class="sxs-lookup"><span data-stu-id="e5e44-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integer-literals).</span></span> <span data-ttu-id="e5e44-105">所有的整數型別也都是實值型別。</span><span class="sxs-lookup"><span data-stu-id="e5e44-105">All integral types are also value types.</span></span> <span data-ttu-id="e5e44-106">所有整數數數值型別都支援[算術](../operators/arithmetic-operators.md)、[位邏輯](../operators/bitwise-and-shift-operators.md)、比較和[等號](../operators/equality-operators.md)[比較](../operators/comparison-operators.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="e5e44-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="e5e44-107">整數型別的特性</span><span class="sxs-lookup"><span data-stu-id="e5e44-107">Characteristics of the integral types</span></span>

<span data-ttu-id="e5e44-108">C# 支援下列預先定義的整數型別：</span><span class="sxs-lookup"><span data-stu-id="e5e44-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="e5e44-109">C# 型別/關鍵字</span><span class="sxs-lookup"><span data-stu-id="e5e44-109">C# type/keyword</span></span>|<span data-ttu-id="e5e44-110">Range</span><span class="sxs-lookup"><span data-stu-id="e5e44-110">Range</span></span>|<span data-ttu-id="e5e44-111">大小</span><span class="sxs-lookup"><span data-stu-id="e5e44-111">Size</span></span>|<span data-ttu-id="e5e44-112">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="e5e44-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="e5e44-113">-128 到 127</span><span class="sxs-lookup"><span data-stu-id="e5e44-113">-128 to 127</span></span>|<span data-ttu-id="e5e44-114">帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="e5e44-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="e5e44-115">0 到 255</span><span class="sxs-lookup"><span data-stu-id="e5e44-115">0 to 255</span></span>|<span data-ttu-id="e5e44-116">不帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="e5e44-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="e5e44-117">-32,768 到 32,767</span><span class="sxs-lookup"><span data-stu-id="e5e44-117">-32,768 to 32,767</span></span>|<span data-ttu-id="e5e44-118">帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="e5e44-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="e5e44-119">0 到 65,535</span><span class="sxs-lookup"><span data-stu-id="e5e44-119">0 to 65,535</span></span>|<span data-ttu-id="e5e44-120">不帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="e5e44-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="e5e44-121">-2,147,483,648 至 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="e5e44-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="e5e44-122">帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="e5e44-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="e5e44-123">0 到 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="e5e44-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="e5e44-124">不帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="e5e44-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="e5e44-125">-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="e5e44-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="e5e44-126">帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="e5e44-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="e5e44-127">0 到 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="e5e44-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="e5e44-128">不帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="e5e44-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="e5e44-129">在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。</span><span class="sxs-lookup"><span data-stu-id="e5e44-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="e5e44-130">它們是可互換的。</span><span class="sxs-lookup"><span data-stu-id="e5e44-130">They are interchangeable.</span></span> <span data-ttu-id="e5e44-131">例如，下列宣告會宣告相同型別的變數：</span><span class="sxs-lookup"><span data-stu-id="e5e44-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="e5e44-132">每個整數型別的預設值都是零 (`0`)。</span><span class="sxs-lookup"><span data-stu-id="e5e44-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="e5e44-133">每個整數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大值。</span><span class="sxs-lookup"><span data-stu-id="e5e44-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="e5e44-134">使用 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> 結構來表示帶正負號的整數，無上下限。</span><span class="sxs-lookup"><span data-stu-id="e5e44-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="e5e44-135">整數常值</span><span class="sxs-lookup"><span data-stu-id="e5e44-135">Integer literals</span></span>

<span data-ttu-id="e5e44-136">整數常值可以是</span><span class="sxs-lookup"><span data-stu-id="e5e44-136">Integer literals can be</span></span>

- <span data-ttu-id="e5e44-137">*decimal*：不含任何前置詞</span><span class="sxs-lookup"><span data-stu-id="e5e44-137">*decimal*: without any prefix</span></span>
- <span data-ttu-id="e5e44-138">*十六進位*：使用 `0x` 或 `0X` 前置詞</span><span class="sxs-lookup"><span data-stu-id="e5e44-138">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="e5e44-139">*binary*：具有 `0b` 或 `0B` 前置詞（可在C# 7.0 和更新版本中取得）</span><span class="sxs-lookup"><span data-stu-id="e5e44-139">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="e5e44-140">下列程式碼示範每個的範例：</span><span class="sxs-lookup"><span data-stu-id="e5e44-140">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="e5e44-141">上述範例也會示範如何使用 `_` 做為*數位分隔符號*，從C# 7.0 開始支援。</span><span class="sxs-lookup"><span data-stu-id="e5e44-141">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="e5e44-142">您可以使用數位分隔符號搭配所有類型的數值常值。</span><span class="sxs-lookup"><span data-stu-id="e5e44-142">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="e5e44-143">整數常值的類型是由其後綴決定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e5e44-143">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="e5e44-144">如果常值沒有後置詞，其類型會是下列類型中可表示其值的第一個型別： `int`、`uint`、`long`、`ulong`。</span><span class="sxs-lookup"><span data-stu-id="e5e44-144">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="e5e44-145">如果常值是以 `U` 或 `u` 為後置字元，則其類型會是下列類型中可表示其值的第一個型別： `uint`、`ulong`。</span><span class="sxs-lookup"><span data-stu-id="e5e44-145">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="e5e44-146">如果常值是以 `L` 或 `l` 為後置字元，則其類型會是下列類型中可表示其值的第一個型別： `long`、`ulong`。</span><span class="sxs-lookup"><span data-stu-id="e5e44-146">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e5e44-147">您可以使用小寫字母 `l` 做為尾碼。</span><span class="sxs-lookup"><span data-stu-id="e5e44-147">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="e5e44-148">不過，這會產生編譯器警告，因為字母 `l` 可以與數位 `1` 混淆。</span><span class="sxs-lookup"><span data-stu-id="e5e44-148">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="e5e44-149">為了清楚起見，請使用 `L`。</span><span class="sxs-lookup"><span data-stu-id="e5e44-149">Use `L` for clarity.</span></span>

- <span data-ttu-id="e5e44-150">如果常值是以 `UL`、`Ul`、`uL`、`ul`、`LU`、`Lu`、`lU` 或 `lu` 為尾碼，則其類型為 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="e5e44-150">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="e5e44-151">如果整數常值所代表的值超出 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>，就會發生編譯錯誤 [CS1021](../../misc/cs1021.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e44-151">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="e5e44-152">如果整數常值的判斷型別是 `int`，而該值是在目的地類型的範圍內，則常值所代表的值可以隱含地轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`：</span><span class="sxs-lookup"><span data-stu-id="e5e44-152">If the determined type of an integer literal is `int` and the value is within the range of the destination type, the value represented by the literal can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="e5e44-153">如上述範例所示，如果常值不在目的地類型的範圍內，就會發生編譯器錯誤[CS0031](../../misc/cs0031.md) 。</span><span class="sxs-lookup"><span data-stu-id="e5e44-153">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="e5e44-154">您也可以使用轉型，將整數常值所代表的值轉換為類型，而不是常值的判斷型別：</span><span class="sxs-lookup"><span data-stu-id="e5e44-154">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="e5e44-155">轉換</span><span class="sxs-lookup"><span data-stu-id="e5e44-155">Conversions</span></span>

<span data-ttu-id="e5e44-156">您可以將任何整數數數值型別轉換成任何其他整數數數值型別。</span><span class="sxs-lookup"><span data-stu-id="e5e44-156">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="e5e44-157">如果目的地類型可以儲存來源類型的所有值，則轉換是隱含的。</span><span class="sxs-lookup"><span data-stu-id="e5e44-157">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="e5e44-158">否則，您必須使用[cast 運算子 `()`](../operators/type-testing-and-cast.md#cast-operator-)來叫用明確轉換。</span><span class="sxs-lookup"><span data-stu-id="e5e44-158">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="e5e44-159">如需詳細資訊，請參閱[內建數值轉換](numeric-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e44-159">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e5e44-160">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e5e44-160">C# language specification</span></span>

<span data-ttu-id="e5e44-161">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="e5e44-161">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="e5e44-162">整數型別</span><span class="sxs-lookup"><span data-stu-id="e5e44-162">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="e5e44-163">整數常值</span><span class="sxs-lookup"><span data-stu-id="e5e44-163">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="e5e44-164">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5e44-164">See also</span></span>

- [<span data-ttu-id="e5e44-165">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e5e44-165">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e5e44-166">內建型別表</span><span class="sxs-lookup"><span data-stu-id="e5e44-166">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="e5e44-167">浮點類型</span><span class="sxs-lookup"><span data-stu-id="e5e44-167">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="e5e44-168">格式化數值結果表</span><span class="sxs-lookup"><span data-stu-id="e5e44-168">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="e5e44-169">.NET 中的數值</span><span class="sxs-lookup"><span data-stu-id="e5e44-169">Numerics in .NET</span></span>](../../../standard/numerics.md)
