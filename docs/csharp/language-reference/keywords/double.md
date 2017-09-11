---
title: "double (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- double
- double_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: 26
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d5588f8391157fb56a5e5067bb8e11f9269fe733
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="double-c-reference"></a><span data-ttu-id="c3ec6-102">double (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c3ec6-102">double (C# Reference)</span></span>
<span data-ttu-id="c3ec6-103">`double` 關鍵字表示儲存 64 位元浮點值的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="c3ec6-104">下表顯示 `double` 類型的精確度和大概範圍。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-104">The following table shows the precision and approximate range for the `double` type.</span></span>  
  
|<span data-ttu-id="c3ec6-105">類型</span><span class="sxs-lookup"><span data-stu-id="c3ec6-105">Type</span></span>|<span data-ttu-id="c3ec6-106">大概範圍</span><span class="sxs-lookup"><span data-stu-id="c3ec6-106">Approximate range</span></span>|<span data-ttu-id="c3ec6-107">精確度</span><span class="sxs-lookup"><span data-stu-id="c3ec6-107">Precision</span></span>|<span data-ttu-id="c3ec6-108">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="c3ec6-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|<span data-ttu-id="c3ec6-109">±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="c3ec6-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="c3ec6-110">15-16 位數</span><span class="sxs-lookup"><span data-stu-id="c3ec6-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="c3ec6-111">常值</span><span class="sxs-lookup"><span data-stu-id="c3ec6-111">Literals</span></span>  
 <span data-ttu-id="c3ec6-112">根據預設，指派運算子右邊的實數常值會視為 `double`。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="c3ec6-113">不過，如果您希望整數被視為 `double`，請使用後置字元 d 或 D，例如︰</span><span class="sxs-lookup"><span data-stu-id="c3ec6-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>  
  
```  
double x = 3D;  
```  
  
## <a name="conversions"></a><span data-ttu-id="c3ec6-114">轉換</span><span class="sxs-lookup"><span data-stu-id="c3ec6-114">Conversions</span></span>  
 <span data-ttu-id="c3ec6-115">您可以在一個運算式中混合使用數值整數型別和浮點類型。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="c3ec6-116">在此情況下，整數型別會轉換成浮點類型。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="c3ec6-117">運算式的評估會根據下列規則來執行：</span><span class="sxs-lookup"><span data-stu-id="c3ec6-117">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="c3ec6-118">如果其中一個浮點類型是 `double`，則運算式會評估為 `double` 或 [bool](../../../csharp/language-reference/keywords/bool.md) (在關聯或布林運算式中)。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="c3ec6-119">運算式中沒有 `double` 類型，它會評估為 [float](../../../csharp/language-reference/keywords/float.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md) (在關聯或布林運算式中)。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="c3ec6-120">浮點運算式可以包含下列值的集合：</span><span class="sxs-lookup"><span data-stu-id="c3ec6-120">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="c3ec6-121">正零和負零。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-121">Positive and negative zero.</span></span>  
  
-   <span data-ttu-id="c3ec6-122">正無限大和負無限大。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-122">Positive and negative infinity.</span></span>  
  
-   <span data-ttu-id="c3ec6-123">非數字值 (NaN)。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-123">Not-a-Number value (NaN).</span></span>  
  
-   <span data-ttu-id="c3ec6-124">非零值的有限集合。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-124">The finite set of nonzero values.</span></span>  
  
 <span data-ttu-id="c3ec6-125">如需這些值的詳細資訊，請參閱 [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3ec6-126">範例</span><span class="sxs-lookup"><span data-stu-id="c3ec6-126">Example</span></span>  
 <span data-ttu-id="c3ec6-127">在下例中，一起新增 [int](../../../csharp/language-reference/keywords/int.md)、[short](../../../csharp/language-reference/keywords/short.md)、[float](../../../csharp/language-reference/keywords/float.md) 和 `double` 以得到 `double` 結果。</span><span class="sxs-lookup"><span data-stu-id="c3ec6-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>  
  
 <span data-ttu-id="c3ec6-128">[!code-cs[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c3ec6-128">[!code-cs[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c3ec6-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c3ec6-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3ec6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3ec6-130">See Also</span></span>  
 <span data-ttu-id="c3ec6-131">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c3ec6-131">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c3ec6-132">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c3ec6-132">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c3ec6-133">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c3ec6-133">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="c3ec6-134">[預設值表](../../../csharp/language-reference/keywords/default-values-table.md) </span><span class="sxs-lookup"><span data-stu-id="c3ec6-134">[Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md) </span></span>  
 <span data-ttu-id="c3ec6-135">[內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="c3ec6-135">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="c3ec6-136">[浮點類型表](../../../csharp/language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="c3ec6-136">[Floating-Point Types Table](../../../csharp/language-reference/keywords/floating-point-types-table.md) </span></span>  
 <span data-ttu-id="c3ec6-137">[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="c3ec6-137">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="c3ec6-138">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="c3ec6-138">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

