---
title: "隱含數值轉換表 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: 12
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
ms.openlocfilehash: 4c7aa29f9bdeb5f30918e6d7b990c5197e7fe1a1
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="eb48f-102">隱含數值轉換表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="eb48f-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="eb48f-103">下表顯示預先定義的隱含數值轉換。</span><span class="sxs-lookup"><span data-stu-id="eb48f-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="eb48f-104">在許多情況下可能會發生隱含轉換，包括方法叫用和指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb48f-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="eb48f-105">從</span><span class="sxs-lookup"><span data-stu-id="eb48f-105">From</span></span>|<span data-ttu-id="eb48f-106">以</span><span class="sxs-lookup"><span data-stu-id="eb48f-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="eb48f-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="eb48f-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="eb48f-108">`short`、`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="eb48f-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="eb48f-109">byte</span><span class="sxs-lookup"><span data-stu-id="eb48f-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="eb48f-110">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="eb48f-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="eb48f-111">short</span><span class="sxs-lookup"><span data-stu-id="eb48f-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="eb48f-112">`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="eb48f-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="eb48f-113">ushort</span><span class="sxs-lookup"><span data-stu-id="eb48f-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="eb48f-114">`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="eb48f-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="eb48f-115">int</span><span class="sxs-lookup"><span data-stu-id="eb48f-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="eb48f-116">`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="eb48f-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="eb48f-117">uint</span><span class="sxs-lookup"><span data-stu-id="eb48f-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="eb48f-118">`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="eb48f-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="eb48f-119">long</span><span class="sxs-lookup"><span data-stu-id="eb48f-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="eb48f-120">`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="eb48f-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="eb48f-121">char</span><span class="sxs-lookup"><span data-stu-id="eb48f-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="eb48f-122">`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="eb48f-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="eb48f-123">float</span><span class="sxs-lookup"><span data-stu-id="eb48f-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="eb48f-124">ulong</span><span class="sxs-lookup"><span data-stu-id="eb48f-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="eb48f-125">`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="eb48f-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb48f-126">備註</span><span class="sxs-lookup"><span data-stu-id="eb48f-126">Remarks</span></span>  
  
-   <span data-ttu-id="eb48f-127">從 `int`、`uint`、`long` 或 `ulong` 轉換為 `float`，以及從 `long` 或 `ulong` 轉換為 `double` 時，可能會遺失精確度，但不會遺失大小。</span><span class="sxs-lookup"><span data-stu-id="eb48f-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="eb48f-128">`char` 類型沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="eb48f-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="eb48f-129">浮點類型與 `decimal` 類型之間沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="eb48f-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="eb48f-130">`int` 類型的常數運算式可以轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`，但前提是常數運算式的值必須在目的地類型的範圍內。</span><span class="sxs-lookup"><span data-stu-id="eb48f-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="eb48f-131">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="eb48f-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eb48f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb48f-132">See Also</span></span>  
 <span data-ttu-id="eb48f-133">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="eb48f-133">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="eb48f-134">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="eb48f-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="eb48f-135">[整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="eb48f-135">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="eb48f-136">[內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="eb48f-136">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="eb48f-137">[明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="eb48f-137">[Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="eb48f-138">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="eb48f-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)

