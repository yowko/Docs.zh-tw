---
title: short (C# 參考)
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 7991259aadd391288caa37b35addd6e16e234878
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027859"
---
# <a name="short-c-reference"></a><span data-ttu-id="c3c29-102">short (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c3c29-102">short (C# Reference)</span></span>

<span data-ttu-id="c3c29-103">`short` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數資料型別。</span><span class="sxs-lookup"><span data-stu-id="c3c29-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="c3c29-104">類型</span><span class="sxs-lookup"><span data-stu-id="c3c29-104">Type</span></span>|<span data-ttu-id="c3c29-105">範圍</span><span class="sxs-lookup"><span data-stu-id="c3c29-105">Range</span></span>|<span data-ttu-id="c3c29-106">大小</span><span class="sxs-lookup"><span data-stu-id="c3c29-106">Size</span></span>|<span data-ttu-id="c3c29-107">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="c3c29-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`short`|<span data-ttu-id="c3c29-108">-32,768 到 32,767</span><span class="sxs-lookup"><span data-stu-id="c3c29-108">-32,768 to 32,767</span></span>|<span data-ttu-id="c3c29-109">帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="c3c29-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="c3c29-110">常值</span><span class="sxs-lookup"><span data-stu-id="c3c29-110">Literals</span></span>  

<span data-ttu-id="c3c29-111">您可以針對 `short` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="c3c29-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="c3c29-112">如果整數常值超出 `short` 的範圍 (亦即，如果小於 <xref:System.Int16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3c29-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="c3c29-113">在下列範例中，以十進位、十六進位和二進位常值表示的 1,034 整數，從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換成 `short` 值。</span><span class="sxs-lookup"><span data-stu-id="c3c29-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `short` values.</span></span>  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> <span data-ttu-id="c3c29-114">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="c3c29-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="c3c29-115">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="c3c29-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c3c29-116">從 C# 7.0 開始，已新增一組功能來提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="c3c29-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="c3c29-117">C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c3c29-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="c3c29-118">C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c3c29-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="c3c29-119">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="c3c29-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="c3c29-120">一些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="c3c29-120">Some examples are shown below.</span></span>

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="c3c29-121">編譯器多載解析</span><span class="sxs-lookup"><span data-stu-id="c3c29-121">Compiler overload resolution</span></span>

 <span data-ttu-id="c3c29-122">呼叫多載的方法時，必須使用轉型。</span><span class="sxs-lookup"><span data-stu-id="c3c29-122">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="c3c29-123">例如，請考慮使用下列使用 `short` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：</span><span class="sxs-lookup"><span data-stu-id="c3c29-123">Consider, for example, the following overloaded methods that use `short` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 <span data-ttu-id="c3c29-124">使用 `short` 轉型時，可以保證呼叫正確的類型，例如：</span><span class="sxs-lookup"><span data-stu-id="c3c29-124">Using the `short` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="c3c29-125">轉換</span><span class="sxs-lookup"><span data-stu-id="c3c29-125">Conversions</span></span>  

 <span data-ttu-id="c3c29-126">有一項從 `short` 轉換為 [int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="c3c29-126">There is a predefined implicit conversion from `short` to [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="c3c29-127">您不能將較大儲存大小的非常值數字類型隱含轉換為 `short` (如需整數類型的儲存大小，請參閱[整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md))。</span><span class="sxs-lookup"><span data-stu-id="c3c29-127">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="c3c29-128">例如，請考慮使用下列兩個 `short` 變數 `x` 和 `y`：</span><span class="sxs-lookup"><span data-stu-id="c3c29-128">Consider, for example, the following two `short` variables `x` and `y`:</span></span>  
  
```csharp  
short x = 5, y = 12;  
```  
  
 <span data-ttu-id="c3c29-129">因為指派運算子右側的算術運算式預設會評估為 [int](../../../csharp/language-reference/keywords/int.md)，所以下列指派陳述式會產生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3c29-129">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 <span data-ttu-id="c3c29-130">若要修正這個問題，請使用轉換：</span><span class="sxs-lookup"><span data-stu-id="c3c29-130">To fix this problem, use a cast:</span></span>  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 <span data-ttu-id="c3c29-131">不過，也可以使用目的地變數具有相同或較大儲存大小的下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="c3c29-131">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="c3c29-132">不會從浮點類型隱含地轉換為 `short`。</span><span class="sxs-lookup"><span data-stu-id="c3c29-132">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="c3c29-133">例如，下列陳述式會在未使用明確轉型的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="c3c29-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 <span data-ttu-id="c3c29-134">如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="c3c29-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="c3c29-135">如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="c3c29-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c3c29-136">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c3c29-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3c29-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3c29-137">See Also</span></span>  
 <xref:System.Int16>  
 [<span data-ttu-id="c3c29-138">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c3c29-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c3c29-139">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c3c29-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c3c29-140">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c3c29-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c3c29-141">整數型別表</span><span class="sxs-lookup"><span data-stu-id="c3c29-141">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="c3c29-142">內建型別表</span><span class="sxs-lookup"><span data-stu-id="c3c29-142">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="c3c29-143">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="c3c29-143">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="c3c29-144">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="c3c29-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
