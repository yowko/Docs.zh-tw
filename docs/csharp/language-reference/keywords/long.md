---
title: "long (C# 參考)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords: long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f18bed80550b293195961fd9d42491dd571cbaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="long-c-reference"></a><span data-ttu-id="499c2-102">long (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="499c2-102">long (C# Reference)</span></span>

<span data-ttu-id="499c2-103">`long` 表示儲存值的整數型別 (以下表所示的大小和範圍為依據)。</span><span class="sxs-lookup"><span data-stu-id="499c2-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="499c2-104">類型</span><span class="sxs-lookup"><span data-stu-id="499c2-104">Type</span></span>|<span data-ttu-id="499c2-105">範圍</span><span class="sxs-lookup"><span data-stu-id="499c2-105">Range</span></span>|<span data-ttu-id="499c2-106">大小</span><span class="sxs-lookup"><span data-stu-id="499c2-106">Size</span></span>|<span data-ttu-id="499c2-107">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="499c2-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`long`|<span data-ttu-id="499c2-108">-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="499c2-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="499c2-109">帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="499c2-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="499c2-110">常值</span><span class="sxs-lookup"><span data-stu-id="499c2-110">Literals</span></span> 

<span data-ttu-id="499c2-111">您可以針對 `long` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="499c2-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="499c2-112">在下列範例中，如果整數等於 4,294,967,296，即表示 `long` 值指派了十進位、十六進位和二進位常值。</span><span class="sxs-lookup"><span data-stu-id="499c2-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> <span data-ttu-id="499c2-113">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="499c2-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="499c2-114">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="499c2-114">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="499c2-115">開始使用 C# 7，已加入一組功能，以提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="499c2-115">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="499c2-116">C# 7.0 可讓使用底線字元， `_`，做為千位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="499c2-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="499c2-117">可讓 C# 7.2`_`来做為二進位或十六進位常值、 數字分隔符號 after 前置字元。</span><span class="sxs-lookup"><span data-stu-id="499c2-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="499c2-118">十進位常值不允許有前置底線。</span><span class="sxs-lookup"><span data-stu-id="499c2-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="499c2-119">某些範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="499c2-119">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="499c2-120">整數常值亦可包含後置詞以表示類型。</span><span class="sxs-lookup"><span data-stu-id="499c2-120">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="499c2-121">`L` 後置詞表示 `long`。</span><span class="sxs-lookup"><span data-stu-id="499c2-121">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="499c2-122">下列範例會使用 `L` 後置詞來表示長整數：</span><span class="sxs-lookup"><span data-stu-id="499c2-122">The following example uses the `L` suffix to denote a long integer:</span></span>
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  <span data-ttu-id="499c2-123">您也可以使用小寫字母 "l" 作為後置詞。</span><span class="sxs-lookup"><span data-stu-id="499c2-123">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="499c2-124">不過，這會產生編譯器警告，因為字母 "l" 很容易與數字 "1" 混淆。</span><span class="sxs-lookup"><span data-stu-id="499c2-124">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="499c2-125">為了清楚起見，請使用 "L"。</span><span class="sxs-lookup"><span data-stu-id="499c2-125">Use "L" for clarity.</span></span>  
  
 <span data-ttu-id="499c2-126">當您使用 `L` 後置詞時，系統會根據常值整數的大小，判斷其類型為 `long` 或 [ulong](../../../csharp/language-reference/keywords/ulong.md)。</span><span class="sxs-lookup"><span data-stu-id="499c2-126">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="499c2-127">在此案例中，其小於 [ulong](../../../csharp/language-reference/keywords/ulong.md) 範圍，因此是 `long`。</span><span class="sxs-lookup"><span data-stu-id="499c2-127">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="499c2-128">後置詞的常見用法是用來呼叫多載方法。</span><span class="sxs-lookup"><span data-stu-id="499c2-128">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="499c2-129">例如，下列多載方法具有 `long` 和 [int](../../../csharp/language-reference/keywords/int.md) 類型的參數：</span><span class="sxs-lookup"><span data-stu-id="499c2-129">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 <span data-ttu-id="499c2-130">`L` 後置詞可確保呼叫正確的多載：</span><span class="sxs-lookup"><span data-stu-id="499c2-130">The `L` suffix guarantees that the correct overload is called:</span></span>  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
<span data-ttu-id="499c2-131">如果整數常值沒有後置詞，其類型會是下列類型中可表示其值的第一個類型：</span><span class="sxs-lookup"><span data-stu-id="499c2-131">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="499c2-132">int</span><span class="sxs-lookup"><span data-stu-id="499c2-132">int</span></span>](int.md)
2. [<span data-ttu-id="499c2-133">uint</span><span class="sxs-lookup"><span data-stu-id="499c2-133">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="499c2-134">ulong</span><span class="sxs-lookup"><span data-stu-id="499c2-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 

<span data-ttu-id="499c2-135">由於上述範例的 4294967296 常值已超出 [uint](../../../csharp/language-reference/keywords/uint.md) 範圍，因此屬於 `long` 類型 (請參閱[整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)，以了解整數型別的儲存大小)。</span><span class="sxs-lookup"><span data-stu-id="499c2-135">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>  
  
 <span data-ttu-id="499c2-136">如果您在相同的運算式中搭配使用 `long` 類型和其他整數型別，則運算式會判斷值為 `long` (若是關聯運算式或布林運算式，則為 [bool](../../../csharp/language-reference/keywords/bool.md))。</span><span class="sxs-lookup"><span data-stu-id="499c2-136">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="499c2-137">例如，下列運算式會判斷值為 `long`：</span><span class="sxs-lookup"><span data-stu-id="499c2-137">For example, the following expression evaluates as `long`:</span></span>  
  
```csharp  
898L + 88  
```  
  
 <span data-ttu-id="499c2-138">如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="499c2-138">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="499c2-139">轉換</span><span class="sxs-lookup"><span data-stu-id="499c2-139">Conversions</span></span>  
 <span data-ttu-id="499c2-140">針對從 `long` 轉換為 [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md)，有一項預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="499c2-140">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="499c2-141">否則，必須使用轉型。</span><span class="sxs-lookup"><span data-stu-id="499c2-141">Otherwise a cast must be used.</span></span> <span data-ttu-id="499c2-142">例如，下列陳述式會在未明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="499c2-142">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 <span data-ttu-id="499c2-143">針對從 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、 [ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `long`，有一項預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="499c2-143">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>  
  
 <span data-ttu-id="499c2-144">另請注意，沒有從浮點型別轉換為 `long` 的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="499c2-144">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="499c2-145">例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="499c2-145">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="499c2-146">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="499c2-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="499c2-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="499c2-147">See Also</span></span>  
 <xref:System.Int64>  
 [<span data-ttu-id="499c2-148">C# 參考</span><span class="sxs-lookup"><span data-stu-id="499c2-148">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="499c2-149">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="499c2-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="499c2-150">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="499c2-150">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="499c2-151">整數型別表</span><span class="sxs-lookup"><span data-stu-id="499c2-151">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="499c2-152">內建型別表</span><span class="sxs-lookup"><span data-stu-id="499c2-152">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="499c2-153">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="499c2-153">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="499c2-154">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="499c2-154">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
