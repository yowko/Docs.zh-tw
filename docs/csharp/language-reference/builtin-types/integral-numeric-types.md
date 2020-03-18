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
ms.openlocfilehash: 394a809a9a2f45f4aee652d0eca892f62f0f2e54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093197"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="c6a32-103">整數的數字型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c6a32-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="c6a32-104">*積分數數值型別*表示整數。</span><span class="sxs-lookup"><span data-stu-id="c6a32-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="c6a32-105">所有積分數數值型別都是[數值型別](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a32-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="c6a32-106">它們也是[簡單的類型](value-types.md#built-in-value-types)，可以使用[文本](#integer-literals)初始化。</span><span class="sxs-lookup"><span data-stu-id="c6a32-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="c6a32-107">所有積分數數值型別都支援[算術](../operators/arithmetic-operators.md)、[位邏輯](../operators/bitwise-and-shift-operators.md)、[比較](../operators/comparison-operators.md)和[相等](../operators/equality-operators.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="c6a32-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="c6a32-108">整數型別的特性</span><span class="sxs-lookup"><span data-stu-id="c6a32-108">Characteristics of the integral types</span></span>

<span data-ttu-id="c6a32-109">C# 支援下列預先定義的整數型別：</span><span class="sxs-lookup"><span data-stu-id="c6a32-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="c6a32-110">C# 型別/關鍵字</span><span class="sxs-lookup"><span data-stu-id="c6a32-110">C# type/keyword</span></span>|<span data-ttu-id="c6a32-111">範圍</span><span class="sxs-lookup"><span data-stu-id="c6a32-111">Range</span></span>|<span data-ttu-id="c6a32-112">大小</span><span class="sxs-lookup"><span data-stu-id="c6a32-112">Size</span></span>|<span data-ttu-id="c6a32-113">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="c6a32-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="c6a32-114">-128 到 127</span><span class="sxs-lookup"><span data-stu-id="c6a32-114">-128 to 127</span></span>|<span data-ttu-id="c6a32-115">帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="c6a32-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="c6a32-116">0 至 255</span><span class="sxs-lookup"><span data-stu-id="c6a32-116">0 to 255</span></span>|<span data-ttu-id="c6a32-117">不帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="c6a32-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="c6a32-118">-32,768 至 32,767</span><span class="sxs-lookup"><span data-stu-id="c6a32-118">-32,768 to 32,767</span></span>|<span data-ttu-id="c6a32-119">帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="c6a32-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="c6a32-120">0 到 65,535</span><span class="sxs-lookup"><span data-stu-id="c6a32-120">0 to 65,535</span></span>|<span data-ttu-id="c6a32-121">不帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="c6a32-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="c6a32-122">-2,147,483,648 至 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="c6a32-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="c6a32-123">帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="c6a32-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="c6a32-124">0 到 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="c6a32-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="c6a32-125">不帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="c6a32-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="c6a32-126">-9,223,372,036,854,775,808 至 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="c6a32-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="c6a32-127">帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="c6a32-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="c6a32-128">0 到 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="c6a32-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="c6a32-129">不帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="c6a32-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="c6a32-130">在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。</span><span class="sxs-lookup"><span data-stu-id="c6a32-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="c6a32-131">它們是可互換的。</span><span class="sxs-lookup"><span data-stu-id="c6a32-131">They are interchangeable.</span></span> <span data-ttu-id="c6a32-132">例如，下列宣告會宣告相同型別的變數：</span><span class="sxs-lookup"><span data-stu-id="c6a32-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="c6a32-133">每個整數型別的預設值都是零 (`0`)。</span><span class="sxs-lookup"><span data-stu-id="c6a32-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="c6a32-134">每個整數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大值。</span><span class="sxs-lookup"><span data-stu-id="c6a32-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="c6a32-135">使用 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> 結構來表示帶正負號的整數，無上下限。</span><span class="sxs-lookup"><span data-stu-id="c6a32-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="c6a32-136">整數常值</span><span class="sxs-lookup"><span data-stu-id="c6a32-136">Integer literals</span></span>

<span data-ttu-id="c6a32-137">整數文本可以是</span><span class="sxs-lookup"><span data-stu-id="c6a32-137">Integer literals can be</span></span>

- <span data-ttu-id="c6a32-138">*十進位*：沒有任何首碼</span><span class="sxs-lookup"><span data-stu-id="c6a32-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="c6a32-139">*十六進位*：帶`0x`或`0X`首碼</span><span class="sxs-lookup"><span data-stu-id="c6a32-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="c6a32-140">*二進位*： `0b` `0B`帶 或 首碼（在 C# 7.0 及更高版本中提供）</span><span class="sxs-lookup"><span data-stu-id="c6a32-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="c6a32-141">以下代碼演示了每個示例：</span><span class="sxs-lookup"><span data-stu-id="c6a32-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="c6a32-142">前面的示例還顯示`_`用作*數位分隔符號*的用途，該分隔符號支援從 C# 7.0 開始。</span><span class="sxs-lookup"><span data-stu-id="c6a32-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="c6a32-143">您可以將數位分隔符號用於所有類型的數位文本。</span><span class="sxs-lookup"><span data-stu-id="c6a32-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="c6a32-144">整數文本的類型由其後綴確定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6a32-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="c6a32-145">如果文本`int`沒有尾碼，則其類型是可以表示其值的以下類型中的第一個： 、 `uint`、 `long`、 `ulong`、 、 、 、 、 、 、 、 、 、 、 、 、 、</span><span class="sxs-lookup"><span data-stu-id="c6a32-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="c6a32-146">如果文本`U`尾碼于 或`u`，其類型是可以表示其值的以下類型中的第一個： `uint`。 `ulong`</span><span class="sxs-lookup"><span data-stu-id="c6a32-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="c6a32-147">如果文本`L`尾碼于 或`l`，其類型是可以表示其值的以下類型中的第一個： `long`。 `ulong`</span><span class="sxs-lookup"><span data-stu-id="c6a32-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c6a32-148">您可以將小寫字母`l`用作尾碼。</span><span class="sxs-lookup"><span data-stu-id="c6a32-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="c6a32-149">但是，這將生成編譯器警告，因為字母`l`可能會與數位`1`混淆。</span><span class="sxs-lookup"><span data-stu-id="c6a32-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="c6a32-150">用於`L`清楚。</span><span class="sxs-lookup"><span data-stu-id="c6a32-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="c6a32-151">如果文本`UL`尾碼為 、 `Ul`、 `uL`、、、、、、、、、`ul``LU``Lu``lU`其類型為`lu`。 `ulong`</span><span class="sxs-lookup"><span data-stu-id="c6a32-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="c6a32-152">如果整數常值所代表的值超出 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>，就會發生編譯錯誤 [CS1021](../../misc/cs1021.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a32-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="c6a32-153">如果整數文本的確定類型為`int`，並且文本表示的值在目標型別的範圍內，則可以隱式轉換為`sbyte`、、、、、、、、、、、、、`short``ushort``uint``ulong``byte`或 ：</span><span class="sxs-lookup"><span data-stu-id="c6a32-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="c6a32-154">如前面的示例所示，如果文本的值不在目標型別範圍內，則會發生編譯器錯誤[CS0031。](../../misc/cs0031.md)</span><span class="sxs-lookup"><span data-stu-id="c6a32-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="c6a32-155">您還可以使用強制轉換將整數文本表示的值轉換為文本的確定類型以外的類型：</span><span class="sxs-lookup"><span data-stu-id="c6a32-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="c6a32-156">轉換</span><span class="sxs-lookup"><span data-stu-id="c6a32-156">Conversions</span></span>

<span data-ttu-id="c6a32-157">您可以將任何積分數數值型別轉換為任何其他積分數數值型別。</span><span class="sxs-lookup"><span data-stu-id="c6a32-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="c6a32-158">如果目標型別可以存儲源類型的所有值，則轉換是隱式轉換。</span><span class="sxs-lookup"><span data-stu-id="c6a32-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="c6a32-159">否則，您需要使用[強制轉換運算子`()`](../operators/type-testing-and-cast.md#cast-operator-)調用顯式轉換。</span><span class="sxs-lookup"><span data-stu-id="c6a32-159">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="c6a32-160">有關詳細資訊，請參閱[內置數位轉換](numeric-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a32-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c6a32-161">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c6a32-161">C# language specification</span></span>

<span data-ttu-id="c6a32-162">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="c6a32-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c6a32-163">整數型別</span><span class="sxs-lookup"><span data-stu-id="c6a32-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="c6a32-164">整數常值</span><span class="sxs-lookup"><span data-stu-id="c6a32-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="c6a32-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6a32-165">See also</span></span>

- [<span data-ttu-id="c6a32-166">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c6a32-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c6a32-167">實值型別</span><span class="sxs-lookup"><span data-stu-id="c6a32-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="c6a32-168">浮點類型</span><span class="sxs-lookup"><span data-stu-id="c6a32-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="c6a32-169">標準數位格式字串</span><span class="sxs-lookup"><span data-stu-id="c6a32-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="c6a32-170">.NET 中的數值</span><span class="sxs-lookup"><span data-stu-id="c6a32-170">Numerics in .NET</span></span>](../../../standard/numerics.md)
