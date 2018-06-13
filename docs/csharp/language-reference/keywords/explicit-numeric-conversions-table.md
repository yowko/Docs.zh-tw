---
title: 明確數值轉換表 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 7363df3e4b2449924222745de409fd68349b93de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218380"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="c5914-102">明確數值轉換表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c5914-102">Explicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="c5914-103">明確數值轉換是使用 cast 運算式，用來將任何數值類型轉換成任何其他數值類型，沒有任何隱含的轉換。</span><span class="sxs-lookup"><span data-stu-id="c5914-103">Explicit numeric conversion is used to convert any numeric type to any other numeric type, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="c5914-104">下表顯示這些轉換。</span><span class="sxs-lookup"><span data-stu-id="c5914-104">The following table shows these conversions.</span></span>  
  
 <span data-ttu-id="c5914-105">如需這些轉換的詳細資訊，請參閱[轉換和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="c5914-105">For more information about conversions, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
|<span data-ttu-id="c5914-106">從</span><span class="sxs-lookup"><span data-stu-id="c5914-106">From</span></span>|<span data-ttu-id="c5914-107">以</span><span class="sxs-lookup"><span data-stu-id="c5914-107">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="c5914-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="c5914-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="c5914-109">`byte`、`ushort`、`uint`、`ulong` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="c5914-109">`byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="c5914-110">byte</span><span class="sxs-lookup"><span data-stu-id="c5914-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="c5914-111">`Sbyte` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="c5914-111">`Sbyte` or `char`</span></span>|  
|[<span data-ttu-id="c5914-112">short</span><span class="sxs-lookup"><span data-stu-id="c5914-112">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="c5914-113">`sbyte`、`byte`、`ushort`、`uint`、`ulong` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="c5914-113">`sbyte`, `byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="c5914-114">ushort</span><span class="sxs-lookup"><span data-stu-id="c5914-114">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="c5914-115">`sbyte`、`byte`、`short` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="c5914-115">`sbyte`, `byte`, `short`, or `char`</span></span>|  
|[<span data-ttu-id="c5914-116">int</span><span class="sxs-lookup"><span data-stu-id="c5914-116">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="c5914-117">`sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong` 或 `char`。</span><span class="sxs-lookup"><span data-stu-id="c5914-117">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`,or `char`</span></span>|  
|[<span data-ttu-id="c5914-118">uint</span><span class="sxs-lookup"><span data-stu-id="c5914-118">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="c5914-119">`sbyte`、`byte`、`short`、`ushort`、`int` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="c5914-119">`sbyte`, `byte`, `short`, `ushort`, `int`, or `char`</span></span>|  
|[<span data-ttu-id="c5914-120">long</span><span class="sxs-lookup"><span data-stu-id="c5914-120">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="c5914-121">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`ulong` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="c5914-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="c5914-122">ulong</span><span class="sxs-lookup"><span data-stu-id="c5914-122">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="c5914-123">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="c5914-123">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, or `char`</span></span>|  
|[<span data-ttu-id="c5914-124">char</span><span class="sxs-lookup"><span data-stu-id="c5914-124">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="c5914-125">`sbyte`、 `byte`或 `short`</span><span class="sxs-lookup"><span data-stu-id="c5914-125">`sbyte`, `byte`, or `short`</span></span>|  
|[<span data-ttu-id="c5914-126">float</span><span class="sxs-lookup"><span data-stu-id="c5914-126">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="c5914-127">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="c5914-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`,or `decimal`</span></span>|  
|[<span data-ttu-id="c5914-128">double</span><span class="sxs-lookup"><span data-stu-id="c5914-128">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="c5914-129">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="c5914-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`,or `decimal`</span></span>|  
|[<span data-ttu-id="c5914-130">decimal</span><span class="sxs-lookup"><span data-stu-id="c5914-130">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="c5914-131">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="c5914-131">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, or `double`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5914-132">備註</span><span class="sxs-lookup"><span data-stu-id="c5914-132">Remarks</span></span>  
  
-   <span data-ttu-id="c5914-133">明確的數值轉換可能會造成有效位數遺失或導致擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c5914-133">The explicit numeric conversion may cause loss of precision or result in throwing exceptions.</span></span>  
  
-   <span data-ttu-id="c5914-134">當您將 `decimal` 值轉換為整數型別時，這個值會捨入到最接近整數值的零。</span><span class="sxs-lookup"><span data-stu-id="c5914-134">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="c5914-135">如果產生的整數值超出目的地類型的範圍，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="c5914-135">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>  
  
-   <span data-ttu-id="c5914-136">從 `double` 或 `float` 值轉換為整數型別時，值會被截斷。</span><span class="sxs-lookup"><span data-stu-id="c5914-136">When you convert from a `double` or `float` value to an integral type, the value is truncated.</span></span> <span data-ttu-id="c5914-137">如果產生的整數值超出目的地類型的範圍，結果隨溢位檢查內容而異。</span><span class="sxs-lookup"><span data-stu-id="c5914-137">If the resulting integral value is outside the range of the destination value, the result depends on the overflow checking context.</span></span> <span data-ttu-id="c5914-138">在已檢查的內容中會擲回 `OverflowException`，而在未經檢查的內容中，結果是目的地類型的未指定值。</span><span class="sxs-lookup"><span data-stu-id="c5914-138">In a checked context, an `OverflowException` is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>  
  
-   <span data-ttu-id="c5914-139">當您將 `double` 轉換成 `float` 時，`double` 值會捨入到最接近 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="c5914-139">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="c5914-140">如果 `double` 值太小或太大以致不符合目的地類型，結果會是零或無限大。</span><span class="sxs-lookup"><span data-stu-id="c5914-140">If the `double` value is too small or too large to fit into the destination type, the result will be zero or infinity.</span></span>  
  
-   <span data-ttu-id="c5914-141">當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換成 `decimal` 表示，必要時捨入到最接近第 28 個小數位數後的數字。</span><span class="sxs-lookup"><span data-stu-id="c5914-141">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="c5914-142">視來源值的值而定，可能會發生下列一種結果：</span><span class="sxs-lookup"><span data-stu-id="c5914-142">Depending on the value of the source value, one of the following results may occur:</span></span>  
  
    -   <span data-ttu-id="c5914-143">如果來源值太小無法以 `decimal` 表示，結果就會變成零。</span><span class="sxs-lookup"><span data-stu-id="c5914-143">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>  
  
    -   <span data-ttu-id="c5914-144">如果來源值是 NaN (不是數字)、無限大或太大，無法以 `decimal` 表示，就會擲回 `OverflowException`。</span><span class="sxs-lookup"><span data-stu-id="c5914-144">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an `OverflowException` is thrown.</span></span>  
  
-   <span data-ttu-id="c5914-145">當您將 `decimal` 轉換成 `float` 或 `double` 時，`decimal` 值會捨入到最接近 `double` 或 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="c5914-145">When you convert `decimal` to `float` or `double`, the `decimal` value is rounded to the nearest `double` or `float` value.</span></span>  
  
 <span data-ttu-id="c5914-146">如需明確轉換的詳細資訊，請參閱＜C# 語言規格＞中的＜明確＞。</span><span class="sxs-lookup"><span data-stu-id="c5914-146">For more information on explicit conversion, see Explicit in the C# Language Specification.</span></span> <span data-ttu-id="c5914-147">如需如何存取規格的詳細資訊，請參閱 [C# 語言規格](../../../csharp/language-reference/language-specification/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c5914-147">For more information on how to access the spec, see [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5914-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="c5914-148">See Also</span></span>  
 [<span data-ttu-id="c5914-149">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c5914-149">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c5914-150">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c5914-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c5914-151">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="c5914-151">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="c5914-152">() 運算子</span><span class="sxs-lookup"><span data-stu-id="c5914-152">() Operator</span></span>](../../../csharp/language-reference/operators/invocation-operator.md)  
 [<span data-ttu-id="c5914-153">整數型別表</span><span class="sxs-lookup"><span data-stu-id="c5914-153">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="c5914-154">內建型別表</span><span class="sxs-lookup"><span data-stu-id="c5914-154">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="c5914-155">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="c5914-155">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
