---
title: "如何：在十六進位字串和數字類型間轉換 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 91e5cff52c67e1e7930d92da7c87ab1f4a3120af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="f3211-102">如何：在十六進位字串和數字類型間轉換 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f3211-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="f3211-103">這些範例示範如何執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f3211-103">These examples show you how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f3211-104">取得[字串](../../../csharp/language-reference/keywords/string.md)中每個字元的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f3211-104">Obtain the hexadecimal value of each character in a [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
-   <span data-ttu-id="f3211-105">取十六進位字串中對應每個值的 [char](../../../csharp/language-reference/keywords/char.md)。</span><span class="sxs-lookup"><span data-stu-id="f3211-105">Obtain the [char](../../../csharp/language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
-   <span data-ttu-id="f3211-106">將十六進位 `string` 轉換成 [int](../../../csharp/language-reference/keywords/int.md)。</span><span class="sxs-lookup"><span data-stu-id="f3211-106">Convert a hexadecimal `string` to an [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
-   <span data-ttu-id="f3211-107">將十六進位 `string` 轉換成 [float](../../../csharp/language-reference/keywords/float.md)。</span><span class="sxs-lookup"><span data-stu-id="f3211-107">Convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md).</span></span>  
  
-   <span data-ttu-id="f3211-108">將 [byte](../../../csharp/language-reference/keywords/byte.md) 陣列轉換成十六進位 `string`。</span><span class="sxs-lookup"><span data-stu-id="f3211-108">Convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3211-109">範例</span><span class="sxs-lookup"><span data-stu-id="f3211-109">Example</span></span>  
 <span data-ttu-id="f3211-110">本例以 `string` 輸出每個字元的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f3211-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="f3211-111">它會先將 `string` 剖析成字元陣列。</span><span class="sxs-lookup"><span data-stu-id="f3211-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="f3211-112">接著在每個字元上呼叫 <xref:System.Convert.ToInt32%28System.Char%29>，以取得其數值。</span><span class="sxs-lookup"><span data-stu-id="f3211-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="f3211-113">最後，在 `string` 中將數字格式化為十六進位表示法。</span><span class="sxs-lookup"><span data-stu-id="f3211-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="f3211-114">範例</span><span class="sxs-lookup"><span data-stu-id="f3211-114">Example</span></span>  
 <span data-ttu-id="f3211-115">本例會剖析十六進位值的 `string`，並輸出對應至每個十六進位值的字元。</span><span class="sxs-lookup"><span data-stu-id="f3211-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="f3211-116">它會先呼叫 [Split(Char\[\])](xref:System.String.Split(System.Char[])) 方法，取得每個十六進位值，作為陣列中的個別 `string`。</span><span class="sxs-lookup"><span data-stu-id="f3211-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="f3211-117">接著呼叫 <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29>，以將十六進位值轉換為呈現為 [int](../../../csharp/language-reference/keywords/int.md) 的十進位值。它會顯示兩種不同取得對應該字元程式碼字元的方式。</span><span class="sxs-lookup"><span data-stu-id="f3211-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../../csharp/language-reference/keywords/int.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="f3211-118">第一個技巧使用 <xref:System.Char.ConvertFromUtf32%28System.Int32%29>，傳回對應於整數引數作為 `string` 的字元。</span><span class="sxs-lookup"><span data-stu-id="f3211-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="f3211-119">第二個技巧將 `int` 明確轉換成 [char](../../../csharp/language-reference/keywords/char.md)。</span><span class="sxs-lookup"><span data-stu-id="f3211-119">The second technique explicitly casts the `int` to a [char](../../../csharp/language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="f3211-120">範例</span><span class="sxs-lookup"><span data-stu-id="f3211-120">Example</span></span>  
 <span data-ttu-id="f3211-121">這個範例示範另一種將十六進位 `string` 轉換為整數的方式，方法是呼叫 <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="f3211-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="f3211-122">範例</span><span class="sxs-lookup"><span data-stu-id="f3211-122">Example</span></span>  
 <span data-ttu-id="f3211-123">下列範例示範如何使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別和 <xref:System.Int32.Parse%2A?displayProperty=nameWithType> 方法，以將十六進位 `string` 轉換為 [float](../../../csharp/language-reference/keywords/float.md)。</span><span class="sxs-lookup"><span data-stu-id="f3211-123">The following example shows how to convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.Int32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="f3211-124">範例</span><span class="sxs-lookup"><span data-stu-id="f3211-124">Example</span></span>  
 <span data-ttu-id="f3211-125">下例示範如何使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別，將 [byte](../../../csharp/language-reference/keywords/byte.md) 陣列轉換為十六進位的字串。</span><span class="sxs-lookup"><span data-stu-id="f3211-125">The following example shows how to convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f3211-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3211-126">See Also</span></span>  
 [<span data-ttu-id="f3211-127">標準數值格式字串</span><span class="sxs-lookup"><span data-stu-id="f3211-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="f3211-128">型別</span><span class="sxs-lookup"><span data-stu-id="f3211-128">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="f3211-129">如何：判斷字串是否表示數值</span><span class="sxs-lookup"><span data-stu-id="f3211-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
