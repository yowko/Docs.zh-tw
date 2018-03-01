---
title: "int (C# 參考)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7acb8bb482ebf8f5c2b508e7cfd45b5b64aae3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="int-c-reference"></a><span data-ttu-id="32ea4-102">int (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="32ea4-102">int (C# Reference)</span></span>

<span data-ttu-id="32ea4-103">`int` 表示儲存值的整數型別 (以下表所示的大小和範圍為依據)。</span><span class="sxs-lookup"><span data-stu-id="32ea4-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="32ea4-104">類型</span><span class="sxs-lookup"><span data-stu-id="32ea4-104">Type</span></span>|<span data-ttu-id="32ea4-105">範圍</span><span class="sxs-lookup"><span data-stu-id="32ea4-105">Range</span></span>|<span data-ttu-id="32ea4-106">大小</span><span class="sxs-lookup"><span data-stu-id="32ea4-106">Size</span></span>|<span data-ttu-id="32ea4-107">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="32ea4-107">.NET Framework type</span></span>|<span data-ttu-id="32ea4-108">預設值</span><span class="sxs-lookup"><span data-stu-id="32ea4-108">Default Value</span></span>|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|<span data-ttu-id="32ea4-109">-2,147,483,648 至 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="32ea4-109">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="32ea4-110">帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="32ea4-110">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="32ea4-111">0</span><span class="sxs-lookup"><span data-stu-id="32ea4-111">0</span></span>|  
  
## <a name="literals"></a><span data-ttu-id="32ea4-112">常值</span><span class="sxs-lookup"><span data-stu-id="32ea4-112">Literals</span></span>  
 
<span data-ttu-id="32ea4-113">您可以針對 `int` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="32ea4-113">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="32ea4-114">如果整數常值超出 `int` 的範圍 (亦即，如果小於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="32ea4-114">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="32ea4-115">在下列範例中，以十進位、十六進位和二進位常值表示的 90,946 整數，會指派給 `int` 值。</span><span class="sxs-lookup"><span data-stu-id="32ea4-115">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="32ea4-116">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="32ea4-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="32ea4-117">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="32ea4-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="32ea4-118">開始使用 C# 7，已加入一組功能，以提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="32ea4-118">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="32ea4-119">C# 7.0 可讓使用底線字元， `_`，做為千位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="32ea4-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="32ea4-120">可讓 C# 7.2`_`来做為二進位或十六進位常值、 數字分隔符號 after 前置字元。</span><span class="sxs-lookup"><span data-stu-id="32ea4-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="32ea4-121">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="32ea4-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="32ea4-122">某些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="32ea4-122">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="32ea4-123">雖然沒有後置詞可以表示 `int` 類型，但整數常值亦可包含尾碼以表示類型。</span><span class="sxs-lookup"><span data-stu-id="32ea4-123">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="32ea4-124">如果整數常值沒有後置詞，其類型會是下列類型中可表示其值的第一個類型：</span><span class="sxs-lookup"><span data-stu-id="32ea4-124">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="32ea4-125">uint</span><span class="sxs-lookup"><span data-stu-id="32ea4-125">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="32ea4-126">long</span><span class="sxs-lookup"><span data-stu-id="32ea4-126">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="32ea4-127">ulong</span><span class="sxs-lookup"><span data-stu-id="32ea4-127">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="32ea4-128">在上述範例中，常值 90946 為 `int` 類型。</span><span class="sxs-lookup"><span data-stu-id="32ea4-128">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="32ea4-129">轉換</span><span class="sxs-lookup"><span data-stu-id="32ea4-129">Conversions</span></span>  
 <span data-ttu-id="32ea4-130">有一項從 `int` 轉換為 [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="32ea4-130">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="32ea4-131">例如: </span><span class="sxs-lookup"><span data-stu-id="32ea4-131">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="32ea4-132">有一項從 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `int` 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="32ea4-132">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="32ea4-133">例如，下列指派陳述式會在並未進行轉換的情況下產生編譯錯誤：</span><span class="sxs-lookup"><span data-stu-id="32ea4-133">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="32ea4-134">另請注意，沒有從浮點類型轉換為 `int` 的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="32ea4-134">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="32ea4-135">例如，除非使用明確轉換，否則下列陳述式會產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="32ea4-135">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="32ea4-136">如需混合浮點類型和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="32ea4-136">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="32ea4-137">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="32ea4-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="32ea4-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32ea4-138">See Also</span></span>  
 <xref:System.Int32>  
 [<span data-ttu-id="32ea4-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="32ea4-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="32ea4-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="32ea4-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="32ea4-141">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="32ea4-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="32ea4-142">整數型別表</span><span class="sxs-lookup"><span data-stu-id="32ea4-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="32ea4-143">內建型別表</span><span class="sxs-lookup"><span data-stu-id="32ea4-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="32ea4-144">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="32ea4-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="32ea4-145">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="32ea4-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
