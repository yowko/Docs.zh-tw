---
title: "short (C# 參考) | Microsoft Docs"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: 17
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
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 14f9c66bb620e2ad35513abeeba77372904cc1f3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="short-c-reference"></a><span data-ttu-id="dc553-102">short (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="dc553-102">short (C# Reference)</span></span>

<span data-ttu-id="dc553-103">`short` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數資料型別。</span><span class="sxs-lookup"><span data-stu-id="dc553-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="dc553-104">類型</span><span class="sxs-lookup"><span data-stu-id="dc553-104">Type</span></span>|<span data-ttu-id="dc553-105">範圍</span><span class="sxs-lookup"><span data-stu-id="dc553-105">Range</span></span>|<span data-ttu-id="dc553-106">大小</span><span class="sxs-lookup"><span data-stu-id="dc553-106">Size</span></span>|<span data-ttu-id="dc553-107">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="dc553-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`short`|<span data-ttu-id="dc553-108">-32,768 到 32,767</span><span class="sxs-lookup"><span data-stu-id="dc553-108">-32,768 to 32,767</span></span>|<span data-ttu-id="dc553-109">帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="dc553-109">Signed 16-bit integer</span></span>|<span data-ttu-id="dc553-110"><xref:System.Int16?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="dc553-110"><xref:System.Int16?displayProperty=fullName></span></span>|  
  
## <a name="literals"></a><span data-ttu-id="dc553-111">常值</span><span class="sxs-lookup"><span data-stu-id="dc553-111">Literals</span></span>  

<span data-ttu-id="dc553-112">您可以將十進位常值、十六進位常值，或二進位常值 (自 C# 7 起) 指派給 `short` 變數，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="dc553-112">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="dc553-113">如果整數常值超出 `short` 範圍 (也就是說，如果它小於 <xref:System.Int16.MinValue?displayProperty=fullName> 或大於 <xref:System.Int16.MaxValue?displayProperty=fullName>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc553-113">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=fullName> or greater than <xref:System.Int16.MaxValue?displayProperty=fullName>, a compilation error occurs.</span></span> 

<span data-ttu-id="dc553-114">在下列範例中，以十進位、十六進位和二進位常值表示的 1,034 整數，從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換成 `short` 值。</span><span class="sxs-lookup"><span data-stu-id="dc553-114">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `short` values.</span></span>  
  
<span data-ttu-id="dc553-115">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]</span><span class="sxs-lookup"><span data-stu-id="dc553-115">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="dc553-116">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="dc553-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="dc553-117">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="dc553-117">Decimal literals have no prefix.</span></span>

<span data-ttu-id="dc553-118">自 C# 7 開始，您也可以使用底線字元 `_` 作為數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="dc553-118">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="dc553-119">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]</span><span class="sxs-lookup"><span data-stu-id="dc553-119">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]</span></span>  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="dc553-120">編譯器多載解析</span><span class="sxs-lookup"><span data-stu-id="dc553-120">Compiler overload resolution</span></span>

 <span data-ttu-id="dc553-121">呼叫多載的方法時，必須使用轉型。</span><span class="sxs-lookup"><span data-stu-id="dc553-121">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="dc553-122">例如，請考慮使用下列使用 `short` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：</span><span class="sxs-lookup"><span data-stu-id="dc553-122">Consider, for example, the following overloaded methods that use `short` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 <span data-ttu-id="dc553-123">使用 `short` 轉型時，可以保證呼叫正確的類型，例如：</span><span class="sxs-lookup"><span data-stu-id="dc553-123">Using the `short` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="dc553-124">轉換</span><span class="sxs-lookup"><span data-stu-id="dc553-124">Conversions</span></span>  

 <span data-ttu-id="dc553-125">有一項從 `short` 轉換為 [int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="dc553-125">There is a predefined implicit conversion from `short` to [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="dc553-126">您不能將較大儲存大小的非常值數字類型隱含轉換為 `short` (如需整數類型的儲存大小，請參閱[整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md))。</span><span class="sxs-lookup"><span data-stu-id="dc553-126">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="dc553-127">例如，請考慮使用下列兩個 `short` 變數 `x` 和 `y`：</span><span class="sxs-lookup"><span data-stu-id="dc553-127">Consider, for example, the following two `short` variables `x` and `y`:</span></span>  
  
```csharp  
short x = 5, y = 12;  
```  
  
 <span data-ttu-id="dc553-128">因為指派運算子右側的算術運算式預設會評估為 [int](../../../csharp/language-reference/keywords/int.md)，所以下列指派陳述式會產生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc553-128">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 <span data-ttu-id="dc553-129">若要修正這個問題，請使用轉型：</span><span class="sxs-lookup"><span data-stu-id="dc553-129">To fix this problem, use a cast:</span></span>  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 <span data-ttu-id="dc553-130">不過，也可以使用目的地變數具有相同或較大儲存大小的下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="dc553-130">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="dc553-131">不會從浮點類型隱含地轉換為 `short`。</span><span class="sxs-lookup"><span data-stu-id="dc553-131">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="dc553-132">例如，下列陳述式會在未使用明確轉型的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="dc553-132">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 <span data-ttu-id="dc553-133">如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="dc553-133">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="dc553-134">如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="dc553-134">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="dc553-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="dc553-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dc553-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc553-136">See Also</span></span>  
 <span data-ttu-id="dc553-137"><xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="dc553-137"><xref:System.Int16></span></span>   
<span data-ttu-id="dc553-138"> [C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc553-138"> [C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="dc553-139"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc553-139"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="dc553-140"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc553-140"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="dc553-141"> [整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="dc553-141"> [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="dc553-142"> [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="dc553-142"> [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="dc553-143"> [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="dc553-143"> [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
<span data-ttu-id="dc553-144"> [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)</span><span class="sxs-lookup"><span data-stu-id="dc553-144"> [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)</span></span>
