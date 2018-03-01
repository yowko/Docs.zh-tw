---
title: "sbyte (C# 參考)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 010ac98f523eca5929100f7c51b8b6ef5d11de30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-c-reference"></a><span data-ttu-id="f7a57-102">sbyte (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f7a57-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="f7a57-103">`sbyte` 表示儲存值的整數型別 (以下表所示的大小和範圍為依據)。</span><span class="sxs-lookup"><span data-stu-id="f7a57-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="f7a57-104">類型</span><span class="sxs-lookup"><span data-stu-id="f7a57-104">Type</span></span>|<span data-ttu-id="f7a57-105">範圍</span><span class="sxs-lookup"><span data-stu-id="f7a57-105">Range</span></span>|<span data-ttu-id="f7a57-106">大小</span><span class="sxs-lookup"><span data-stu-id="f7a57-106">Size</span></span>|<span data-ttu-id="f7a57-107">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="f7a57-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="f7a57-108">-128 到 127</span><span class="sxs-lookup"><span data-stu-id="f7a57-108">-128 to 127</span></span>|<span data-ttu-id="f7a57-109">帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="f7a57-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="f7a57-110">常值</span><span class="sxs-lookup"><span data-stu-id="f7a57-110">Literals</span></span>  

<span data-ttu-id="f7a57-111">您可以針對 `sbyte` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="f7a57-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="f7a57-112">下列範例會將以十進位、十六進位和二進位常值表示的 -102 整數，從 [int](../../../csharp/language-reference/keywords/int.md) 轉換成 `sbyte` 值。</span><span class="sxs-lookup"><span data-stu-id="f7a57-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> <span data-ttu-id="f7a57-113">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="f7a57-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="f7a57-114">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="f7a57-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="f7a57-115">開始使用 C# 7，已加入一組功能，以提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="f7a57-115">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="f7a57-116">C# 7.0 可讓使用底線字元， `_`，做為千位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="f7a57-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="f7a57-117">可讓 C# 7.2`_`来做為二進位或十六進位常值、 數字分隔符號 after 前置字元。</span><span class="sxs-lookup"><span data-stu-id="f7a57-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="f7a57-118">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="f7a57-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

 <span data-ttu-id="f7a57-119">某些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="f7a57-119">Some examples are shown below.</span></span>

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

<span data-ttu-id="f7a57-120">如果整數常值超出 `sbyte` 的範圍 (亦即，如果小於 <xref:System.SByte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.SByte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="f7a57-120">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="f7a57-121">整數常值沒有後置詞時，其類型會是下列類型中可表示其值的第一個類型：[int](int.md)、[uint](uint.md)、[long](long.md)、[ulong](ulong.md)。</span><span class="sxs-lookup"><span data-stu-id="f7a57-121">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="f7a57-122">這表示，此範例會將數值常值 `0x9A` 和 `0b10011010` 解譯為 32 位元帶正負號的整數值 156，而該值已超過 <xref:System.SByte.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f7a57-122">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7a57-123">因此，您需要使用轉型運算子，且作業必須發生在 [unchecked](unchecked.md) 內容中。</span><span class="sxs-lookup"><span data-stu-id="f7a57-123">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="f7a57-124">編譯器多載解析</span><span class="sxs-lookup"><span data-stu-id="f7a57-124">Compiler overload resolution</span></span>

 <span data-ttu-id="f7a57-125">呼叫多載的方法時，必須使用轉型。</span><span class="sxs-lookup"><span data-stu-id="f7a57-125">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="f7a57-126">例如，請考慮使用下列使用 `sbyte` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：</span><span class="sxs-lookup"><span data-stu-id="f7a57-126">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="f7a57-127">使用 `sbyte` 轉型時，可以保證呼叫正確的類型，例如：</span><span class="sxs-lookup"><span data-stu-id="f7a57-127">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="f7a57-128">轉換</span><span class="sxs-lookup"><span data-stu-id="f7a57-128">Conversions</span></span>  
 <span data-ttu-id="f7a57-129">有一項從 `sbyte` 轉換為 [short](../../../csharp/language-reference/keywords/short.md)、[int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="f7a57-129">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="f7a57-130">您不能將較大儲存大小的非常值數字類型隱含轉換為 `sbyte` (如需整數類型的儲存大小，請參閱[整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md))。</span><span class="sxs-lookup"><span data-stu-id="f7a57-130">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="f7a57-131">例如，請考慮使用下列兩個 `sbyte` 變數 `x` 和 `y`：</span><span class="sxs-lookup"><span data-stu-id="f7a57-131">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="f7a57-132">因為指派運算子右側的算術運算式預設會評估為 [int](../../../csharp/language-reference/keywords/int.md)，所以下列指派陳述式將會產生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="f7a57-132">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="f7a57-133">若要修正這個問題，請轉型運算式，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="f7a57-133">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="f7a57-134">不過，可以使用目的地變數具有相同或較大儲存大小的下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="f7a57-134">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="f7a57-135">另請注意，不會從浮點類型隱含地轉換為 `sbyte`。</span><span class="sxs-lookup"><span data-stu-id="f7a57-135">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="f7a57-136">例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="f7a57-136">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="f7a57-137">如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="f7a57-137">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="f7a57-138">如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="f7a57-138">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f7a57-139">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f7a57-139">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f7a57-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7a57-140">See Also</span></span>  
 <xref:System.SByte>  
 [<span data-ttu-id="f7a57-141">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f7a57-141">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f7a57-142">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f7a57-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f7a57-143">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f7a57-143">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f7a57-144">整數型別表</span><span class="sxs-lookup"><span data-stu-id="f7a57-144">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="f7a57-145">內建型別表</span><span class="sxs-lookup"><span data-stu-id="f7a57-145">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="f7a57-146">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="f7a57-146">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="f7a57-147">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="f7a57-147">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
