---
title: "ushort (C# 參考)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords: ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 83fa657303e8392997b04b7d80cdbcdbf39de887
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-c-reference"></a><span data-ttu-id="45d49-102">ushort (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="45d49-102">ushort (C# Reference)</span></span>

<span data-ttu-id="45d49-103">`ushort` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數資料類型。</span><span class="sxs-lookup"><span data-stu-id="45d49-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="45d49-104">類型</span><span class="sxs-lookup"><span data-stu-id="45d49-104">Type</span></span>|<span data-ttu-id="45d49-105">範圍</span><span class="sxs-lookup"><span data-stu-id="45d49-105">Range</span></span>|<span data-ttu-id="45d49-106">大小</span><span class="sxs-lookup"><span data-stu-id="45d49-106">Size</span></span>|<span data-ttu-id="45d49-107">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="45d49-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ushort`|<span data-ttu-id="45d49-108">0 到 65,535</span><span class="sxs-lookup"><span data-stu-id="45d49-108">0 to 65,535</span></span>|<span data-ttu-id="45d49-109">不帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="45d49-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="45d49-110">常值</span><span class="sxs-lookup"><span data-stu-id="45d49-110">Literals</span></span>  

<span data-ttu-id="45d49-111">您可以針對 `ushort` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="45d49-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="45d49-112">如果整數常值超出 `ushort` 的範圍 (亦即，如果小於 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="45d49-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="45d49-113">在下列範例中，以十進位、十六進位和二進位常值表示的 65,034 整數，從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換成 `ushort` 值。</span><span class="sxs-lookup"><span data-stu-id="45d49-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `ushort` values.</span></span>    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> <span data-ttu-id="45d49-114">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="45d49-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="45d49-115">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="45d49-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="45d49-116">開始使用 C# 7，已加入一組功能，以提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="45d49-116">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="45d49-117">C# 7.0 可讓使用底線字元， `_`，做為千位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="45d49-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="45d49-118">可讓 C# 7.2`_`来做為二進位或十六進位常值、 數字分隔符號 after 前置字元。</span><span class="sxs-lookup"><span data-stu-id="45d49-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="45d49-119">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="45d49-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="45d49-120">某些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="45d49-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="45d49-121">編譯器多載解析</span><span class="sxs-lookup"><span data-stu-id="45d49-121">Compiler overload resolution</span></span>
  
 <span data-ttu-id="45d49-122">當您呼叫多載方法時，必須使用轉換。</span><span class="sxs-lookup"><span data-stu-id="45d49-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="45d49-123">例如，請考慮使用下列使用 `ushort` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：</span><span class="sxs-lookup"><span data-stu-id="45d49-123">Consider, for example, the following overloaded methods that use `ushort` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 <span data-ttu-id="45d49-124">使用 `ushort` 轉型時，可以保證呼叫正確的類型，例如：</span><span class="sxs-lookup"><span data-stu-id="45d49-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a><span data-ttu-id="45d49-125">轉換</span><span class="sxs-lookup"><span data-stu-id="45d49-125">Conversions</span></span>  
 <span data-ttu-id="45d49-126">有一項從 `ushort` 轉換為 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="45d49-126">There is a predefined implicit conversion from `ushort` to [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="45d49-127">有一項從 [byte](../../../csharp/language-reference/keywords/byte.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `ushort` 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="45d49-127">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md) or [char](../../../csharp/language-reference/keywords/char.md) to `ushort`.</span></span> <span data-ttu-id="45d49-128">否則必須使用轉換來執行明確轉換。</span><span class="sxs-lookup"><span data-stu-id="45d49-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="45d49-129">例如，請考慮使用下列兩個 `ushort` 變數 `x` 和 `y`：</span><span class="sxs-lookup"><span data-stu-id="45d49-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 <span data-ttu-id="45d49-130">因為指派運算子右邊的算術運算式預設會評估為 `int`，所以下列指派陳述式將會產生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="45d49-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 <span data-ttu-id="45d49-131">若要修正這個問題，請使用轉換：</span><span class="sxs-lookup"><span data-stu-id="45d49-131">To fix this problem, use a cast:</span></span>  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 <span data-ttu-id="45d49-132">不過，可以使用目的地變數具有相同或較大儲存大小的下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="45d49-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="45d49-133">另請注意，不會從浮點類型隱含地轉換為 `ushort`。</span><span class="sxs-lookup"><span data-stu-id="45d49-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="45d49-134">例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="45d49-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 <span data-ttu-id="45d49-135">如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="45d49-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="45d49-136">如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="45d49-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="45d49-137">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="45d49-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45d49-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45d49-138">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="45d49-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="45d49-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="45d49-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="45d49-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="45d49-141">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="45d49-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="45d49-142">整數型別表</span><span class="sxs-lookup"><span data-stu-id="45d49-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="45d49-143">內建型別表</span><span class="sxs-lookup"><span data-stu-id="45d49-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="45d49-144">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="45d49-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="45d49-145">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="45d49-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
