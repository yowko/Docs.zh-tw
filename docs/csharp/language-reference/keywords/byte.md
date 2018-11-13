---
title: byte (C# 參考)
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: d952f56df62aa3a53e3889baa65c491e1a0fc81e
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "43505091"
---
# <a name="byte-c-reference"></a><span data-ttu-id="38989-102">byte (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="38989-102">byte (C# Reference)</span></span>

<span data-ttu-id="38989-103">`byte` 表示用來儲存下表所指出值的整數型別。</span><span class="sxs-lookup"><span data-stu-id="38989-103">`byte` denotes an integral type that stores values as indicated in the following table.</span></span>  
  
|<span data-ttu-id="38989-104">類型</span><span class="sxs-lookup"><span data-stu-id="38989-104">Type</span></span>|<span data-ttu-id="38989-105">範圍</span><span class="sxs-lookup"><span data-stu-id="38989-105">Range</span></span>|<span data-ttu-id="38989-106">大小</span><span class="sxs-lookup"><span data-stu-id="38989-106">Size</span></span>|<span data-ttu-id="38989-107">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="38989-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`byte`|<span data-ttu-id="38989-108">0 到 255</span><span class="sxs-lookup"><span data-stu-id="38989-108">0 to 255</span></span>|<span data-ttu-id="38989-109">不帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="38989-109">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="38989-110">常值</span><span class="sxs-lookup"><span data-stu-id="38989-110">Literals</span></span>  

 <span data-ttu-id="38989-111">您可以針對 `byte` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="38989-111">You can declare and initialize a `byte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="38989-112">如果整數常值超出 `byte` 的範圍 (亦即，如果小於 <xref:System.Byte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Byte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="38989-112">If the integer literal is outside the range of `byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="38989-113">在下列範例中，以十進位、十六進位和二進位常值表示的 201 整數，從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換成 `byte` 值。</span><span class="sxs-lookup"><span data-stu-id="38989-113">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `byte` values.</span></span>    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> <span data-ttu-id="38989-114">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="38989-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="38989-115">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="38989-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="38989-116">從 C# 7.0 開始，已新增一組功能來提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="38989-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="38989-117">C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="38989-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="38989-118">C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="38989-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="38989-119">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="38989-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="38989-120">一些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="38989-120">Some examples are shown below.</span></span>

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a><span data-ttu-id="38989-121">轉換</span><span class="sxs-lookup"><span data-stu-id="38989-121">Conversions</span></span>  
 <span data-ttu-id="38989-122">有一項從 `byte` 轉換為 [short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="38989-122">There is a predefined implicit conversion from `byte` to [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="38989-123">您無法將較大儲存大小的非常值數字類型隱含轉換為 `byte`。</span><span class="sxs-lookup"><span data-stu-id="38989-123">You cannot implicitly convert non-literal numeric types of larger storage size to `byte`.</span></span> <span data-ttu-id="38989-124">如需整數型別儲存大小的詳細資訊，請參閱[整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="38989-124">For more information on the storage sizes of integral types, see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md).</span></span> <span data-ttu-id="38989-125">例如，請考慮使用下列兩個 `byte` 變數 `x` 和 `y`：</span><span class="sxs-lookup"><span data-stu-id="38989-125">Consider, for example, the following two `byte` variables `x` and `y`:</span></span>  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 <span data-ttu-id="38989-126">因為指派運算子右側的算術運算式預設會評估為 `int`，所以下列指派陳述式將會產生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="38989-126">The following assignment statement will produce a compilation error, because the arithmetic expression on the right-hand side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 <span data-ttu-id="38989-127">若要修正這個問題，請使用轉換：</span><span class="sxs-lookup"><span data-stu-id="38989-127">To fix this problem, use a cast:</span></span>  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 <span data-ttu-id="38989-128">不過，可以使用目的地變數具有相同或較大儲存大小的下列陳述式︰</span><span class="sxs-lookup"><span data-stu-id="38989-128">It is possible though, to use the following statements where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="38989-129">同時，沒有從浮點類型轉換為 `byte` 的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="38989-129">Also, there is no implicit conversion from floating-point types to `byte`.</span></span> <span data-ttu-id="38989-130">例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="38989-130">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 <span data-ttu-id="38989-131">呼叫多載的方法時，必須使用轉型。</span><span class="sxs-lookup"><span data-stu-id="38989-131">When calling overloaded methods, a cast must be used.</span></span> <span data-ttu-id="38989-132">例如，請考慮使用下列使用 `byte` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：</span><span class="sxs-lookup"><span data-stu-id="38989-132">Consider, for example, the following overloaded methods that use `byte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 <span data-ttu-id="38989-133">使用 `byte` 轉型時，可以保證呼叫正確的類型，例如：</span><span class="sxs-lookup"><span data-stu-id="38989-133">Using the `byte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 <span data-ttu-id="38989-134">如需混合浮點類型和整數型別之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="38989-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="38989-135">如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="38989-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="38989-136">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="38989-136">C# Language Specification</span></span>  

<span data-ttu-id="38989-137">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[整數型別](~/_csharplang/spec/types.md#integral-types)。</span><span class="sxs-lookup"><span data-stu-id="38989-137">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="38989-138">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="38989-138">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="38989-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="38989-139">See Also</span></span>  

- <xref:System.Byte>  
- [<span data-ttu-id="38989-140">C# 參考</span><span class="sxs-lookup"><span data-stu-id="38989-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="38989-141">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="38989-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="38989-142">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="38989-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="38989-143">整數型別表</span><span class="sxs-lookup"><span data-stu-id="38989-143">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="38989-144">內建型別表</span><span class="sxs-lookup"><span data-stu-id="38989-144">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="38989-145">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="38989-145">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="38989-146">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="38989-146">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
