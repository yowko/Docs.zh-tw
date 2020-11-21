---
title: '如何在十六進位字串和數位類型之間轉換-c # 程式設計指南'
description: 瞭解如何在十六進位字串和數位類型之間轉換。 請參閱程式碼範例，並檢視其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: fc2ffd24a67f026bd0c78e7d604a0147cf57ba49
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099155"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="36f03-104">如何在十六進位字串和數位類型之間轉換 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="36f03-104">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>

<span data-ttu-id="36f03-105">這些範例示範如何執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="36f03-105">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="36f03-106">取得[字串](../../language-reference/builtin-types/reference-types.md)中每個字元的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="36f03-106">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="36f03-107">取十六進位字串中對應每個值的 [char](../../language-reference/builtin-types/char.md)。</span><span class="sxs-lookup"><span data-stu-id="36f03-107">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="36f03-108">將十六進位 `string` 轉換成 [int](../../language-reference/builtin-types/integral-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="36f03-108">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="36f03-109">將十六進位 `string` 轉換成 [float](../../language-reference/builtin-types/floating-point-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="36f03-109">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="36f03-110">將 [byte](../../language-reference/builtin-types/integral-numeric-types.md) 陣列轉換成十六進位 `string`。</span><span class="sxs-lookup"><span data-stu-id="36f03-110">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36f03-111">範例</span><span class="sxs-lookup"><span data-stu-id="36f03-111">Example</span></span>  

 <span data-ttu-id="36f03-112">本例以 `string` 輸出每個字元的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="36f03-112">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="36f03-113">它會先將 `string` 剖析成字元陣列。</span><span class="sxs-lookup"><span data-stu-id="36f03-113">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="36f03-114">接著在每個字元上呼叫 <xref:System.Convert.ToInt32%28System.Char%29>，以取得其數值。</span><span class="sxs-lookup"><span data-stu-id="36f03-114">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="36f03-115">最後，在 `string` 中將數字格式化為十六進位表示法。</span><span class="sxs-lookup"><span data-stu-id="36f03-115">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="36f03-116">範例</span><span class="sxs-lookup"><span data-stu-id="36f03-116">Example</span></span>  

 <span data-ttu-id="36f03-117">本例會剖析十六進位值的 `string`，並輸出對應至每個十六進位值的字元。</span><span class="sxs-lookup"><span data-stu-id="36f03-117">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="36f03-118">首先，它會呼叫[Split (Char \[ \]) ](xref:System.String.Split(System.Char[]))方法，以取得每個十六進位值做為陣列中的個別值 `string` 。</span><span class="sxs-lookup"><span data-stu-id="36f03-118">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="36f03-119">然後，它會呼叫 <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> ，將十六進位值轉換成以 [int](../../language-reference/builtin-types/integral-numeric-types.md)表示的十進位值。它會顯示兩種不同的方式來取得對應至該字元碼的字元。</span><span class="sxs-lookup"><span data-stu-id="36f03-119">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="36f03-120">第一個技巧使用 <xref:System.Char.ConvertFromUtf32%28System.Int32%29>，傳回對應於整數引數作為 `string` 的字元。</span><span class="sxs-lookup"><span data-stu-id="36f03-120">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="36f03-121">第二個技巧將 `int` 明確轉換成 [char](../../language-reference/builtin-types/char.md)。</span><span class="sxs-lookup"><span data-stu-id="36f03-121">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="36f03-122">範例</span><span class="sxs-lookup"><span data-stu-id="36f03-122">Example</span></span>  

 <span data-ttu-id="36f03-123">這個範例示範另一種將十六進位 `string` 轉換為整數的方式，方法是呼叫 <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="36f03-123">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="36f03-124">範例</span><span class="sxs-lookup"><span data-stu-id="36f03-124">Example</span></span>  

 <span data-ttu-id="36f03-125">下列範例示範如何使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別和 <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> 方法，以將十六進位 `string` 轉換為 [float](../../language-reference/builtin-types/floating-point-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="36f03-125">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="36f03-126">範例</span><span class="sxs-lookup"><span data-stu-id="36f03-126">Example</span></span>  

 <span data-ttu-id="36f03-127">下例示範如何使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別，將 [byte](../../language-reference/builtin-types/integral-numeric-types.md) 陣列轉換為十六進位的字串。</span><span class="sxs-lookup"><span data-stu-id="36f03-127">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="36f03-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36f03-128">See also</span></span>

- <span data-ttu-id="36f03-129">[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="36f03-129">[Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md)</span></span>
- [<span data-ttu-id="36f03-130">類型</span><span class="sxs-lookup"><span data-stu-id="36f03-130">Types</span></span>](./index.md)
- [<span data-ttu-id="36f03-131">如何判斷字串是否表示數值</span><span class="sxs-lookup"><span data-stu-id="36f03-131">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
