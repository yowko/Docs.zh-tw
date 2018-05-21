---
title: char (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 67efc4b9600d7d722ebbef83819e143506a93c26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="char-c-reference"></a><span data-ttu-id="46c32-102">char (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="46c32-102">char (C# Reference)</span></span>
<span data-ttu-id="46c32-103">`char` 關鍵字是用來宣告 .NET Framework 用來代表 Unicode 字元的 <xref:System.Char?displayProperty=nameWithType> 結構執行個體。</span><span class="sxs-lookup"><span data-stu-id="46c32-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="46c32-104">`Char` 物件的值是 16 位元數字 (序數) 值。</span><span class="sxs-lookup"><span data-stu-id="46c32-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>  
  
 <span data-ttu-id="46c32-105">Unicode 字元是用來代表世界各地的大部分書寫語言。</span><span class="sxs-lookup"><span data-stu-id="46c32-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>  
  
|<span data-ttu-id="46c32-106">類型</span><span class="sxs-lookup"><span data-stu-id="46c32-106">Type</span></span>|<span data-ttu-id="46c32-107">範圍</span><span class="sxs-lookup"><span data-stu-id="46c32-107">Range</span></span>|<span data-ttu-id="46c32-108">大小</span><span class="sxs-lookup"><span data-stu-id="46c32-108">Size</span></span>|<span data-ttu-id="46c32-109">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="46c32-109">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`char`|<span data-ttu-id="46c32-110">U+0000 到 U+FFFF</span><span class="sxs-lookup"><span data-stu-id="46c32-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="46c32-111">Unicode 16 位元字元</span><span class="sxs-lookup"><span data-stu-id="46c32-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="46c32-112">常值</span><span class="sxs-lookup"><span data-stu-id="46c32-112">Literals</span></span>  
 <span data-ttu-id="46c32-113">`char` 類型的常數可以撰寫為字元常值、十六進位逸出序列或 Unicode 表示法。</span><span class="sxs-lookup"><span data-stu-id="46c32-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="46c32-114">您也可以轉型整數字元碼。</span><span class="sxs-lookup"><span data-stu-id="46c32-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="46c32-115">在下列範例中，四個 `char` 變數都會初始化成相同的字元 `X`：</span><span class="sxs-lookup"><span data-stu-id="46c32-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a><span data-ttu-id="46c32-116">轉換</span><span class="sxs-lookup"><span data-stu-id="46c32-116">Conversions</span></span>  
 <span data-ttu-id="46c32-117">`char` 可以隱含地轉換為 [ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md)。</span><span class="sxs-lookup"><span data-stu-id="46c32-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="46c32-118">不過，沒有從其他類型到 `char` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="46c32-118">However, there are no implicit conversions from other types to the `char` type.</span></span>  
  
 <span data-ttu-id="46c32-119"><xref:System.Char?displayProperty=nameWithType> 型別提供數種使用 `char` 值的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="46c32-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="46c32-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="46c32-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46c32-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="46c32-121">See Also</span></span>  
 <xref:System.Char>  
 [<span data-ttu-id="46c32-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="46c32-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="46c32-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="46c32-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46c32-124">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="46c32-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="46c32-125">整數型別表</span><span class="sxs-lookup"><span data-stu-id="46c32-125">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="46c32-126">內建型別表</span><span class="sxs-lookup"><span data-stu-id="46c32-126">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="46c32-127">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="46c32-127">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="46c32-128">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="46c32-128">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="46c32-129">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="46c32-129">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="46c32-130">字串</span><span class="sxs-lookup"><span data-stu-id="46c32-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
