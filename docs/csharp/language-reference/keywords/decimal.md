---
title: "decimal (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords: decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 114c2c68f50704595b71f22386625091b5b05e8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="decimal-c-reference"></a><span data-ttu-id="d3f04-102">decimal (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d3f04-102">decimal (C# Reference)</span></span>
<span data-ttu-id="d3f04-103">`decimal` 關鍵字表示 128 位元的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d3f04-103">The `decimal` keyword indicates a 128-bit data type.</span></span> <span data-ttu-id="d3f04-104">相較於其他浮點類型，`decimal` 類型的精確度較高且範圍較小，因此非常適合財務和金融計算。</span><span class="sxs-lookup"><span data-stu-id="d3f04-104">Compared to other floating-point types, the `decimal` type has more precision and a smaller range, which makes it appropriate for financial and monetary calculations.</span></span> <span data-ttu-id="d3f04-105">下表顯示 `decimal` 類型的大概範圍和精確度。</span><span class="sxs-lookup"><span data-stu-id="d3f04-105">The approximate range and precision for the `decimal` type are shown in the following table.</span></span>  
  
|<span data-ttu-id="d3f04-106">類型</span><span class="sxs-lookup"><span data-stu-id="d3f04-106">Type</span></span>|<span data-ttu-id="d3f04-107">大概範圍</span><span class="sxs-lookup"><span data-stu-id="d3f04-107">Approximate Range</span></span>|<span data-ttu-id="d3f04-108">精確度</span><span class="sxs-lookup"><span data-stu-id="d3f04-108">Precision</span></span>|<span data-ttu-id="d3f04-109">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="d3f04-109">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|<span data-ttu-id="d3f04-110">(-7.9 x 10<sup>28</sup> 至 7.9 x 10<sup>28</sup>) / (10<sup>0</sup> 至 10<sup>28</sup>)</span><span class="sxs-lookup"><span data-stu-id="d3f04-110">(-7.9 x 10<sup>28</sup> to 7.9 x 10<sup>28</sup>) / (10<sup>0</sup> to 10<sup>28</sup>)</span></span>|<span data-ttu-id="d3f04-111">28-29 個有效數字</span><span class="sxs-lookup"><span data-stu-id="d3f04-111">28-29 significant digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="d3f04-112">常值</span><span class="sxs-lookup"><span data-stu-id="d3f04-112">Literals</span></span>  
 <span data-ttu-id="d3f04-113">如果要將數值實數常值視為 `decimal` 處理，請使用後置字元 m 或 M，例如：</span><span class="sxs-lookup"><span data-stu-id="d3f04-113">If you want a numeric real literal to be treated as `decimal`, use the suffix m or M, for example:</span></span>  
  
```csharp
decimal myMoney = 300.5m;  
```  
  
 <span data-ttu-id="d3f04-114">如果沒有後置字元 m，會將數字視為 [double](../../../csharp/language-reference/keywords/double.md) 處理，因而產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3f04-114">Without the suffix m, the number is treated as a [double](../../../csharp/language-reference/keywords/double.md) and generates a compiler error.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="d3f04-115">轉換</span><span class="sxs-lookup"><span data-stu-id="d3f04-115">Conversions</span></span>  
 <span data-ttu-id="d3f04-116">整數類資料類型會隱含轉換成 `decimal`，而且結果會判斷值為 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="d3f04-116">The integral types are implicitly converted to `decimal` and the result evaluates to `decimal`.</span></span> <span data-ttu-id="d3f04-117">因此，您可以使用整數常值來初始化 Decimal 變數，而不需要後置字元，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3f04-117">Therefore you can initialize a decimal variable using an integer literal, without the suffix, as follows:</span></span>  
  
```csharp
decimal myMoney = 300;  
```  
  
 <span data-ttu-id="d3f04-118">其他浮點類型和 `decimal` 類型之間沒有隱含轉換，因此，這兩種類型之間必須使用轉換進行轉換。</span><span class="sxs-lookup"><span data-stu-id="d3f04-118">There is no implicit conversion between other floating-point types and the `decimal` type; therefore, a cast must be used to convert between these two types.</span></span> <span data-ttu-id="d3f04-119">例如: </span><span class="sxs-lookup"><span data-stu-id="d3f04-119">For example:</span></span>  
  
```csharp
decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 <span data-ttu-id="d3f04-120">您也可以在同一個運算式中混合使用 `decimal` 和數值整數類資料類型。</span><span class="sxs-lookup"><span data-stu-id="d3f04-120">You can also mix `decimal` and numeric integral types in the same expression.</span></span> <span data-ttu-id="d3f04-121">然而，未使用轉換就混合使用 `decimal` 與其他浮點類型會造成編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3f04-121">However, mixing `decimal` and other floating-point types without a cast causes a compilation error.</span></span>  
  
 <span data-ttu-id="d3f04-122">如需隱含數值轉換的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f04-122">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="d3f04-123">如需明確數值轉換的詳細資訊，請參閱[明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f04-123">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
## <a name="formatting-decimal-output"></a><span data-ttu-id="d3f04-124">格式化 Decimal 輸出</span><span class="sxs-lookup"><span data-stu-id="d3f04-124">Formatting Decimal Output</span></span>  
 <span data-ttu-id="d3f04-125">您可以使用 `String.Format` 方法，或透過會呼叫 <xref:System.Console.Write%2A?displayProperty=nameWithType> 的 `String.Format()` 方法格式化結果。</span><span class="sxs-lookup"><span data-stu-id="d3f04-125">You can format the results by using the `String.Format` method, or through the <xref:System.Console.Write%2A?displayProperty=nameWithType> method, which calls `String.Format()`.</span></span> <span data-ttu-id="d3f04-126">貨幣格式是使用標準貨幣格式字串 "C" 或 "c" 所指定，如本文稍後的第二個範例所示。</span><span class="sxs-lookup"><span data-stu-id="d3f04-126">The currency format is specified by using the standard currency format string "C" or "c," as shown in the second example later in this article.</span></span> <span data-ttu-id="d3f04-127">如需 `String.Format` 方法的詳細資訊，請參閱 <xref:System.String.Format%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d3f04-127">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3f04-128">範例</span><span class="sxs-lookup"><span data-stu-id="d3f04-128">Example</span></span>  
 <span data-ttu-id="d3f04-129">下列範例會嘗試新增 [double](../../../csharp/language-reference/keywords/double.md) 和 `decimal` 變數，而造成編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3f04-129">The following example causes a compiler error by trying to add [double](../../../csharp/language-reference/keywords/double.md) and `decimal` variables.</span></span>  
  
```csharp  
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
```  
  
 <span data-ttu-id="d3f04-130">結果會是下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="d3f04-130">The result is the following error:</span></span>  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 <span data-ttu-id="d3f04-131">在這個範例中，`decimal` 和 [int](../../../csharp/language-reference/keywords/int.md) 會在同一個運算式中混用。</span><span class="sxs-lookup"><span data-stu-id="d3f04-131">In this example, a `decimal` and an [int](../../../csharp/language-reference/keywords/int.md) are mixed in the same expression.</span></span> <span data-ttu-id="d3f04-132">結果會判斷值為 `decimal` 類型。</span><span class="sxs-lookup"><span data-stu-id="d3f04-132">The result evaluates to the `decimal` type.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d3f04-133">範例</span><span class="sxs-lookup"><span data-stu-id="d3f04-133">Example</span></span>  
 <span data-ttu-id="d3f04-134">在這個範例中，輸出是使用貨幣格式字串格式化。</span><span class="sxs-lookup"><span data-stu-id="d3f04-134">In this example, the output is formatted by using the currency format string.</span></span> <span data-ttu-id="d3f04-135">您會發現，`x` 會捨入，因為小數位數超過 $0.99。</span><span class="sxs-lookup"><span data-stu-id="d3f04-135">Notice that `x` is rounded because the decimal places exceed $0.99.</span></span> <span data-ttu-id="d3f04-136">代表最大確切位數的變數 `y` 會以正確格式精確顯示。</span><span class="sxs-lookup"><span data-stu-id="d3f04-136">The variable `y`, which represents the maximum exact digits, is displayed exactly in the correct format.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d3f04-137">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d3f04-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d3f04-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3f04-138">See Also</span></span>  
 <xref:System.Decimal>  
 [<span data-ttu-id="d3f04-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d3f04-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d3f04-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d3f04-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d3f04-141">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d3f04-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d3f04-142">整數型別表</span><span class="sxs-lookup"><span data-stu-id="d3f04-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="d3f04-143">內建型別表</span><span class="sxs-lookup"><span data-stu-id="d3f04-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="d3f04-144">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="d3f04-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="d3f04-145">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="d3f04-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="d3f04-146">標準數值格式字串</span><span class="sxs-lookup"><span data-stu-id="d3f04-146">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
