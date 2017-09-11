---
title: "float (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- float
- float_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: 24
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
ms.openlocfilehash: 3f26fa2a009221679652fd8fdf67713be9e3bfe8
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="float-c-reference"></a><span data-ttu-id="f95b7-102">float (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f95b7-102">float (C# Reference)</span></span>
<span data-ttu-id="f95b7-103">`float` 關鍵字表示儲存 32 位元浮點值的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="f95b7-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="f95b7-104">下表顯示 `float` 類型的精確度和大概範圍。</span><span class="sxs-lookup"><span data-stu-id="f95b7-104">The following table shows the precision and approximate range for the `float` type.</span></span>  
  
|<span data-ttu-id="f95b7-105">類型</span><span class="sxs-lookup"><span data-stu-id="f95b7-105">Type</span></span>|<span data-ttu-id="f95b7-106">大概範圍</span><span class="sxs-lookup"><span data-stu-id="f95b7-106">Approximate range</span></span>|<span data-ttu-id="f95b7-107">精確度</span><span class="sxs-lookup"><span data-stu-id="f95b7-107">Precision</span></span>|<span data-ttu-id="f95b7-108">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="f95b7-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="f95b7-109">-3.4 × 10<sup>38</sup> 至 +3.4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="f95b7-109">-3.4 × 10<sup>38</sup>to +3.4 × 10<sup>38</sup></span></span>|<span data-ttu-id="f95b7-110">7 位數</span><span class="sxs-lookup"><span data-stu-id="f95b7-110">7 digits</span></span>|<span data-ttu-id="f95b7-111"><xref:System.Single?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f95b7-111"><xref:System.Single?displayProperty=fullName></span></span>|  
  
## <a name="literals"></a><span data-ttu-id="f95b7-112">常值</span><span class="sxs-lookup"><span data-stu-id="f95b7-112">Literals</span></span>  
 <span data-ttu-id="f95b7-113">根據預設，指派運算子右邊的實數常值會視為 [double](double.md)。</span><span class="sxs-lookup"><span data-stu-id="f95b7-113">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="f95b7-114">因此，若要初始化 float 變數，請使用後置字元 `f` 或 `F`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f95b7-114">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>  
  
```csharp
float x = 3.5F;  
```
  
 <span data-ttu-id="f95b7-115">如果您在上述宣告中未使用此後置字元，由於您嘗試將 [double](double.md) 值儲存至 `float` 變數，因此會收到編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="f95b7-115">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="f95b7-116">轉換</span><span class="sxs-lookup"><span data-stu-id="f95b7-116">Conversions</span></span>  
 <span data-ttu-id="f95b7-117">您可以在一個運算式中混合使用數值整數型別和浮點類型。</span><span class="sxs-lookup"><span data-stu-id="f95b7-117">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="f95b7-118">在此情況下，整數型別會轉換成浮點類型。</span><span class="sxs-lookup"><span data-stu-id="f95b7-118">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="f95b7-119">運算式的評估會根據下列規則來執行：</span><span class="sxs-lookup"><span data-stu-id="f95b7-119">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="f95b7-120">如果其中一個浮點類型是 [double](double.md)，則運算式會評估為 [double](double.md) 或 [bool](bool.md) (在關聯或布林運算式中)。</span><span class="sxs-lookup"><span data-stu-id="f95b7-120">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md) or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="f95b7-121">如果運算式中沒有 [double](double.md) 類型，則運算式會評估為 `float` 或 [bool](bool.md) (在關聯或布林運算式中)。</span><span class="sxs-lookup"><span data-stu-id="f95b7-121">If there is no [double](double.md) type in the expression, the expression evaluates to `float` or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="f95b7-122">浮點運算式可以包含下列值的集合：</span><span class="sxs-lookup"><span data-stu-id="f95b7-122">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="f95b7-123">正零和負零</span><span class="sxs-lookup"><span data-stu-id="f95b7-123">Positive and negative zero</span></span>  
  
-   <span data-ttu-id="f95b7-124">正無限大和負無限大</span><span class="sxs-lookup"><span data-stu-id="f95b7-124">Positive and negative infinity</span></span>  
  
-   <span data-ttu-id="f95b7-125">非數字值 (NaN)</span><span class="sxs-lookup"><span data-stu-id="f95b7-125">Not-a-Number value (NaN)</span></span>  
  
-   <span data-ttu-id="f95b7-126">非零值的有限集合</span><span class="sxs-lookup"><span data-stu-id="f95b7-126">The finite set of nonzero values</span></span>  
  
 <span data-ttu-id="f95b7-127">如需這些值的詳細資訊，請參閱 [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。</span><span class="sxs-lookup"><span data-stu-id="f95b7-127">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f95b7-128">範例</span><span class="sxs-lookup"><span data-stu-id="f95b7-128">Example</span></span>  
 <span data-ttu-id="f95b7-129">在下列範例中，會將一個 [int](int.md)、[short](short.md) 和 `float` 加入數學運算式，以產生 `float` 結果</span><span class="sxs-lookup"><span data-stu-id="f95b7-129">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="f95b7-130">(請記住，`float` 是 <xref:System.Single?displayProperty=fullName> 類型的別名)。請注意，運算式中沒有 [double](double.md)。</span><span class="sxs-lookup"><span data-stu-id="f95b7-130">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=fullName> type.) Notice that there is no [double](double.md) in the expression.</span></span>  
  
 <span data-ttu-id="f95b7-131">[!code-cs[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f95b7-131">[!code-cs[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f95b7-132">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f95b7-132">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f95b7-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f95b7-133">See Also</span></span>  
 <span data-ttu-id="f95b7-134"><xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="f95b7-134"><xref:System.Single></span></span>   
<span data-ttu-id="f95b7-135"> [C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f95b7-135"> [C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="f95b7-136"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f95b7-136"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="f95b7-137"> [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="f95b7-137"> [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span></span>  
<span data-ttu-id="f95b7-138"> [C# 關鍵字](index.md) </span><span class="sxs-lookup"><span data-stu-id="f95b7-138"> [C# Keywords](index.md) </span></span>  
<span data-ttu-id="f95b7-139"> [整數型別表](integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="f95b7-139"> [Integral Types Table](integral-types-table.md) </span></span>  
<span data-ttu-id="f95b7-140"> [內建類型表](built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="f95b7-140"> [Built-In Types Table](built-in-types-table.md) </span></span>  
<span data-ttu-id="f95b7-141"> [隱含數值轉換表](implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="f95b7-141"> [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md) </span></span>  
<span data-ttu-id="f95b7-142"> [明確數值轉換表](explicit-numeric-conversions-table.md)</span><span class="sxs-lookup"><span data-stu-id="f95b7-142"> [Explicit Numeric Conversions Table](explicit-numeric-conversions-table.md)</span></span>
