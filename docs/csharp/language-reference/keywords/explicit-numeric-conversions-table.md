---
title: 明確數值轉換表 (C# 參考)
ms.date: 09/06/2018
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 948961d19518343c1f8ee14cd48dc33ec72cf23d
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2018
ms.locfileid: "49478918"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="3d004-102">明確數值轉換表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3d004-102">Explicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="3d004-103">下表顯示 .NET 數字類型間預先定義的明確轉換不含有[隱含轉換](implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="3d004-103">The following table shows the predefined explicit conversions between .NET numeric types for which there is no [implicit conversion](implicit-numeric-conversions-table.md).</span></span>

|<span data-ttu-id="3d004-104">從</span><span class="sxs-lookup"><span data-stu-id="3d004-104">From</span></span>|<span data-ttu-id="3d004-105">以</span><span class="sxs-lookup"><span data-stu-id="3d004-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="3d004-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="3d004-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="3d004-107">`byte`、`ushort`、`uint`、`ulong` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="3d004-107">`byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="3d004-108">byte</span><span class="sxs-lookup"><span data-stu-id="3d004-108">byte</span></span>](byte.md)|<span data-ttu-id="3d004-109">`sbyte` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="3d004-109">`sbyte` or `char`</span></span>|  
|[<span data-ttu-id="3d004-110">short</span><span class="sxs-lookup"><span data-stu-id="3d004-110">short</span></span>](short.md)|<span data-ttu-id="3d004-111">`sbyte`、`byte`、`ushort`、`uint`、`ulong` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="3d004-111">`sbyte`, `byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="3d004-112">ushort</span><span class="sxs-lookup"><span data-stu-id="3d004-112">ushort</span></span>](ushort.md)|<span data-ttu-id="3d004-113">`sbyte`、`byte`、`short` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="3d004-113">`sbyte`, `byte`, `short`, or `char`</span></span>|  
|[<span data-ttu-id="3d004-114">int</span><span class="sxs-lookup"><span data-stu-id="3d004-114">int</span></span>](int.md)|<span data-ttu-id="3d004-115">`sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong` 或 `char`。</span><span class="sxs-lookup"><span data-stu-id="3d004-115">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`,or `char`</span></span>|  
|[<span data-ttu-id="3d004-116">uint</span><span class="sxs-lookup"><span data-stu-id="3d004-116">uint</span></span>](uint.md)|<span data-ttu-id="3d004-117">`sbyte`、`byte`、`short`、`ushort`、`int` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="3d004-117">`sbyte`, `byte`, `short`, `ushort`, `int`, or `char`</span></span>|  
|[<span data-ttu-id="3d004-118">long</span><span class="sxs-lookup"><span data-stu-id="3d004-118">long</span></span>](long.md)|<span data-ttu-id="3d004-119">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`ulong` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="3d004-119">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="3d004-120">ulong</span><span class="sxs-lookup"><span data-stu-id="3d004-120">ulong</span></span>](ulong.md)|<span data-ttu-id="3d004-121">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="3d004-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, or `char`</span></span>|  
|[<span data-ttu-id="3d004-122">char</span><span class="sxs-lookup"><span data-stu-id="3d004-122">char</span></span>](char.md)|<span data-ttu-id="3d004-123">`sbyte`、 `byte`或 `short`</span><span class="sxs-lookup"><span data-stu-id="3d004-123">`sbyte`, `byte`, or `short`</span></span>|  
|[<span data-ttu-id="3d004-124">float</span><span class="sxs-lookup"><span data-stu-id="3d004-124">float</span></span>](float.md)|<span data-ttu-id="3d004-125">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="3d004-125">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`,or `decimal`</span></span>|  
|[<span data-ttu-id="3d004-126">double</span><span class="sxs-lookup"><span data-stu-id="3d004-126">double</span></span>](double.md)|<span data-ttu-id="3d004-127">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="3d004-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`,or `decimal`</span></span>|  
|[<span data-ttu-id="3d004-128">decimal</span><span class="sxs-lookup"><span data-stu-id="3d004-128">decimal</span></span>](decimal.md)|<span data-ttu-id="3d004-129">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="3d004-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, or `double`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d004-130">備註</span><span class="sxs-lookup"><span data-stu-id="3d004-130">Remarks</span></span>  
  
- <span data-ttu-id="3d004-131">明確的數值轉換可能會造成有效位數遺失或導致擲回例外狀況，通常為 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="3d004-131">The explicit numeric conversion may cause loss of precision or result in throwing an exception, typically an <xref:System.OverflowException>.</span></span>  

- <span data-ttu-id="3d004-132">將整數型別的值轉換為另一個整數型別時，結果取決於溢位[檢查內容](checked-and-unchecked.md)。</span><span class="sxs-lookup"><span data-stu-id="3d004-132">When you convert a value of an integral type to another integral type, the result depends on the overflow [checking context](checked-and-unchecked.md).</span></span> <span data-ttu-id="3d004-133">在已檢查的內容中，如果來源值在目標類型的範圍內，轉換將會成功。</span><span class="sxs-lookup"><span data-stu-id="3d004-133">In a checked context, the conversion succeeds if the source value is within the range of the destination type.</span></span> <span data-ttu-id="3d004-134">否則會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="3d004-134">Otherwise, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="3d004-135">在未檢查的內容中，轉換一律會成功，並按照如下所示繼續進行：</span><span class="sxs-lookup"><span data-stu-id="3d004-135">In an unchecked context, the conversion always succeeds, and proceeds as follows:</span></span>

  - <span data-ttu-id="3d004-136">如果來源類型大於目的地類型，會藉由捨棄其「額外」最高有效位元，來截斷來源值。</span><span class="sxs-lookup"><span data-stu-id="3d004-136">If the source type is larger than the destination type, then the source value is truncated by discarding its "extra" most significant bits.</span></span> <span data-ttu-id="3d004-137">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="3d004-137">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="3d004-138">如果來源類型小於目標類型，則來源值可以是正負號擴充或零擴充，以使其與目標類型的大小相同。</span><span class="sxs-lookup"><span data-stu-id="3d004-138">If the source type is smaller than the destination type, then the source value is either sign-extended or zero-extended so that it is the same size as the destination type.</span></span> <span data-ttu-id="3d004-139">如果來源類型帶正負號，則會使用正負號擴充；如果來源類型不帶正負號，則會使用零擴充。</span><span class="sxs-lookup"><span data-stu-id="3d004-139">Sign-extension is used if the source type is signed; zero-extension is used if the source type is unsigned.</span></span> <span data-ttu-id="3d004-140">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="3d004-140">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="3d004-141">如果來源類型與目標類型的大小相同，則來源值將視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="3d004-141">If the source type is the same size as the destination type, then the source value is treated as a value of the destination type.</span></span>
  
- <span data-ttu-id="3d004-142">當您將 `decimal` 值轉換為整數型別時，這個值會捨入到最接近整數值的零。</span><span class="sxs-lookup"><span data-stu-id="3d004-142">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="3d004-143">如果產生的整數值超出目的地類型的範圍，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="3d004-143">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>  
  
- <span data-ttu-id="3d004-144">當您將 `double` 或 `float` 值轉換為整數型別時，這個值會往零的方向捨入到最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="3d004-144">When you convert a `double` or `float` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="3d004-145">如果產生的整數值超出目的地類型的範圍，結果隨溢位[檢查內容](checked-and-unchecked.md)而異。</span><span class="sxs-lookup"><span data-stu-id="3d004-145">If the resulting integral value is outside the range of the destination type, the result depends on the overflow [checking context](checked-and-unchecked.md).</span></span> <span data-ttu-id="3d004-146">在已檢查的內容中會擲回 <xref:System.OverflowException>，而在未經檢查的內容中，結果是目的地類型的未指定值。</span><span class="sxs-lookup"><span data-stu-id="3d004-146">In a checked context, an <xref:System.OverflowException> is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>  
  
- <span data-ttu-id="3d004-147">當您將 `double` 轉換成 `float` 時，`double` 值會捨入到最接近 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="3d004-147">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="3d004-148">如果 `double` 值太小或太大以致不符合目的地類型，結果會是零或無限大。</span><span class="sxs-lookup"><span data-stu-id="3d004-148">If the `double` value is too small or too large to fit into the destination type, the result will be zero or infinity.</span></span>  
  
- <span data-ttu-id="3d004-149">當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換成 `decimal` 表示，必要時捨入到最接近第 28 個小數位數後的數字。</span><span class="sxs-lookup"><span data-stu-id="3d004-149">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="3d004-150">視來源值的值而定，可能會發生下列一種結果：</span><span class="sxs-lookup"><span data-stu-id="3d004-150">Depending on the value of the source value, one of the following results may occur:</span></span>  

  - <span data-ttu-id="3d004-151">如果來源值太小無法以 `decimal` 表示，結果就會變成零。</span><span class="sxs-lookup"><span data-stu-id="3d004-151">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>  

  - <span data-ttu-id="3d004-152">如果來源值是 NaN (不是數字)、無限大或太大，無法以 `decimal` 表示，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="3d004-152">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an <xref:System.OverflowException> is thrown.</span></span>  
  
- <span data-ttu-id="3d004-153">當您將 `decimal` 轉換成 `float` 或 `double` 時，`decimal` 值會捨入到最接近 `double` 或 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="3d004-153">When you convert `decimal` to `float` or `double`, the `decimal` value is rounded to the nearest `double` or `float` value.</span></span>  
  
 <span data-ttu-id="3d004-154">如需明確轉換的詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[明確轉換](~/_csharplang/spec/conversions.md#explicit-conversions)一節。</span><span class="sxs-lookup"><span data-stu-id="3d004-154">For more information about explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3d004-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d004-155">See also</span></span>

- [<span data-ttu-id="3d004-156">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3d004-156">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3d004-157">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3d004-157">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3d004-158">轉換和類型轉換</span><span class="sxs-lookup"><span data-stu-id="3d004-158">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="3d004-159">() 運算子</span><span class="sxs-lookup"><span data-stu-id="3d004-159">() Operator</span></span>](../operators/invocation-operator.md)
- [<span data-ttu-id="3d004-160">整數型別表</span><span class="sxs-lookup"><span data-stu-id="3d004-160">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="3d004-161">浮點數類型表</span><span class="sxs-lookup"><span data-stu-id="3d004-161">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="3d004-162">內建型別表</span><span class="sxs-lookup"><span data-stu-id="3d004-162">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="3d004-163">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="3d004-163">Implicit numeric conversions table</span></span>](implicit-numeric-conversions-table.md)
