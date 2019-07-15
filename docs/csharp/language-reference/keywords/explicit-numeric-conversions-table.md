---
title: 明確數值轉換表 - C# 參考
ms.custom: seodec18
ms.date: 09/06/2018
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: d1533872850a953a38800aaeac85b9e6e565d374
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661373"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="26fe4-102">明確數值轉換表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="26fe4-102">Explicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="26fe4-103">下表顯示 .NET 數字類型間預先定義的明確轉換不含有[隱含轉換](implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="26fe4-103">The following table shows the predefined explicit conversions between .NET numeric types for which there is no [implicit conversion](implicit-numeric-conversions-table.md).</span></span>

|<span data-ttu-id="26fe4-104">從</span><span class="sxs-lookup"><span data-stu-id="26fe4-104">From</span></span>|<span data-ttu-id="26fe4-105">以</span><span class="sxs-lookup"><span data-stu-id="26fe4-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="26fe4-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="26fe4-106">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="26fe4-107">`byte`、`ushort`、`uint`、`ulong` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="26fe4-107">`byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="26fe4-108">byte</span><span class="sxs-lookup"><span data-stu-id="26fe4-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="26fe4-109">`sbyte` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="26fe4-109">`sbyte` or `char`</span></span>|  
|[<span data-ttu-id="26fe4-110">short</span><span class="sxs-lookup"><span data-stu-id="26fe4-110">short</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="26fe4-111">`sbyte`、`byte`、`ushort`、`uint`、`ulong` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="26fe4-111">`sbyte`, `byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="26fe4-112">ushort</span><span class="sxs-lookup"><span data-stu-id="26fe4-112">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="26fe4-113">`sbyte`、`byte`、`short` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="26fe4-113">`sbyte`, `byte`, `short`, or `char`</span></span>|  
|[<span data-ttu-id="26fe4-114">int</span><span class="sxs-lookup"><span data-stu-id="26fe4-114">int</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="26fe4-115">`sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong` 或 `char`。</span><span class="sxs-lookup"><span data-stu-id="26fe4-115">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`,or `char`</span></span>|  
|[<span data-ttu-id="26fe4-116">uint</span><span class="sxs-lookup"><span data-stu-id="26fe4-116">uint</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="26fe4-117">`sbyte`、`byte`、`short`、`ushort`、`int` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="26fe4-117">`sbyte`, `byte`, `short`, `ushort`, `int`, or `char`</span></span>|  
|[<span data-ttu-id="26fe4-118">long</span><span class="sxs-lookup"><span data-stu-id="26fe4-118">long</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="26fe4-119">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`ulong` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="26fe4-119">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="26fe4-120">ulong</span><span class="sxs-lookup"><span data-stu-id="26fe4-120">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="26fe4-121">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="26fe4-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, or `char`</span></span>|  
|[<span data-ttu-id="26fe4-122">char</span><span class="sxs-lookup"><span data-stu-id="26fe4-122">char</span></span>](char.md)|<span data-ttu-id="26fe4-123">`sbyte`、 `byte`或 `short`</span><span class="sxs-lookup"><span data-stu-id="26fe4-123">`sbyte`, `byte`, or `short`</span></span>|  
|[<span data-ttu-id="26fe4-124">float</span><span class="sxs-lookup"><span data-stu-id="26fe4-124">float</span></span>](../builtin-types/floating-point-numeric-types.md)|<span data-ttu-id="26fe4-125">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="26fe4-125">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`,or `decimal`</span></span>|  
|[<span data-ttu-id="26fe4-126">double</span><span class="sxs-lookup"><span data-stu-id="26fe4-126">double</span></span>](../builtin-types/floating-point-numeric-types.md)|<span data-ttu-id="26fe4-127">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="26fe4-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`,or `decimal`</span></span>|  
|[<span data-ttu-id="26fe4-128">decimal</span><span class="sxs-lookup"><span data-stu-id="26fe4-128">decimal</span></span>](../builtin-types/floating-point-numeric-types.md)|<span data-ttu-id="26fe4-129">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="26fe4-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, or `double`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26fe4-130">備註</span><span class="sxs-lookup"><span data-stu-id="26fe4-130">Remarks</span></span>  
  
- <span data-ttu-id="26fe4-131">明確的數值轉換可能會造成有效位數遺失或導致擲回例外狀況，通常為 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="26fe4-131">The explicit numeric conversion may cause loss of precision or result in throwing an exception, typically an <xref:System.OverflowException>.</span></span>  

- <span data-ttu-id="26fe4-132">將整數型別的值轉換為另一個整數型別時，結果取決於溢位[檢查內容](checked-and-unchecked.md)。</span><span class="sxs-lookup"><span data-stu-id="26fe4-132">When you convert a value of an integral type to another integral type, the result depends on the overflow [checking context](checked-and-unchecked.md).</span></span> <span data-ttu-id="26fe4-133">在已檢查的內容中，如果來源值在目標類型的範圍內，轉換將會成功。</span><span class="sxs-lookup"><span data-stu-id="26fe4-133">In a checked context, the conversion succeeds if the source value is within the range of the destination type.</span></span> <span data-ttu-id="26fe4-134">否則會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="26fe4-134">Otherwise, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="26fe4-135">在未檢查的內容中，轉換一律會成功，並按照如下所示繼續進行：</span><span class="sxs-lookup"><span data-stu-id="26fe4-135">In an unchecked context, the conversion always succeeds, and proceeds as follows:</span></span>

  - <span data-ttu-id="26fe4-136">如果來源類型大於目的地類型，會藉由捨棄其「額外」最高有效位元，來截斷來源值。</span><span class="sxs-lookup"><span data-stu-id="26fe4-136">If the source type is larger than the destination type, then the source value is truncated by discarding its "extra" most significant bits.</span></span> <span data-ttu-id="26fe4-137">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="26fe4-137">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="26fe4-138">如果來源類型小於目標類型，則來源值可以是正負號擴充或零擴充，以使其與目標類型的大小相同。</span><span class="sxs-lookup"><span data-stu-id="26fe4-138">If the source type is smaller than the destination type, then the source value is either sign-extended or zero-extended so that it is the same size as the destination type.</span></span> <span data-ttu-id="26fe4-139">如果來源類型帶正負號，則會使用正負號擴充；如果來源類型不帶正負號，則會使用零擴充。</span><span class="sxs-lookup"><span data-stu-id="26fe4-139">Sign-extension is used if the source type is signed; zero-extension is used if the source type is unsigned.</span></span> <span data-ttu-id="26fe4-140">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="26fe4-140">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="26fe4-141">如果來源類型與目標類型的大小相同，則來源值將視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="26fe4-141">If the source type is the same size as the destination type, then the source value is treated as a value of the destination type.</span></span>
  
- <span data-ttu-id="26fe4-142">當您將 `decimal` 值轉換為整數型別時，這個值會捨入到最接近整數值的零。</span><span class="sxs-lookup"><span data-stu-id="26fe4-142">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="26fe4-143">如果產生的整數值超出目的地類型的範圍，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="26fe4-143">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>  
  
- <span data-ttu-id="26fe4-144">當您將 `double` 或 `float` 值轉換為整數型別時，這個值會往零的方向捨入到最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="26fe4-144">When you convert a `double` or `float` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="26fe4-145">如果產生的整數值超出目的地類型的範圍，結果隨溢位[檢查內容](checked-and-unchecked.md)而異。</span><span class="sxs-lookup"><span data-stu-id="26fe4-145">If the resulting integral value is outside the range of the destination type, the result depends on the overflow [checking context](checked-and-unchecked.md).</span></span> <span data-ttu-id="26fe4-146">在已檢查的內容中會擲回 <xref:System.OverflowException>，而在未經檢查的內容中，結果是目的地類型的未指定值。</span><span class="sxs-lookup"><span data-stu-id="26fe4-146">In a checked context, an <xref:System.OverflowException> is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>  
  
- <span data-ttu-id="26fe4-147">當您將 `double` 轉換成 `float` 時，`double` 值會捨入到最接近 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="26fe4-147">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="26fe4-148">如果 `double` 值太小或太大以致不符合目的地類型，結果會是零或無限大。</span><span class="sxs-lookup"><span data-stu-id="26fe4-148">If the `double` value is too small or too large to fit into the destination type, the result will be zero or infinity.</span></span>  
  
- <span data-ttu-id="26fe4-149">當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換成 `decimal` 表示，必要時捨入到最接近第 28 個小數位數後的數字。</span><span class="sxs-lookup"><span data-stu-id="26fe4-149">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="26fe4-150">視來源值的值而定，可能會發生下列一種結果：</span><span class="sxs-lookup"><span data-stu-id="26fe4-150">Depending on the value of the source value, one of the following results may occur:</span></span>  

  - <span data-ttu-id="26fe4-151">如果來源值太小無法以 `decimal` 表示，結果就會變成零。</span><span class="sxs-lookup"><span data-stu-id="26fe4-151">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>  

  - <span data-ttu-id="26fe4-152">如果來源值是 NaN (不是數字)、無限大或太大，無法以 `decimal` 表示，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="26fe4-152">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an <xref:System.OverflowException> is thrown.</span></span>  
  
- <span data-ttu-id="26fe4-153">當您將 `decimal` 轉換成 `float` 或 `double` 時，`decimal` 值會捨入到最接近 `double` 或 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="26fe4-153">When you convert `decimal` to `float` or `double`, the `decimal` value is rounded to the nearest `double` or `float` value.</span></span>  
  
 <span data-ttu-id="26fe4-154">如需明確轉換的詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[明確轉換](~/_csharplang/spec/conversions.md#explicit-conversions)一節。</span><span class="sxs-lookup"><span data-stu-id="26fe4-154">For more information about explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="26fe4-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26fe4-155">See also</span></span>

- [<span data-ttu-id="26fe4-156">C# 參考</span><span class="sxs-lookup"><span data-stu-id="26fe4-156">C# reference</span></span>](../index.md)
- [<span data-ttu-id="26fe4-157">轉換和類型轉換</span><span class="sxs-lookup"><span data-stu-id="26fe4-157">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="26fe4-158">() 運算子</span><span class="sxs-lookup"><span data-stu-id="26fe4-158">() operator</span></span>](../operators/type-testing-and-conversion-operators.md#cast-operator-)
- [<span data-ttu-id="26fe4-159">整數型別</span><span class="sxs-lookup"><span data-stu-id="26fe4-159">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="26fe4-160">浮點數類型表</span><span class="sxs-lookup"><span data-stu-id="26fe4-160">Floating-point types table</span></span>](../builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="26fe4-161">內建型別表</span><span class="sxs-lookup"><span data-stu-id="26fe4-161">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="26fe4-162">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="26fe4-162">Implicit numeric conversions table</span></span>](implicit-numeric-conversions-table.md)
