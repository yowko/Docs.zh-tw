---
title: 內建數值轉換 - C# 參考
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: b7d53e508e4d585c746a3cc61824cdace7707deb
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121456"
---
# <a name="built-in-numeric-conversions-c-reference"></a><span data-ttu-id="3de3f-102">內建數值轉換(C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3de3f-102">Built-in numeric conversions (C# reference)</span></span>

<span data-ttu-id="3de3f-103">C# 提供一組[積分](integral-numeric-types.md)和[浮點](floating-point-numeric-types.md)數值類型。</span><span class="sxs-lookup"><span data-stu-id="3de3f-103">C# provides a set of [integral](integral-numeric-types.md) and [floating-point](floating-point-numeric-types.md) numeric types.</span></span> <span data-ttu-id="3de3f-104">任何兩種數位類型(隱式或顯式類型)之間存在轉換。</span><span class="sxs-lookup"><span data-stu-id="3de3f-104">There exists a conversion between any two numeric types, either implicit or explicit.</span></span> <span data-ttu-id="3de3f-105">您必須使用[強制轉換表達式](../operators/type-testing-and-cast.md#cast-expression)來執行顯式轉換。</span><span class="sxs-lookup"><span data-stu-id="3de3f-105">You must use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span>

## <a name="implicit-numeric-conversions"></a><span data-ttu-id="3de3f-106">隱含數值轉換</span><span class="sxs-lookup"><span data-stu-id="3de3f-106">Implicit numeric conversions</span></span>

<span data-ttu-id="3de3f-107">下表顯示內置數值型態之間的預定義隱式轉換:</span><span class="sxs-lookup"><span data-stu-id="3de3f-107">The following table shows the predefined implicit conversions between the built-in numeric types:</span></span>

|<span data-ttu-id="3de3f-108">從</span><span class="sxs-lookup"><span data-stu-id="3de3f-108">From</span></span>|<span data-ttu-id="3de3f-109">至</span><span class="sxs-lookup"><span data-stu-id="3de3f-109">To</span></span>|
|----------|--------|
|[<span data-ttu-id="3de3f-110">sbyte</span><span class="sxs-lookup"><span data-stu-id="3de3f-110">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-111">`short`、`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="3de3f-111">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-112">byte</span><span class="sxs-lookup"><span data-stu-id="3de3f-112">byte</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-113">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="3de3f-113">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-114">short</span><span class="sxs-lookup"><span data-stu-id="3de3f-114">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-115">`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="3de3f-115">`int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-116">ushort</span><span class="sxs-lookup"><span data-stu-id="3de3f-116">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-117">`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="3de3f-117">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-118">int</span><span class="sxs-lookup"><span data-stu-id="3de3f-118">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-119">`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="3de3f-119">`long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-120">uint</span><span class="sxs-lookup"><span data-stu-id="3de3f-120">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-121">`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="3de3f-121">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-122">長</span><span class="sxs-lookup"><span data-stu-id="3de3f-122">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-123">`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="3de3f-123">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-124">ulong</span><span class="sxs-lookup"><span data-stu-id="3de3f-124">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-125">`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="3de3f-125">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-126">浮動</span><span class="sxs-lookup"><span data-stu-id="3de3f-126">float</span></span>](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> <span data-ttu-id="3de3f-127">從`int``uint`、 `long`、`ulong``float`或`long`到`ulong``double`和到和到的隱式轉換可能會導致精度損失, 但永遠不會損失數量級。</span><span class="sxs-lookup"><span data-stu-id="3de3f-127">The implicit conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double` may cause a loss of precision, but never a loss of an order of magnitude.</span></span> <span data-ttu-id="3de3f-128">其他隱式數位轉換永遠不會丟失任何資訊。</span><span class="sxs-lookup"><span data-stu-id="3de3f-128">The other implicit numeric conversions never lose any information.</span></span>

<span data-ttu-id="3de3f-129">另請注意</span><span class="sxs-lookup"><span data-stu-id="3de3f-129">Also note that</span></span>

- <span data-ttu-id="3de3f-130">任何[位置數值型態](integral-numeric-types.md)都隱式轉換為任何[浮點數值類型](floating-point-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="3de3f-130">Any [integral numeric type](integral-numeric-types.md) is implicitly convertible to any [floating-point numeric type](floating-point-numeric-types.md).</span></span>

- <span data-ttu-id="3de3f-131">沒有對和`byte``sbyte`類型的隱式轉換。</span><span class="sxs-lookup"><span data-stu-id="3de3f-131">There are no implicit conversions to the `byte` and `sbyte` types.</span></span> <span data-ttu-id="3de3f-132">沒有來自 `double` 與 `decimal` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="3de3f-132">There are no implicit conversions from the `double` and `decimal` types.</span></span>

- <span data-ttu-id="3de3f-133">`decimal` 類型和 `float` 或 `double` 類型之間沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="3de3f-133">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>

- <span data-ttu-id="3de3f-134">類型`int`常數表示式的值(例如,由整數文字表示的值)可以隱式轉換`sbyte`為`ulong``byte``short``ushort``uint`、、、、、、、、、、、、、 或 ,如果該值位於目標類型的範圍內:</span><span class="sxs-lookup"><span data-stu-id="3de3f-134">A value of a constant expression of type `int` (for example, a value represented by an integer literal) can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, if it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  <span data-ttu-id="3de3f-135">如前面的示例所示,如果常量值不在目標類型範圍內,則會發生編譯器錯誤[CS0031。](../../misc/cs0031.md)</span><span class="sxs-lookup"><span data-stu-id="3de3f-135">As the preceding example shows, if the constant value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

## <a name="explicit-numeric-conversions"></a><span data-ttu-id="3de3f-136">明確數值轉換</span><span class="sxs-lookup"><span data-stu-id="3de3f-136">Explicit numeric conversions</span></span>

<span data-ttu-id="3de3f-137">下表顯示了沒有[隱式轉換](#implicit-numeric-conversions)的內建數字型態之間的預定義顯式轉換:</span><span class="sxs-lookup"><span data-stu-id="3de3f-137">The following table shows the predefined explicit conversions between the built-in numeric types for which there is no [implicit conversion](#implicit-numeric-conversions):</span></span>

|<span data-ttu-id="3de3f-138">從</span><span class="sxs-lookup"><span data-stu-id="3de3f-138">From</span></span>|<span data-ttu-id="3de3f-139">至</span><span class="sxs-lookup"><span data-stu-id="3de3f-139">To</span></span>|
|----------|--------|
|[<span data-ttu-id="3de3f-140">sbyte</span><span class="sxs-lookup"><span data-stu-id="3de3f-140">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-141">`byte`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="3de3f-141">`byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="3de3f-142">byte</span><span class="sxs-lookup"><span data-stu-id="3de3f-142">byte</span></span>](integral-numeric-types.md)|`sbyte`|
|[<span data-ttu-id="3de3f-143">short</span><span class="sxs-lookup"><span data-stu-id="3de3f-143">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-144">`sbyte`、`byte`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="3de3f-144">`sbyte`, `byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="3de3f-145">ushort</span><span class="sxs-lookup"><span data-stu-id="3de3f-145">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-146">`sbyte`、`byte` 或 `short`</span><span class="sxs-lookup"><span data-stu-id="3de3f-146">`sbyte`, `byte`, or `short`</span></span>|
|[<span data-ttu-id="3de3f-147">int</span><span class="sxs-lookup"><span data-stu-id="3de3f-147">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-148">`sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="3de3f-148">`sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="3de3f-149">uint</span><span class="sxs-lookup"><span data-stu-id="3de3f-149">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-150">`sbyte`、`byte`、`short`、`ushort` 或 `int`</span><span class="sxs-lookup"><span data-stu-id="3de3f-150">`sbyte`, `byte`, `short`, `ushort`, or `int`</span></span>|
|[<span data-ttu-id="3de3f-151">長</span><span class="sxs-lookup"><span data-stu-id="3de3f-151">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-152">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="3de3f-152">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="3de3f-153">ulong</span><span class="sxs-lookup"><span data-stu-id="3de3f-153">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="3de3f-154">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `long`。</span><span class="sxs-lookup"><span data-stu-id="3de3f-154">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `long`</span></span>|
|[<span data-ttu-id="3de3f-155">浮動</span><span class="sxs-lookup"><span data-stu-id="3de3f-155">float</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="3de3f-156">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="3de3f-156">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-157">double</span><span class="sxs-lookup"><span data-stu-id="3de3f-157">double</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="3de3f-158">`sbyte``byte` `short` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `ushort` `int` `uint` `long` `ulong` `float``decimal`</span><span class="sxs-lookup"><span data-stu-id="3de3f-158">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `decimal`</span></span>|
|[<span data-ttu-id="3de3f-159">decimal</span><span class="sxs-lookup"><span data-stu-id="3de3f-159">decimal</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="3de3f-160">`sbyte``byte` `short` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `ushort` `int` `uint` `long` `ulong` `float``double`</span><span class="sxs-lookup"><span data-stu-id="3de3f-160">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `double`</span></span>|

> [!NOTE]
> <span data-ttu-id="3de3f-161">顯式數位轉換可能會導致數據丟失或引發異常(通常<xref:System.OverflowException>是)。</span><span class="sxs-lookup"><span data-stu-id="3de3f-161">An explicit numeric conversion might result in data loss or throw an exception, typically an <xref:System.OverflowException>.</span></span>

<span data-ttu-id="3de3f-162">另請注意</span><span class="sxs-lookup"><span data-stu-id="3de3f-162">Also note that</span></span>

- <span data-ttu-id="3de3f-163">將整數型別的值轉換為另一個整數型別時，結果取決於溢位[檢查內容](../keywords/checked-and-unchecked.md)。</span><span class="sxs-lookup"><span data-stu-id="3de3f-163">When you convert a value of an integral type to another integral type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="3de3f-164">在已檢查的內容中，如果來源值在目標類型的範圍內，轉換將會成功。</span><span class="sxs-lookup"><span data-stu-id="3de3f-164">In a checked context, the conversion succeeds if the source value is within the range of the destination type.</span></span> <span data-ttu-id="3de3f-165">否則會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="3de3f-165">Otherwise, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="3de3f-166">在未檢查的內容中，轉換一律會成功，並按照如下所示繼續進行：</span><span class="sxs-lookup"><span data-stu-id="3de3f-166">In an unchecked context, the conversion always succeeds, and proceeds as follows:</span></span>

  - <span data-ttu-id="3de3f-167">如果來源類型大於目的地類型，會藉由捨棄其「額外」最高有效位元，來截斷來源值。</span><span class="sxs-lookup"><span data-stu-id="3de3f-167">If the source type is larger than the destination type, then the source value is truncated by discarding its "extra" most significant bits.</span></span> <span data-ttu-id="3de3f-168">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="3de3f-168">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="3de3f-169">如果源類型小於目標類型,則源值是符號擴展或零擴展,以便其大小與目標類型相同。</span><span class="sxs-lookup"><span data-stu-id="3de3f-169">If the source type is smaller than the destination type, then the source value is either sign-extended or zero-extended so that it's of the same size as the destination type.</span></span> <span data-ttu-id="3de3f-170">如果來源類型帶正負號，則會使用正負號擴充；如果來源類型不帶正負號，則會使用零擴充。</span><span class="sxs-lookup"><span data-stu-id="3de3f-170">Sign-extension is used if the source type is signed; zero-extension is used if the source type is unsigned.</span></span> <span data-ttu-id="3de3f-171">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="3de3f-171">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="3de3f-172">如果來源類型與目標類型的大小相同，則來源值將視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="3de3f-172">If the source type is the same size as the destination type, then the source value is treated as a value of the destination type.</span></span>

- <span data-ttu-id="3de3f-173">當您將 `decimal` 值轉換為整數型別時，這個值會捨入到最接近整數值的零。</span><span class="sxs-lookup"><span data-stu-id="3de3f-173">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="3de3f-174">如果產生的整數值超出目的地類型的範圍，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="3de3f-174">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="3de3f-175">當您將 `double` 或 `float` 值轉換為整數型別時，這個值會往零的方向捨入到最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="3de3f-175">When you convert a `double` or `float` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="3de3f-176">如果產生的整數值超出目的地類型的範圍，結果隨溢位[檢查內容](../keywords/checked-and-unchecked.md)而異。</span><span class="sxs-lookup"><span data-stu-id="3de3f-176">If the resulting integral value is outside the range of the destination type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="3de3f-177">在已檢查的內容中會擲回 <xref:System.OverflowException>，而在未經檢查的內容中，結果是目的地類型的未指定值。</span><span class="sxs-lookup"><span data-stu-id="3de3f-177">In a checked context, an <xref:System.OverflowException> is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>

- <span data-ttu-id="3de3f-178">當您將 `double` 轉換成 `float` 時，`double` 值會捨入到最接近 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="3de3f-178">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="3de3f-179">如果`double`該值太小或太大,無法放入類型`float`, 則結果為零或無窮大。</span><span class="sxs-lookup"><span data-stu-id="3de3f-179">If the `double` value is too small or too large to fit into the `float` type, the result is zero or infinity.</span></span>

- <span data-ttu-id="3de3f-180">當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換成 `decimal` 表示，必要時捨入到最接近第 28 個小數位數後的數字。</span><span class="sxs-lookup"><span data-stu-id="3de3f-180">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="3de3f-181">視來源值的值而定，可能會發生下列一種結果：</span><span class="sxs-lookup"><span data-stu-id="3de3f-181">Depending on the value of the source value, one of the following results may occur:</span></span>

  - <span data-ttu-id="3de3f-182">如果來源值太小無法以 `decimal` 表示，結果就會變成零。</span><span class="sxs-lookup"><span data-stu-id="3de3f-182">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>

  - <span data-ttu-id="3de3f-183">如果來源值是 NaN (不是數字)、無限大或太大，無法以 `decimal` 表示，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="3de3f-183">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="3de3f-184">轉換為`decimal``float``double`或 時,源值將分別捨入`float`到`double`最近值 或值。</span><span class="sxs-lookup"><span data-stu-id="3de3f-184">When you convert `decimal` to `float` or `double`, the source value is rounded to the nearest `float` or `double` value, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3de3f-185">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3de3f-185">C# language specification</span></span>

<span data-ttu-id="3de3f-186">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="3de3f-186">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="3de3f-187">隱含數值轉換</span><span class="sxs-lookup"><span data-stu-id="3de3f-187">Implicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [<span data-ttu-id="3de3f-188">明確數值轉換</span><span class="sxs-lookup"><span data-stu-id="3de3f-188">Explicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a><span data-ttu-id="3de3f-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3de3f-189">See also</span></span>

- [<span data-ttu-id="3de3f-190">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3de3f-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3de3f-191">鑄造和類型轉換</span><span class="sxs-lookup"><span data-stu-id="3de3f-191">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
