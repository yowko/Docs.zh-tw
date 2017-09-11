---
title: "byte (C# 參考) | Microsoft Docs"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- byte
- byte_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 25b6f54ea7a6e83f081963bb1903f358a6884f74
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="byte-c-reference"></a><span data-ttu-id="7c756-102">byte (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7c756-102">byte (C# Reference)</span></span>

<span data-ttu-id="7c756-103">`byte` 表示用來儲存下表所指出值的整數型別。</span><span class="sxs-lookup"><span data-stu-id="7c756-103">`byte` denotes an integral type that stores values as indicated in the following table.</span></span>  
  
|<span data-ttu-id="7c756-104">類型</span><span class="sxs-lookup"><span data-stu-id="7c756-104">Type</span></span>|<span data-ttu-id="7c756-105">範圍</span><span class="sxs-lookup"><span data-stu-id="7c756-105">Range</span></span>|<span data-ttu-id="7c756-106">大小</span><span class="sxs-lookup"><span data-stu-id="7c756-106">Size</span></span>|<span data-ttu-id="7c756-107">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="7c756-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`byte`|<span data-ttu-id="7c756-108">0 到 255</span><span class="sxs-lookup"><span data-stu-id="7c756-108">0 to 255</span></span>|<span data-ttu-id="7c756-109">不帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="7c756-109">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="7c756-110">常值</span><span class="sxs-lookup"><span data-stu-id="7c756-110">Literals</span></span>  

 <span data-ttu-id="7c756-111">您可以針對 `byte` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="7c756-111">You can declare and initialize a `byte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="7c756-112">如果整數常值超出 `byte` 的範圍 (亦即，如果小於 <xref:System.Byte.MinValue?displayProperty=fullName> 或大於 <xref:System.Byte.MaxValue?displayProperty=fullName>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="7c756-112">If the integer literal is outside the range of `byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=fullName> or greater than <xref:System.Byte.MaxValue?displayProperty=fullName>, a compilation error occurs.</span></span>

<span data-ttu-id="7c756-113">在下列範例中，以十進位、十六進位和二進位常值表示的 201 整數，從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換成 `byte` 值。</span><span class="sxs-lookup"><span data-stu-id="7c756-113">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `byte` values.</span></span>    
  
<span data-ttu-id="7c756-114">[!code-cs[位元組](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]</span><span class="sxs-lookup"><span data-stu-id="7c756-114">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="7c756-115">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="7c756-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="7c756-116">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="7c756-116">Decimal literals have no prefix.</span></span>

<span data-ttu-id="7c756-117">自 C# 7 開始，您也可以使用底線字元 `_` 作為數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7c756-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="7c756-118">[!code-cs[位元組](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]</span><span class="sxs-lookup"><span data-stu-id="7c756-118">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]</span></span>  
 
## <a name="conversions"></a><span data-ttu-id="7c756-119">轉換</span><span class="sxs-lookup"><span data-stu-id="7c756-119">Conversions</span></span>  
 <span data-ttu-id="7c756-120">有一項從 `byte` 轉換為 [short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="7c756-120">There is a predefined implicit conversion from `byte` to [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="7c756-121">您無法將較大儲存大小的非常值數字類型隱含轉換為 `byte`。</span><span class="sxs-lookup"><span data-stu-id="7c756-121">You cannot implicitly convert non-literal numeric types of larger storage size to `byte`.</span></span> <span data-ttu-id="7c756-122">如需整數型別儲存大小的詳細資訊，請參閱[整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="7c756-122">For more information on the storage sizes of integral types, see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md).</span></span> <span data-ttu-id="7c756-123">例如，請考慮使用下列兩個 `byte` 變數 `x` 和 `y`：</span><span class="sxs-lookup"><span data-stu-id="7c756-123">Consider, for example, the following two `byte` variables `x` and `y`:</span></span>  
  
```  
byte x = 10, y = 20;  
```  
  
 <span data-ttu-id="7c756-124">因為指派運算子右側的算術運算式預設會評估為 `int`，所以下列指派陳述式將會產生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="7c756-124">The following assignment statement will produce a compilation error, because the arithmetic expression on the right-hand side of the assignment operator evaluates to `int` by default.</span></span>  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 <span data-ttu-id="7c756-125">若要修正這個問題，請使用轉型：</span><span class="sxs-lookup"><span data-stu-id="7c756-125">To fix this problem, use a cast:</span></span>  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 <span data-ttu-id="7c756-126">不過，可以使用目的地變數具有相同或較大儲存大小的下列陳述式︰</span><span class="sxs-lookup"><span data-stu-id="7c756-126">It is possible though, to use the following statements where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="7c756-127">同時，沒有從浮點類型轉換為 `byte` 的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="7c756-127">Also, there is no implicit conversion from floating-point types to `byte`.</span></span> <span data-ttu-id="7c756-128">例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="7c756-128">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 <span data-ttu-id="7c756-129">呼叫多載的方法時，必須使用轉型。</span><span class="sxs-lookup"><span data-stu-id="7c756-129">When calling overloaded methods, a cast must be used.</span></span> <span data-ttu-id="7c756-130">例如，假設下列使用 `byte` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：</span><span class="sxs-lookup"><span data-stu-id="7c756-130">Consider, for example, the following overloaded methods that use `byte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 <span data-ttu-id="7c756-131">使用 `byte` 轉型時，可以保證呼叫正確的類型，例如：</span><span class="sxs-lookup"><span data-stu-id="7c756-131">Using the `byte` cast guarantees that the correct type is called, for example:</span></span>  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 <span data-ttu-id="7c756-132">如需混合浮點類型和整數型別之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="7c756-132">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="7c756-133">如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="7c756-133">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7c756-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="7c756-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7c756-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c756-135">See Also</span></span>  
 <xref:System.Byte>   
<span data-ttu-id="7c756-136"> [C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7c756-136"> [C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="7c756-137"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7c756-137"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="7c756-138"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="7c756-138"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="7c756-139"> [整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="7c756-139"> [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="7c756-140"> [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="7c756-140"> [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="7c756-141"> [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="7c756-141"> [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
<span data-ttu-id="7c756-142"> [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)</span><span class="sxs-lookup"><span data-stu-id="7c756-142"> [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)</span></span>

