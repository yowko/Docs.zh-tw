---
title: 隱含數值轉換表 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 2d417a2020656f300de0517526742679388f262e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217190"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="9bb9c-102">隱含數值轉換表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9bb9c-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="9bb9c-103">下表顯示預先定義的隱含數值轉換。</span><span class="sxs-lookup"><span data-stu-id="9bb9c-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="9bb9c-104">在許多情況下可能會發生隱含轉換，包括方法叫用和指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="9bb9c-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="9bb9c-105">從</span><span class="sxs-lookup"><span data-stu-id="9bb9c-105">From</span></span>|<span data-ttu-id="9bb9c-106">以</span><span class="sxs-lookup"><span data-stu-id="9bb9c-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="9bb9c-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="9bb9c-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="9bb9c-108">`short`、`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9bb9c-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="9bb9c-109">byte</span><span class="sxs-lookup"><span data-stu-id="9bb9c-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="9bb9c-110">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9bb9c-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="9bb9c-111">short</span><span class="sxs-lookup"><span data-stu-id="9bb9c-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="9bb9c-112">`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9bb9c-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="9bb9c-113">ushort</span><span class="sxs-lookup"><span data-stu-id="9bb9c-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="9bb9c-114">`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="9bb9c-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="9bb9c-115">int</span><span class="sxs-lookup"><span data-stu-id="9bb9c-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="9bb9c-116">`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9bb9c-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="9bb9c-117">uint</span><span class="sxs-lookup"><span data-stu-id="9bb9c-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="9bb9c-118">`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9bb9c-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="9bb9c-119">long</span><span class="sxs-lookup"><span data-stu-id="9bb9c-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="9bb9c-120">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9bb9c-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="9bb9c-121">char</span><span class="sxs-lookup"><span data-stu-id="9bb9c-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="9bb9c-122">`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9bb9c-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="9bb9c-123">float</span><span class="sxs-lookup"><span data-stu-id="9bb9c-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="9bb9c-124">ulong</span><span class="sxs-lookup"><span data-stu-id="9bb9c-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="9bb9c-125">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9bb9c-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bb9c-126">備註</span><span class="sxs-lookup"><span data-stu-id="9bb9c-126">Remarks</span></span>  
  
-   <span data-ttu-id="9bb9c-127">從 `int`、`uint`、`long` 或 `ulong` 轉換為 `float`，以及從 `long` 或 `ulong` 轉換為 `double` 時，可能會遺失精確度，但不會遺失大小。</span><span class="sxs-lookup"><span data-stu-id="9bb9c-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="9bb9c-128">`char` 類型沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="9bb9c-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="9bb9c-129">浮點類型與 `decimal` 類型之間沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="9bb9c-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="9bb9c-130">`int` 類型的常數運算式可以轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`，但前提是常數運算式的值必須在目的地類型的範圍內。</span><span class="sxs-lookup"><span data-stu-id="9bb9c-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9bb9c-131">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9bb9c-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9bb9c-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="9bb9c-132">See Also</span></span>  
 [<span data-ttu-id="9bb9c-133">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9bb9c-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9bb9c-134">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9bb9c-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9bb9c-135">整數型別表</span><span class="sxs-lookup"><span data-stu-id="9bb9c-135">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="9bb9c-136">內建型別表</span><span class="sxs-lookup"><span data-stu-id="9bb9c-136">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="9bb9c-137">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="9bb9c-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="9bb9c-138">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="9bb9c-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
