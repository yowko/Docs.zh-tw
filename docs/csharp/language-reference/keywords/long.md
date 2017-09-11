---
title: "long (C# 參考) | Microsoft Docs"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
dev_langs:
- CSharp
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
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
ms.openlocfilehash: 0ea7f109ab934660418aab1a88bff7206ef23a37
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="long-c-reference"></a><span data-ttu-id="81ae3-102">long (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="81ae3-102">long (C# Reference)</span></span>

<span data-ttu-id="81ae3-103">`long` 表示儲存值的整數型別 (以下表所示的大小和範圍為依據)。</span><span class="sxs-lookup"><span data-stu-id="81ae3-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="81ae3-104">類型</span><span class="sxs-lookup"><span data-stu-id="81ae3-104">Type</span></span>|<span data-ttu-id="81ae3-105">範圍</span><span class="sxs-lookup"><span data-stu-id="81ae3-105">Range</span></span>|<span data-ttu-id="81ae3-106">大小</span><span class="sxs-lookup"><span data-stu-id="81ae3-106">Size</span></span>|<span data-ttu-id="81ae3-107">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="81ae3-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`long`|<span data-ttu-id="81ae3-108">–9,223,372,036,854,775,808 到 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="81ae3-108">–9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="81ae3-109">帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="81ae3-109">Signed 64-bit integer</span></span>|<span data-ttu-id="81ae3-110"><xref:System.Int64?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="81ae3-110"><xref:System.Int64?displayProperty=fullName></span></span>|  
  
## <a name="literals"></a><span data-ttu-id="81ae3-111">常值</span><span class="sxs-lookup"><span data-stu-id="81ae3-111">Literals</span></span> 

<span data-ttu-id="81ae3-112">您可以針對 `long` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7 起)，以將其宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="81ae3-112">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="81ae3-113">在下列範例中，如果整數等於 4,294,967,296，即表示 `long` 值指派了十進位、十六進位和二進位常值。</span><span class="sxs-lookup"><span data-stu-id="81ae3-113">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>  
  
<span data-ttu-id="81ae3-114">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]</span><span class="sxs-lookup"><span data-stu-id="81ae3-114">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="81ae3-115">您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。</span><span class="sxs-lookup"><span data-stu-id="81ae3-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="81ae3-116">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="81ae3-116">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="81ae3-117">自 C# 7 開始，您也可以使用底線字元 `_` 作為數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="81ae3-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="81ae3-118">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span><span class="sxs-lookup"><span data-stu-id="81ae3-118">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span></span>  
 
 <span data-ttu-id="81ae3-119">整數常值亦可包含尾碼以表示類型。</span><span class="sxs-lookup"><span data-stu-id="81ae3-119">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="81ae3-120">`L` 後置詞表示 `long`。</span><span class="sxs-lookup"><span data-stu-id="81ae3-120">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="81ae3-121">下列範例會使用 `L` 後置詞來表示長整數：</span><span class="sxs-lookup"><span data-stu-id="81ae3-121">The following example uses the `L` suffix to denote a long integer:</span></span>
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  <span data-ttu-id="81ae3-122">您也可以使用小寫字母 "l" 作為後置詞。</span><span class="sxs-lookup"><span data-stu-id="81ae3-122">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="81ae3-123">不過，這會產生編譯器警告，因為字母 "l" 很容易與數字 "1" 混淆。</span><span class="sxs-lookup"><span data-stu-id="81ae3-123">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="81ae3-124">為了清楚起見，請使用 "L"。</span><span class="sxs-lookup"><span data-stu-id="81ae3-124">Use "L" for clarity.</span></span>  
  
 <span data-ttu-id="81ae3-125">當您使用 `L` 後置詞時，系統會根據常值整數的大小，判斷其類型為 `long` 或 [ulong](../../../csharp/language-reference/keywords/ulong.md)。</span><span class="sxs-lookup"><span data-stu-id="81ae3-125">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="81ae3-126">在此案例中，其小於 [ulong](../../../csharp/language-reference/keywords/ulong.md) 範圍，因此是 `long`。</span><span class="sxs-lookup"><span data-stu-id="81ae3-126">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="81ae3-127">後置詞的常見用法是用來呼叫多載方法。</span><span class="sxs-lookup"><span data-stu-id="81ae3-127">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="81ae3-128">例如，下列多載方法具有 `long` 和 [int](../../../csharp/language-reference/keywords/int.md) 類型的參數：</span><span class="sxs-lookup"><span data-stu-id="81ae3-128">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 <span data-ttu-id="81ae3-129">`L` 後置詞可確保呼叫正確的多載：</span><span class="sxs-lookup"><span data-stu-id="81ae3-129">The `L` suffix guarantees that the correct overload is called:</span></span>  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
<span data-ttu-id="81ae3-130">如果整數常值沒有後置詞，其類型會是下列類型中可表示其值的第一個類型：</span><span class="sxs-lookup"><span data-stu-id="81ae3-130">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="81ae3-131">int</span><span class="sxs-lookup"><span data-stu-id="81ae3-131">int</span></span>](int.md)
2. [<span data-ttu-id="81ae3-132">uint</span><span class="sxs-lookup"><span data-stu-id="81ae3-132">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="81ae3-133">ulong</span><span class="sxs-lookup"><span data-stu-id="81ae3-133">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 

<span data-ttu-id="81ae3-134">由於上述範例的 4294967296 常值已超出 [uint](../../../csharp/language-reference/keywords/uint.md) 範圍，因此屬於 `long` 類型 (請參閱[整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)，以了解整數型別的儲存大小)。</span><span class="sxs-lookup"><span data-stu-id="81ae3-134">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>  
  
 <span data-ttu-id="81ae3-135">如果您在相同的運算式中搭配使用 `long` 類型和其他整數型別，則運算式會判斷值為 `long` (若是關聯運算式或布林運算式，則為 [bool](../../../csharp/language-reference/keywords/bool.md))。</span><span class="sxs-lookup"><span data-stu-id="81ae3-135">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="81ae3-136">例如，下列運算式會判斷值為 `long`：</span><span class="sxs-lookup"><span data-stu-id="81ae3-136">For example, the following expression evaluates as `long`:</span></span>  
  
```csharp  
898L + 88  
```  
  
 <span data-ttu-id="81ae3-137">如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="81ae3-137">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="81ae3-138">轉換</span><span class="sxs-lookup"><span data-stu-id="81ae3-138">Conversions</span></span>  
 <span data-ttu-id="81ae3-139">針對從 `long` 轉換為 [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md)，有一項預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="81ae3-139">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="81ae3-140">否則，必須使用轉型。</span><span class="sxs-lookup"><span data-stu-id="81ae3-140">Otherwise a cast must be used.</span></span> <span data-ttu-id="81ae3-141">例如，下列陳述式會在未明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="81ae3-141">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 <span data-ttu-id="81ae3-142">針對從 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、 [ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `long`，有一項預先定義的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="81ae3-142">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>  
  
 <span data-ttu-id="81ae3-143">另請注意，沒有從浮點型別轉換為 `long` 的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="81ae3-143">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="81ae3-144">例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="81ae3-144">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="81ae3-145">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="81ae3-145">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="81ae3-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81ae3-146">See Also</span></span>  
 <span data-ttu-id="81ae3-147"><xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="81ae3-147"><xref:System.Int64></span></span>   
<span data-ttu-id="81ae3-148"> [C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="81ae3-148"> [C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="81ae3-149"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="81ae3-149"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="81ae3-150"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="81ae3-150"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="81ae3-151"> [整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="81ae3-151"> [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="81ae3-152"> [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="81ae3-152"> [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="81ae3-153"> [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="81ae3-153"> [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
<span data-ttu-id="81ae3-154"> [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)</span><span class="sxs-lookup"><span data-stu-id="81ae3-154"> [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)</span></span>
