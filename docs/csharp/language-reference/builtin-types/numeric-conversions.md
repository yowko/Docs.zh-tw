---
title: 內建數值轉換- C#參考
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5380e8480c39d1940df13b2ecb50a0f394367388
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776030"
---
# <a name="built-in-numeric-conversions-c-reference"></a><span data-ttu-id="16a0a-102">內建數值轉換（C#參考）</span><span class="sxs-lookup"><span data-stu-id="16a0a-102">Built-in numeric conversions (C# reference)</span></span>

<span data-ttu-id="16a0a-103">C#提供一組[整數](integral-numeric-types.md)和[浮點](floating-point-numeric-types.md)數數值型別。</span><span class="sxs-lookup"><span data-stu-id="16a0a-103">C# provides a set of [integral](integral-numeric-types.md) and [floating-point](floating-point-numeric-types.md) numeric types.</span></span> <span data-ttu-id="16a0a-104">任何兩個數數值型別（隱含或明確）之間都有轉換。</span><span class="sxs-lookup"><span data-stu-id="16a0a-104">There exists a conversion between any two numeric types, either implicit or explicit.</span></span> <span data-ttu-id="16a0a-105">您必須使用[cast 運算子 `()`](../operators/type-testing-and-cast.md#cast-operator-)來叫用明確轉換。</span><span class="sxs-lookup"><span data-stu-id="16a0a-105">You must use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span>

## <a name="implicit-numeric-conversions"></a><span data-ttu-id="16a0a-106">隱含數值轉換</span><span class="sxs-lookup"><span data-stu-id="16a0a-106">Implicit numeric conversions</span></span>

<span data-ttu-id="16a0a-107">下表顯示內建數數值型別之間的預先定義隱含轉換：</span><span class="sxs-lookup"><span data-stu-id="16a0a-107">The following table shows the predefined implicit conversions between the built-in numeric types:</span></span>

|<span data-ttu-id="16a0a-108">From</span><span class="sxs-lookup"><span data-stu-id="16a0a-108">From</span></span>|<span data-ttu-id="16a0a-109">若要</span><span class="sxs-lookup"><span data-stu-id="16a0a-109">To</span></span>|
|----------|--------|
|[<span data-ttu-id="16a0a-110">sbyte</span><span class="sxs-lookup"><span data-stu-id="16a0a-110">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-111">`short`、`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="16a0a-111">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-112">byte</span><span class="sxs-lookup"><span data-stu-id="16a0a-112">byte</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-113">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="16a0a-113">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-114">short</span><span class="sxs-lookup"><span data-stu-id="16a0a-114">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-115">`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="16a0a-115">`int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-116">ushort</span><span class="sxs-lookup"><span data-stu-id="16a0a-116">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-117">`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="16a0a-117">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-118">int</span><span class="sxs-lookup"><span data-stu-id="16a0a-118">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-119">`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="16a0a-119">`long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-120">uint</span><span class="sxs-lookup"><span data-stu-id="16a0a-120">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-121">`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="16a0a-121">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-122">long</span><span class="sxs-lookup"><span data-stu-id="16a0a-122">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-123">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="16a0a-123">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-124">ulong</span><span class="sxs-lookup"><span data-stu-id="16a0a-124">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-125">`float`、 `double`或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="16a0a-125">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-126">float</span><span class="sxs-lookup"><span data-stu-id="16a0a-126">float</span></span>](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> <span data-ttu-id="16a0a-127">從 `int`、`uint`、`long` 或 `ulong` 到 `float` 的隱含轉換，或從 `long` 或 `ulong` 到 `double` 可能會導致精確度遺失，但不會遺失任何程度的順序。</span><span class="sxs-lookup"><span data-stu-id="16a0a-127">The implicit conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double` may cause a loss of precision, but never a loss of an order of magnitude.</span></span> <span data-ttu-id="16a0a-128">其他隱含數值轉換永遠不會遺失任何資訊。</span><span class="sxs-lookup"><span data-stu-id="16a0a-128">The other implicit numeric conversions never lose any information.</span></span>

<span data-ttu-id="16a0a-129">另請注意，</span><span class="sxs-lookup"><span data-stu-id="16a0a-129">Also note that</span></span>

- <span data-ttu-id="16a0a-130">任何[整數數數值型別](integral-numeric-types.md)都可以隱含地轉換成任何[浮點數數值型別](floating-point-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="16a0a-130">Any [integral numeric type](integral-numeric-types.md) is implicitly convertible to any [floating-point numeric type](floating-point-numeric-types.md).</span></span>

- <span data-ttu-id="16a0a-131">@No__t_0 和 `sbyte` 類型沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="16a0a-131">There are no implicit conversions to the `byte` and `sbyte` types.</span></span> <span data-ttu-id="16a0a-132">沒有來自 `double` 與 `decimal` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="16a0a-132">There are no implicit conversions from the `double` and `decimal` types.</span></span>

- <span data-ttu-id="16a0a-133">`decimal` 類型和 `float` 或 `double` 類型之間沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="16a0a-133">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>

- <span data-ttu-id="16a0a-134">類型 `int` 的常數運算式值（例如，整數常值所代表的值）可以隱含地轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong` （如果它是在目的地類型的範圍內）。:</span><span class="sxs-lookup"><span data-stu-id="16a0a-134">A value of a constant expression of type `int` (for example, a value represented by an integer literal) can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, if it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  <span data-ttu-id="16a0a-135">如上述範例所示，如果常數值不在目的地類型的範圍內，就會發生編譯器錯誤[CS0031](../../misc/cs0031.md) 。</span><span class="sxs-lookup"><span data-stu-id="16a0a-135">As the preceding example shows, if the constant value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

## <a name="explicit-numeric-conversions"></a><span data-ttu-id="16a0a-136">明確數值轉換</span><span class="sxs-lookup"><span data-stu-id="16a0a-136">Explicit numeric conversions</span></span>

<span data-ttu-id="16a0a-137">下表顯示在沒有[隱含轉換](#implicit-numeric-conversions)的內建數數值型別之間，預先定義的明確轉換：</span><span class="sxs-lookup"><span data-stu-id="16a0a-137">The following table shows the predefined explicit conversions between the built-in numeric types for which there is no [implicit conversion](#implicit-numeric-conversions):</span></span>

|<span data-ttu-id="16a0a-138">From</span><span class="sxs-lookup"><span data-stu-id="16a0a-138">From</span></span>|<span data-ttu-id="16a0a-139">若要</span><span class="sxs-lookup"><span data-stu-id="16a0a-139">To</span></span>|
|----------|--------|
|[<span data-ttu-id="16a0a-140">sbyte</span><span class="sxs-lookup"><span data-stu-id="16a0a-140">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-141">`byte`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="16a0a-141">`byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="16a0a-142">byte</span><span class="sxs-lookup"><span data-stu-id="16a0a-142">byte</span></span>](integral-numeric-types.md)|`sbyte`|
|[<span data-ttu-id="16a0a-143">short</span><span class="sxs-lookup"><span data-stu-id="16a0a-143">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-144">`sbyte`、`byte`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="16a0a-144">`sbyte`, `byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="16a0a-145">ushort</span><span class="sxs-lookup"><span data-stu-id="16a0a-145">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-146">`sbyte`、 `byte`或 `short`</span><span class="sxs-lookup"><span data-stu-id="16a0a-146">`sbyte`, `byte`, or `short`</span></span>|
|[<span data-ttu-id="16a0a-147">int</span><span class="sxs-lookup"><span data-stu-id="16a0a-147">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-148">`sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="16a0a-148">`sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="16a0a-149">uint</span><span class="sxs-lookup"><span data-stu-id="16a0a-149">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-150">`sbyte`、`byte`、`short`、`ushort` 或 `int`</span><span class="sxs-lookup"><span data-stu-id="16a0a-150">`sbyte`, `byte`, `short`, `ushort`, or `int`</span></span>|
|[<span data-ttu-id="16a0a-151">long</span><span class="sxs-lookup"><span data-stu-id="16a0a-151">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-152">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="16a0a-152">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="16a0a-153">ulong</span><span class="sxs-lookup"><span data-stu-id="16a0a-153">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="16a0a-154">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `long`。</span><span class="sxs-lookup"><span data-stu-id="16a0a-154">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `long`</span></span>|
|[<span data-ttu-id="16a0a-155">float</span><span class="sxs-lookup"><span data-stu-id="16a0a-155">float</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="16a0a-156">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="16a0a-156">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-157">double</span><span class="sxs-lookup"><span data-stu-id="16a0a-157">double</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="16a0a-158">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="16a0a-158">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `decimal`</span></span>|
|[<span data-ttu-id="16a0a-159">decimal</span><span class="sxs-lookup"><span data-stu-id="16a0a-159">decimal</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="16a0a-160">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float` 或 `double`</span><span class="sxs-lookup"><span data-stu-id="16a0a-160">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `double`</span></span>|

> [!NOTE]
> <span data-ttu-id="16a0a-161">明確的數值轉換可能會導致資料遺失或擲回例外狀況，通常是 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="16a0a-161">An explicit numeric conversion might result in data loss or throw an exception, typically an <xref:System.OverflowException>.</span></span>

<span data-ttu-id="16a0a-162">另請注意，</span><span class="sxs-lookup"><span data-stu-id="16a0a-162">Also note that</span></span>

- <span data-ttu-id="16a0a-163">將整數型別的值轉換為另一個整數型別時，結果取決於溢位[檢查內容](../keywords/checked-and-unchecked.md)。</span><span class="sxs-lookup"><span data-stu-id="16a0a-163">When you convert a value of an integral type to another integral type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="16a0a-164">在已檢查的內容中，如果來源值在目標類型的範圍內，轉換將會成功。</span><span class="sxs-lookup"><span data-stu-id="16a0a-164">In a checked context, the conversion succeeds if the source value is within the range of the destination type.</span></span> <span data-ttu-id="16a0a-165">否則會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="16a0a-165">Otherwise, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="16a0a-166">在未檢查的內容中，轉換一律會成功，並按照如下所示繼續進行：</span><span class="sxs-lookup"><span data-stu-id="16a0a-166">In an unchecked context, the conversion always succeeds, and proceeds as follows:</span></span>

  - <span data-ttu-id="16a0a-167">如果來源類型大於目的地類型，會藉由捨棄其「額外」最高有效位元，來截斷來源值。</span><span class="sxs-lookup"><span data-stu-id="16a0a-167">If the source type is larger than the destination type, then the source value is truncated by discarding its "extra" most significant bits.</span></span> <span data-ttu-id="16a0a-168">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="16a0a-168">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="16a0a-169">如果來源類型小於目的地類型，則來源值會是 [擴充] 或 [零擴充]，使其大小與目的地類型相同。</span><span class="sxs-lookup"><span data-stu-id="16a0a-169">If the source type is smaller than the destination type, then the source value is either sign-extended or zero-extended so that it's of the same size as the destination type.</span></span> <span data-ttu-id="16a0a-170">如果來源類型帶正負號，則會使用正負號擴充；如果來源類型不帶正負號，則會使用零擴充。</span><span class="sxs-lookup"><span data-stu-id="16a0a-170">Sign-extension is used if the source type is signed; zero-extension is used if the source type is unsigned.</span></span> <span data-ttu-id="16a0a-171">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="16a0a-171">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="16a0a-172">如果來源類型與目標類型的大小相同，則來源值將視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="16a0a-172">If the source type is the same size as the destination type, then the source value is treated as a value of the destination type.</span></span>

- <span data-ttu-id="16a0a-173">當您將 `decimal` 值轉換為整數型別時，這個值會捨入到最接近整數值的零。</span><span class="sxs-lookup"><span data-stu-id="16a0a-173">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="16a0a-174">如果產生的整數值超出目的地類型的範圍，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="16a0a-174">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="16a0a-175">當您將 `double` 或 `float` 值轉換為整數型別時，這個值會往零的方向捨入到最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="16a0a-175">When you convert a `double` or `float` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="16a0a-176">如果產生的整數值超出目的地類型的範圍，結果隨溢位[檢查內容](../keywords/checked-and-unchecked.md)而異。</span><span class="sxs-lookup"><span data-stu-id="16a0a-176">If the resulting integral value is outside the range of the destination type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="16a0a-177">在已檢查的內容中會擲回 <xref:System.OverflowException>，而在未經檢查的內容中，結果是目的地類型的未指定值。</span><span class="sxs-lookup"><span data-stu-id="16a0a-177">In a checked context, an <xref:System.OverflowException> is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>

- <span data-ttu-id="16a0a-178">當您將 `double` 轉換成 `float` 時，`double` 值會捨入到最接近 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="16a0a-178">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="16a0a-179">如果 `double` 值太小或太大，而無法納入 `float` 類型，則結果為零或無限大。</span><span class="sxs-lookup"><span data-stu-id="16a0a-179">If the `double` value is too small or too large to fit into the `float` type, the result is zero or infinity.</span></span>

- <span data-ttu-id="16a0a-180">當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換成 `decimal` 表示，必要時捨入到最接近第 28 個小數位數後的數字。</span><span class="sxs-lookup"><span data-stu-id="16a0a-180">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="16a0a-181">視來源值的值而定，可能會發生下列一種結果：</span><span class="sxs-lookup"><span data-stu-id="16a0a-181">Depending on the value of the source value, one of the following results may occur:</span></span>

  - <span data-ttu-id="16a0a-182">如果來源值太小無法以 `decimal` 表示，結果就會變成零。</span><span class="sxs-lookup"><span data-stu-id="16a0a-182">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>

  - <span data-ttu-id="16a0a-183">如果來源值是 NaN (不是數字)、無限大或太大，無法以 `decimal` 表示，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="16a0a-183">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="16a0a-184">當您將 `decimal` 轉換成 `float` 或 `double` 時，會分別將來源值四捨五入為最接近的 `float` 或 `double` 值。</span><span class="sxs-lookup"><span data-stu-id="16a0a-184">When you convert `decimal` to `float` or `double`, the source value is rounded to the nearest `float` or `double` value, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="16a0a-185">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="16a0a-185">C# language specification</span></span>

<span data-ttu-id="16a0a-186">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="16a0a-186">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="16a0a-187">隱含數值轉換</span><span class="sxs-lookup"><span data-stu-id="16a0a-187">Implicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [<span data-ttu-id="16a0a-188">明確數值轉換</span><span class="sxs-lookup"><span data-stu-id="16a0a-188">Explicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a><span data-ttu-id="16a0a-189">請參閱</span><span class="sxs-lookup"><span data-stu-id="16a0a-189">See also</span></span>

- [<span data-ttu-id="16a0a-190">C# 參考</span><span class="sxs-lookup"><span data-stu-id="16a0a-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="16a0a-191">轉換和類型轉換</span><span class="sxs-lookup"><span data-stu-id="16a0a-191">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
