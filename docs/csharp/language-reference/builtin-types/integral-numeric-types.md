---
title: 整數的數字型別 - C# 參考
description: 了解每個整數數字型別的範圍、儲存體大小和用法。
ms.date: 06/25/2019
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
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236081"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="44692-103">整數的數字型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="44692-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="44692-104">**整數數字型別**是**簡單型別**的子集，且可使用[*常值*](#integral-literals)初始化。</span><span class="sxs-lookup"><span data-stu-id="44692-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="44692-105">所有的整數型別也都是實值型別。</span><span class="sxs-lookup"><span data-stu-id="44692-105">All integral types are also value types.</span></span> <span data-ttu-id="44692-106">所有整數的數字型別都支援[算術](../operators/arithmetic-operators.md)、[位元邏輯](../operators/bitwise-and-shift-operators.md)、[比較和等號](../operators/equality-operators.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="44692-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="44692-107">整數型別的特性</span><span class="sxs-lookup"><span data-stu-id="44692-107">Characteristics of the integral types</span></span>

<span data-ttu-id="44692-108">C# 支援下列預先定義的整數型別：</span><span class="sxs-lookup"><span data-stu-id="44692-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="44692-109">C# 型別/關鍵字</span><span class="sxs-lookup"><span data-stu-id="44692-109">C# type/keyword</span></span>|<span data-ttu-id="44692-110">範圍</span><span class="sxs-lookup"><span data-stu-id="44692-110">Range</span></span>|<span data-ttu-id="44692-111">大小</span><span class="sxs-lookup"><span data-stu-id="44692-111">Size</span></span>|<span data-ttu-id="44692-112">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="44692-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="44692-113">-128 到 127</span><span class="sxs-lookup"><span data-stu-id="44692-113">-128 to 127</span></span>|<span data-ttu-id="44692-114">帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="44692-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="44692-115">0 到 255</span><span class="sxs-lookup"><span data-stu-id="44692-115">0 to 255</span></span>|<span data-ttu-id="44692-116">不帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="44692-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="44692-117">-32,768 到 32,767</span><span class="sxs-lookup"><span data-stu-id="44692-117">-32,768 to 32,767</span></span>|<span data-ttu-id="44692-118">帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="44692-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="44692-119">0 到 65,535</span><span class="sxs-lookup"><span data-stu-id="44692-119">0 to 65,535</span></span>|<span data-ttu-id="44692-120">不帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="44692-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="44692-121">-2,147,483,648 至 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="44692-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="44692-122">帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="44692-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="44692-123">0 到 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="44692-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="44692-124">不帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="44692-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="44692-125">-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="44692-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="44692-126">帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="44692-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="44692-127">0 到 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="44692-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="44692-128">不帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="44692-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="44692-129">在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。</span><span class="sxs-lookup"><span data-stu-id="44692-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="44692-130">它們是可互換的。</span><span class="sxs-lookup"><span data-stu-id="44692-130">They are interchangeable.</span></span> <span data-ttu-id="44692-131">例如，下列宣告會宣告相同型別的變數：</span><span class="sxs-lookup"><span data-stu-id="44692-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="44692-132">每個整數型別的預設值都是零 (`0`)。</span><span class="sxs-lookup"><span data-stu-id="44692-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="44692-133">每個整數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大值。</span><span class="sxs-lookup"><span data-stu-id="44692-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="44692-134">使用 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> 結構來表示帶正負號的整數，無上下限。</span><span class="sxs-lookup"><span data-stu-id="44692-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="44692-135">整數常值</span><span class="sxs-lookup"><span data-stu-id="44692-135">Integral literals</span></span>

<span data-ttu-id="44692-136">整數常值可指定為*十進位常值*、*十六進位常值*或*二進位常值*。</span><span class="sxs-lookup"><span data-stu-id="44692-136">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="44692-137">各自的範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="44692-137">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="44692-138">十進位常值不需要任何前置詞。</span><span class="sxs-lookup"><span data-stu-id="44692-138">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="44692-139">`x` 或 `X` 前置詞表示*十六進位常值*。</span><span class="sxs-lookup"><span data-stu-id="44692-139">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="44692-140">`b` 或 `B` 前置詞表示*二進位常值*。</span><span class="sxs-lookup"><span data-stu-id="44692-140">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="44692-141">`binaryLiteral` 宣告示範使用 `_` 作為*數字分隔符號*。</span><span class="sxs-lookup"><span data-stu-id="44692-141">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="44692-142">數字分隔符號可搭配所有數字常值使用。</span><span class="sxs-lookup"><span data-stu-id="44692-142">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="44692-143">自 C# 7.0 開始，支援二進位常值和數字分隔符號 `_`。</span><span class="sxs-lookup"><span data-stu-id="44692-143">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

### <a name="literal-suffixes"></a><span data-ttu-id="44692-144">常值後置詞</span><span class="sxs-lookup"><span data-stu-id="44692-144">Literal suffixes</span></span>

<span data-ttu-id="44692-145">`l` 或 `L` 後置詞會指定整數常值應為 `long` 型別。</span><span class="sxs-lookup"><span data-stu-id="44692-145">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="44692-146">`ul` 或 `UL` 後置詞指定 `ulong` 型別。</span><span class="sxs-lookup"><span data-stu-id="44692-146">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="44692-147">如果大於 9,223,372,036,854,775,807 的常值使用 `L` 後置詞 (`long` 的最大值)，則該值會轉換成 `ulong` 型別。</span><span class="sxs-lookup"><span data-stu-id="44692-147">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="44692-148">如果整數常值所代表的值超出 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>，就會發生編譯錯誤 [CS1021](../../misc/cs1021.md)。</span><span class="sxs-lookup"><span data-stu-id="44692-148">If the value represented by an integral literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="44692-149">您可以使用小寫字母 "l" 作為後置詞。</span><span class="sxs-lookup"><span data-stu-id="44692-149">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="44692-150">不過，因為字母 "l" 很容易與數字 "1" 混淆，所以這會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="44692-150">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="44692-151">為了清楚起見，請使用 "L"。</span><span class="sxs-lookup"><span data-stu-id="44692-151">Use "L" for clarity.</span></span>

### <a name="type-of-an-integral-literal"></a><span data-ttu-id="44692-152">整數常值的型別</span><span class="sxs-lookup"><span data-stu-id="44692-152">Type of an integral literal</span></span>

<span data-ttu-id="44692-153">如果整數常值沒有後置詞，則其型別會是下列可表示值型別中的第一個：</span><span class="sxs-lookup"><span data-stu-id="44692-153">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="44692-154">您可以使用指派或轉換，將整數常值轉換成範圍比預設小的型別：</span><span class="sxs-lookup"><span data-stu-id="44692-154">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="44692-155">您可以使用指派、轉換或常數後置詞，將整數常值轉換成範圍比預設大的型別：</span><span class="sxs-lookup"><span data-stu-id="44692-155">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="44692-156">轉換</span><span class="sxs-lookup"><span data-stu-id="44692-156">Conversions</span></span>

<span data-ttu-id="44692-157">在目的地型別可以儲存來源型別全部值的整數型別中，任兩者之間都具有隱含轉換 (稱為「擴展轉換」  )。</span><span class="sxs-lookup"><span data-stu-id="44692-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="44692-158">例如，`int` 到 `long` 有隱含轉換，因為 `int` 值範圍是適當的 `long` 子集。</span><span class="sxs-lookup"><span data-stu-id="44692-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="44692-159">較小的不帶正負號整數型別可隱含轉換成較大帶正負號整數型別。</span><span class="sxs-lookup"><span data-stu-id="44692-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="44692-160">任一整數型別也皆可隱含轉換成任一浮點型別。</span><span class="sxs-lookup"><span data-stu-id="44692-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="44692-161">任一帶正負號的整數型別不會隱含轉換成任一不帶正負號的整數型別。</span><span class="sxs-lookup"><span data-stu-id="44692-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="44692-162">當來源型別未定義隱含轉換成目的地型別時，您必須使用明確轉換將一種整數型別轉換成另一種整數型別。</span><span class="sxs-lookup"><span data-stu-id="44692-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="44692-163">這稱為「縮小轉換」  。</span><span class="sxs-lookup"><span data-stu-id="44692-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="44692-164">因為轉換會導致資料遺失，所以需要明確轉換。</span><span class="sxs-lookup"><span data-stu-id="44692-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="44692-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44692-165">See also</span></span>

- [<span data-ttu-id="44692-166">C# 語言規格 - 整數型別</span><span class="sxs-lookup"><span data-stu-id="44692-166">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="44692-167">C# 參考</span><span class="sxs-lookup"><span data-stu-id="44692-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="44692-168">浮點類型</span><span class="sxs-lookup"><span data-stu-id="44692-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="44692-169">預設值表</span><span class="sxs-lookup"><span data-stu-id="44692-169">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="44692-170">格式化數值結果表</span><span class="sxs-lookup"><span data-stu-id="44692-170">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="44692-171">內建型別表</span><span class="sxs-lookup"><span data-stu-id="44692-171">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="44692-172">.NET 中的數值</span><span class="sxs-lookup"><span data-stu-id="44692-172">Numerics in .NET</span></span>](../../../standard/numerics.md)
