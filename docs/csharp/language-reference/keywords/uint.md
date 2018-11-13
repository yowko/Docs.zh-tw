---
title: uint (C# 參考)
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
ms.openlocfilehash: c8610d13a97e672773fdf80d013a159a58e7cfbf
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "50744324"
---
# <a name="uint-c-reference"></a><span data-ttu-id="3f40c-102">uint (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3f40c-102">uint (C# Reference)</span></span>

<span data-ttu-id="3f40c-103">`uint` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數型別。</span><span class="sxs-lookup"><span data-stu-id="3f40c-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="3f40c-104">類型</span><span class="sxs-lookup"><span data-stu-id="3f40c-104">Type</span></span>|<span data-ttu-id="3f40c-105">範圍</span><span class="sxs-lookup"><span data-stu-id="3f40c-105">Range</span></span>|<span data-ttu-id="3f40c-106">大小</span><span class="sxs-lookup"><span data-stu-id="3f40c-106">Size</span></span>|<span data-ttu-id="3f40c-107">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="3f40c-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`uint`|<span data-ttu-id="3f40c-108">0 到 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="3f40c-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="3f40c-109">不帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="3f40c-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 <span data-ttu-id="3f40c-110">**注意** `uint`類型不符合 CLS 規範。</span><span class="sxs-lookup"><span data-stu-id="3f40c-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="3f40c-111">請盡可能使用 `int`。</span><span class="sxs-lookup"><span data-stu-id="3f40c-111">Use `int` whenever possible.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="3f40c-112">常值</span><span class="sxs-lookup"><span data-stu-id="3f40c-112">Literals</span></span>  

<span data-ttu-id="3f40c-113">您可以針對 `uint` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="3f40c-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="3f40c-114">如果整數常值超出 `uint` 的範圍 (亦即，如果小於 <xref:System.UInt32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="3f40c-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="3f40c-115">在下列範例中，以十進位、十六進位和二進位常值表示的 3,000,000,000 整數，會指派給 `uint` 值。</span><span class="sxs-lookup"><span data-stu-id="3f40c-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> <span data-ttu-id="3f40c-116">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="3f40c-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="3f40c-117">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="3f40c-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="3f40c-118">從 C# 7.0 開始，已新增一組功能來提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="3f40c-118">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="3f40c-119">C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3f40c-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="3f40c-120">C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3f40c-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="3f40c-121">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="3f40c-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="3f40c-122">一些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="3f40c-122">Some examples are shown below.</span></span>

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 <span data-ttu-id="3f40c-123">整數常值亦可包含後置詞以表示類型。</span><span class="sxs-lookup"><span data-stu-id="3f40c-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="3f40c-124">`U` 或 'u' 後置詞表示 `uint` 或 `ulong`，視常值的數值而定。</span><span class="sxs-lookup"><span data-stu-id="3f40c-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="3f40c-125">下列範例會使用 `u` 後置詞來表示這兩種類型的不帶正負號整數。</span><span class="sxs-lookup"><span data-stu-id="3f40c-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="3f40c-126">請注意，第一個常值是 `uint`，因為其值小於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>而第二個是 `ulong`，因為其值大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3f40c-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
<span data-ttu-id="3f40c-127">如果整數常值沒有後置詞，其類型會是下列類型中可表示其值的第一個類型：</span><span class="sxs-lookup"><span data-stu-id="3f40c-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="3f40c-128">int</span><span class="sxs-lookup"><span data-stu-id="3f40c-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="3f40c-129">long</span><span class="sxs-lookup"><span data-stu-id="3f40c-129">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="3f40c-130">ulong</span><span class="sxs-lookup"><span data-stu-id="3f40c-130">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a><span data-ttu-id="3f40c-131">轉換</span><span class="sxs-lookup"><span data-stu-id="3f40c-131">Conversions</span></span>  
 <span data-ttu-id="3f40c-132">有一項從 `uint` 轉換為 [long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="3f40c-132">There is a predefined implicit conversion from `uint` to [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="3f40c-133">例如: </span><span class="sxs-lookup"><span data-stu-id="3f40c-133">For example:</span></span>  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 <span data-ttu-id="3f40c-134">有一項從 [byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `uint` 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="3f40c-134">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `uint`.</span></span> <span data-ttu-id="3f40c-135">否則，您必須使用轉換。</span><span class="sxs-lookup"><span data-stu-id="3f40c-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="3f40c-136">例如，下列指派陳述式會在未進行轉換的情況下產生編譯錯誤：</span><span class="sxs-lookup"><span data-stu-id="3f40c-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 <span data-ttu-id="3f40c-137">另請注意，沒有從浮點類型轉換為 `uint` 的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="3f40c-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="3f40c-138">例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="3f40c-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 <span data-ttu-id="3f40c-139">如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="3f40c-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="3f40c-140">如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="3f40c-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f40c-141">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3f40c-141">C# Language Specification</span></span>  

<span data-ttu-id="3f40c-142">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[整數型別](~/_csharplang/spec/types.md#integral-types)。</span><span class="sxs-lookup"><span data-stu-id="3f40c-142">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="3f40c-143">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="3f40c-143">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3f40c-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="3f40c-144">See Also</span></span>

- <xref:System.UInt32>  
- [<span data-ttu-id="3f40c-145">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3f40c-145">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3f40c-146">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3f40c-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3f40c-147">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="3f40c-147">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="3f40c-148">整數型別表</span><span class="sxs-lookup"><span data-stu-id="3f40c-148">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="3f40c-149">內建型別表</span><span class="sxs-lookup"><span data-stu-id="3f40c-149">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="3f40c-150">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="3f40c-150">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="3f40c-151">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="3f40c-151">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
