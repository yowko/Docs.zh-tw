---
title: "char (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bf4c71d6f33d66e5ca917f2cfeb6c882b19b9d22
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="char-c-reference"></a><span data-ttu-id="c92fd-102">char (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c92fd-102">char (C# Reference)</span></span>
<span data-ttu-id="c92fd-103">`char` 關鍵字是用來宣告 .NET Framework 用來代表 Unicode 字元的 <xref:System.Char?displayProperty=fullName> 結構執行個體。</span><span class="sxs-lookup"><span data-stu-id="c92fd-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=fullName> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="c92fd-104">`Char` 物件的值是 16 位元數字 (序數) 值。</span><span class="sxs-lookup"><span data-stu-id="c92fd-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>  
  
 <span data-ttu-id="c92fd-105">Unicode 字元是用來代表世界各地的大部分書寫語言。</span><span class="sxs-lookup"><span data-stu-id="c92fd-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>  
  
|<span data-ttu-id="c92fd-106">類型</span><span class="sxs-lookup"><span data-stu-id="c92fd-106">Type</span></span>|<span data-ttu-id="c92fd-107">範圍</span><span class="sxs-lookup"><span data-stu-id="c92fd-107">Range</span></span>|<span data-ttu-id="c92fd-108">大小</span><span class="sxs-lookup"><span data-stu-id="c92fd-108">Size</span></span>|<span data-ttu-id="c92fd-109">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="c92fd-109">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`char`|<span data-ttu-id="c92fd-110">U+0000 到 U+FFFF</span><span class="sxs-lookup"><span data-stu-id="c92fd-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="c92fd-111">Unicode 16 位元字元</span><span class="sxs-lookup"><span data-stu-id="c92fd-111">Unicode 16-bit character</span></span>|<span data-ttu-id="c92fd-112"><xref:System.Char?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c92fd-112"><xref:System.Char?displayProperty=fullName></span></span>|  
  
## <a name="literals"></a><span data-ttu-id="c92fd-113">常值</span><span class="sxs-lookup"><span data-stu-id="c92fd-113">Literals</span></span>  
 <span data-ttu-id="c92fd-114">`char` 類型的常數可以撰寫為字元常值、十六進位逸出序列或 Unicode 表示法。</span><span class="sxs-lookup"><span data-stu-id="c92fd-114">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="c92fd-115">您也可以轉型整數字元碼。</span><span class="sxs-lookup"><span data-stu-id="c92fd-115">You can also cast the integral character codes.</span></span> <span data-ttu-id="c92fd-116">在下列範例中，四個 `char` 變數都會初始化成相同的字元 `X`：</span><span class="sxs-lookup"><span data-stu-id="c92fd-116">In the following example four `char` variables are initialized with the same character `X`:</span></span>  
  
 <span data-ttu-id="c92fd-117">[!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c92fd-117">[!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="c92fd-118">轉換</span><span class="sxs-lookup"><span data-stu-id="c92fd-118">Conversions</span></span>  
 <span data-ttu-id="c92fd-119">`char` 可以隱含地轉換為 [ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md)。</span><span class="sxs-lookup"><span data-stu-id="c92fd-119">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="c92fd-120">不過，沒有從其他類型到 `char` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="c92fd-120">However, there are no implicit conversions from other types to the `char` type.</span></span>  
  
 <span data-ttu-id="c92fd-121"><xref:System.Char?displayProperty=fullName> 類型提供數個使用 `char` 值的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="c92fd-121">The <xref:System.Char?displayProperty=fullName> type provides several static methods for working with `char` values.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c92fd-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c92fd-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c92fd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c92fd-123">See Also</span></span>  
 <span data-ttu-id="c92fd-124"><xref:System.Char></span><span class="sxs-lookup"><span data-stu-id="c92fd-124"><xref:System.Char></span></span>   
<span data-ttu-id="c92fd-125"> [C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c92fd-125"> [C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="c92fd-126"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c92fd-126"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="c92fd-127"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c92fd-127"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="c92fd-128"> [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="c92fd-128"> [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="c92fd-129"> [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="c92fd-129"> [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="c92fd-130"> [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="c92fd-130"> [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
<span data-ttu-id="c92fd-131"> [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="c92fd-131"> [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span></span>  
<span data-ttu-id="c92fd-132"> [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="c92fd-132"> [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
<span data-ttu-id="c92fd-133"> [字串](../../../csharp/programming-guide/strings/index.md)</span><span class="sxs-lookup"><span data-stu-id="c92fd-133"> [Strings](../../../csharp/programming-guide/strings/index.md)</span></span>
