---
description: 瞭解 C 中內建數數值型別之間的隱含和明確轉換#
title: '內建的數值轉換-c # 參考'
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: ee5def3b5e0e067919a8c8335db701dbb6dd4d88
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142241"
---
# <a name="built-in-numeric-conversions-c-reference"></a><span data-ttu-id="9dbbb-103">內建的數值轉換 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="9dbbb-103">Built-in numeric conversions (C# reference)</span></span>

<span data-ttu-id="9dbbb-104">C # 提供一組 [整數](integral-numeric-types.md) 和 [浮點](floating-point-numeric-types.md) 數數值型別。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-104">C# provides a set of [integral](integral-numeric-types.md) and [floating-point](floating-point-numeric-types.md) numeric types.</span></span> <span data-ttu-id="9dbbb-105">任兩個數數值型別（隱含或明確）之間存在轉換。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-105">There exists a conversion between any two numeric types, either implicit or explicit.</span></span> <span data-ttu-id="9dbbb-106">您必須使用 [cast 運算式](../operators/type-testing-and-cast.md#cast-expression) 來執行明確的轉換。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-106">You must use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span>

## <a name="implicit-numeric-conversions"></a><span data-ttu-id="9dbbb-107">隱含數值轉換</span><span class="sxs-lookup"><span data-stu-id="9dbbb-107">Implicit numeric conversions</span></span>

<span data-ttu-id="9dbbb-108">下表顯示內建數數值型別之間預先定義的隱含轉換：</span><span class="sxs-lookup"><span data-stu-id="9dbbb-108">The following table shows the predefined implicit conversions between the built-in numeric types:</span></span>

|<span data-ttu-id="9dbbb-109">寄件者</span><span class="sxs-lookup"><span data-stu-id="9dbbb-109">From</span></span>|<span data-ttu-id="9dbbb-110">收件者</span><span class="sxs-lookup"><span data-stu-id="9dbbb-110">To</span></span>|
|----------|--------|
|[<span data-ttu-id="9dbbb-111">sbyte</span><span class="sxs-lookup"><span data-stu-id="9dbbb-111">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-112">`short`、`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-112">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-113">byte</span><span class="sxs-lookup"><span data-stu-id="9dbbb-113">byte</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-114">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-114">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-115">short</span><span class="sxs-lookup"><span data-stu-id="9dbbb-115">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-116">`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-116">`int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-117">ushort</span><span class="sxs-lookup"><span data-stu-id="9dbbb-117">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-118">`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-118">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-119">int</span><span class="sxs-lookup"><span data-stu-id="9dbbb-119">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-120">`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-120">`long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-121">uint</span><span class="sxs-lookup"><span data-stu-id="9dbbb-121">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-122">`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-122">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-123">long</span><span class="sxs-lookup"><span data-stu-id="9dbbb-123">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-124">`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-124">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-125">ulong</span><span class="sxs-lookup"><span data-stu-id="9dbbb-125">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-126">`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-126">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-127">float</span><span class="sxs-lookup"><span data-stu-id="9dbbb-127">float</span></span>](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> <span data-ttu-id="9dbbb-128">從 `int` 、 `uint` 、 `long` 或 `ulong` 到 `float` 和 from 或 to 的隱含 `long` 轉換 `ulong` `double` 可能會導致精確度遺失，但永遠不會遺失量值的順序。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-128">The implicit conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double` may cause a loss of precision, but never a loss of an order of magnitude.</span></span> <span data-ttu-id="9dbbb-129">其他的隱含數值轉換絕不會遺失任何資訊。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-129">The other implicit numeric conversions never lose any information.</span></span>

<span data-ttu-id="9dbbb-130">另請注意，</span><span class="sxs-lookup"><span data-stu-id="9dbbb-130">Also note that</span></span>

- <span data-ttu-id="9dbbb-131">任何 [整數數數值型別](integral-numeric-types.md) 都可以隱含地轉換成任何 [浮點數](floating-point-numeric-types.md)型別。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-131">Any [integral numeric type](integral-numeric-types.md) is implicitly convertible to any [floating-point numeric type](floating-point-numeric-types.md).</span></span>

- <span data-ttu-id="9dbbb-132">和類型沒有隱含的轉換 `byte` `sbyte` 。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-132">There are no implicit conversions to the `byte` and `sbyte` types.</span></span> <span data-ttu-id="9dbbb-133">沒有來自 `double` 與 `decimal` 類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-133">There are no implicit conversions from the `double` and `decimal` types.</span></span>

- <span data-ttu-id="9dbbb-134">`decimal` 類型和 `float` 或 `double` 類型之間沒有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-134">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>

- <span data-ttu-id="9dbbb-135">型別的常數運算式值 `int` (例如，整數常值所代表的值) 可以隱含地轉換成 `sbyte` 、 `byte` 、 `short` 、 `ushort` 、 `uint` 或 `ulong` ，如果它是在目的地類型的範圍內：</span><span class="sxs-lookup"><span data-stu-id="9dbbb-135">A value of a constant expression of type `int` (for example, a value represented by an integer literal) can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, if it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  <span data-ttu-id="9dbbb-136">如先前的範例所示，如果常數值不在目的類型範圍內，就會發生編譯器錯誤 [CS0031](../../misc/cs0031.md) 。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-136">As the preceding example shows, if the constant value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

## <a name="explicit-numeric-conversions"></a><span data-ttu-id="9dbbb-137">明確數值轉換</span><span class="sxs-lookup"><span data-stu-id="9dbbb-137">Explicit numeric conversions</span></span>

<span data-ttu-id="9dbbb-138">下表顯示內建數數值型別（沒有 [隱含轉換](#implicit-numeric-conversions)）之間的預先定義明確轉換：</span><span class="sxs-lookup"><span data-stu-id="9dbbb-138">The following table shows the predefined explicit conversions between the built-in numeric types for which there is no [implicit conversion](#implicit-numeric-conversions):</span></span>

|<span data-ttu-id="9dbbb-139">寄件者</span><span class="sxs-lookup"><span data-stu-id="9dbbb-139">From</span></span>|<span data-ttu-id="9dbbb-140">收件者</span><span class="sxs-lookup"><span data-stu-id="9dbbb-140">To</span></span>|
|----------|--------|
|[<span data-ttu-id="9dbbb-141">sbyte</span><span class="sxs-lookup"><span data-stu-id="9dbbb-141">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-142">`byte`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-142">`byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="9dbbb-143">byte</span><span class="sxs-lookup"><span data-stu-id="9dbbb-143">byte</span></span>](integral-numeric-types.md)|`sbyte`|
|[<span data-ttu-id="9dbbb-144">short</span><span class="sxs-lookup"><span data-stu-id="9dbbb-144">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-145">`sbyte`、`byte`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-145">`sbyte`, `byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="9dbbb-146">ushort</span><span class="sxs-lookup"><span data-stu-id="9dbbb-146">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-147">`sbyte`、`byte` 或 `short`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-147">`sbyte`, `byte`, or `short`</span></span>|
|[<span data-ttu-id="9dbbb-148">int</span><span class="sxs-lookup"><span data-stu-id="9dbbb-148">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-149">`sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-149">`sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="9dbbb-150">uint</span><span class="sxs-lookup"><span data-stu-id="9dbbb-150">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-151">`sbyte`、`byte`、`short`、`ushort` 或 `int`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-151">`sbyte`, `byte`, `short`, `ushort`, or `int`</span></span>|
|[<span data-ttu-id="9dbbb-152">long</span><span class="sxs-lookup"><span data-stu-id="9dbbb-152">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-153">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-153">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="9dbbb-154">ulong</span><span class="sxs-lookup"><span data-stu-id="9dbbb-154">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="9dbbb-155">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `long`。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-155">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `long`</span></span>|
|[<span data-ttu-id="9dbbb-156">float</span><span class="sxs-lookup"><span data-stu-id="9dbbb-156">float</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="9dbbb-157">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-157">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-158">double</span><span class="sxs-lookup"><span data-stu-id="9dbbb-158">double</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="9dbbb-159">`sbyte`、 `byte` 、 `short` 、 `ushort` 、 `int` 、 `uint` 、 `long` `ulong` `float` 、、或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-159">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `decimal`</span></span>|
|[<span data-ttu-id="9dbbb-160">decimal</span><span class="sxs-lookup"><span data-stu-id="9dbbb-160">decimal</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="9dbbb-161">`sbyte`、 `byte` 、 `short` 、 `ushort` 、 `int` 、 `uint` 、 `long` `ulong` `float` 、、或 `double`</span><span class="sxs-lookup"><span data-stu-id="9dbbb-161">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `double`</span></span>|

> [!NOTE]
> <span data-ttu-id="9dbbb-162">明確的數值轉換可能會造成資料遺失或擲回例外狀況，通常是 <xref:System.OverflowException> 。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-162">An explicit numeric conversion might result in data loss or throw an exception, typically an <xref:System.OverflowException>.</span></span>

<span data-ttu-id="9dbbb-163">另請注意，</span><span class="sxs-lookup"><span data-stu-id="9dbbb-163">Also note that</span></span>

- <span data-ttu-id="9dbbb-164">將整數型別的值轉換為另一個整數型別時，結果取決於溢位[檢查內容](../keywords/checked-and-unchecked.md)。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-164">When you convert a value of an integral type to another integral type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="9dbbb-165">在已檢查的內容中，如果來源值在目標類型的範圍內，轉換將會成功。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-165">In a checked context, the conversion succeeds if the source value is within the range of the destination type.</span></span> <span data-ttu-id="9dbbb-166">否則會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-166">Otherwise, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="9dbbb-167">在未檢查的內容中，轉換一律會成功，並按照如下所示繼續進行：</span><span class="sxs-lookup"><span data-stu-id="9dbbb-167">In an unchecked context, the conversion always succeeds, and proceeds as follows:</span></span>

  - <span data-ttu-id="9dbbb-168">如果來源類型大於目的地類型，會藉由捨棄其「額外」最高有效位元，來截斷來源值。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-168">If the source type is larger than the destination type, then the source value is truncated by discarding its "extra" most significant bits.</span></span> <span data-ttu-id="9dbbb-169">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-169">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="9dbbb-170">如果來源類型小於目的地類型，則來源值會是「簽章」或「零延伸」，使其大小與目的地類型相同。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-170">If the source type is smaller than the destination type, then the source value is either sign-extended or zero-extended so that it's of the same size as the destination type.</span></span> <span data-ttu-id="9dbbb-171">如果來源類型帶正負號，則會使用正負號擴充；如果來源類型不帶正負號，則會使用零擴充。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-171">Sign-extension is used if the source type is signed; zero-extension is used if the source type is unsigned.</span></span> <span data-ttu-id="9dbbb-172">然後會將結果視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-172">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="9dbbb-173">如果來源類型與目標類型的大小相同，則來源值將視為目標類型的值。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-173">If the source type is the same size as the destination type, then the source value is treated as a value of the destination type.</span></span>

- <span data-ttu-id="9dbbb-174">當您將 `decimal` 值轉換為整數型別時，這個值會捨入到最接近整數值的零。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-174">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="9dbbb-175">如果產生的整數值超出目的地類型的範圍，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-175">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="9dbbb-176">當您將 `double` 或 `float` 值轉換為整數型別時，這個值會往零的方向捨入到最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-176">When you convert a `double` or `float` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="9dbbb-177">如果產生的整數值超出目的地類型的範圍，結果隨溢位[檢查內容](../keywords/checked-and-unchecked.md)而異。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-177">If the resulting integral value is outside the range of the destination type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="9dbbb-178">在已檢查的內容中會擲回 <xref:System.OverflowException>，而在未經檢查的內容中，結果是目的地類型的未指定值。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-178">In a checked context, an <xref:System.OverflowException> is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>

- <span data-ttu-id="9dbbb-179">當您將 `double` 轉換成 `float` 時，`double` 值會捨入到最接近 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-179">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="9dbbb-180">如果 `double` 值太小或太大而無法放入 `float` 類型中，則結果為零或無限大。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-180">If the `double` value is too small or too large to fit into the `float` type, the result is zero or infinity.</span></span>

- <span data-ttu-id="9dbbb-181">當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換成 `decimal` 表示，必要時捨入到最接近第 28 個小數位數後的數字。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-181">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="9dbbb-182">視來源值的值而定，可能會發生下列一種結果：</span><span class="sxs-lookup"><span data-stu-id="9dbbb-182">Depending on the value of the source value, one of the following results may occur:</span></span>

  - <span data-ttu-id="9dbbb-183">如果來源值太小無法以 `decimal` 表示，結果就會變成零。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-183">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>

  - <span data-ttu-id="9dbbb-184">如果來源值是 NaN (不是數字)、無限大或太大，無法以 `decimal` 表示，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-184">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="9dbbb-185">當您轉換 `decimal` 成 `float` 或時 `double` ，來源值會分別四捨五入為最接近或最接近的 `float` `double` 值。</span><span class="sxs-lookup"><span data-stu-id="9dbbb-185">When you convert `decimal` to `float` or `double`, the source value is rounded to the nearest `float` or `double` value, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9dbbb-186">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9dbbb-186">C# language specification</span></span>

<span data-ttu-id="9dbbb-187">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="9dbbb-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="9dbbb-188">隱含數值轉換</span><span class="sxs-lookup"><span data-stu-id="9dbbb-188">Implicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [<span data-ttu-id="9dbbb-189">明確數值轉換</span><span class="sxs-lookup"><span data-stu-id="9dbbb-189">Explicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a><span data-ttu-id="9dbbb-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dbbb-190">See also</span></span>

- [<span data-ttu-id="9dbbb-191">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="9dbbb-191">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9dbbb-192">轉換和類型轉換</span><span class="sxs-lookup"><span data-stu-id="9dbbb-192">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
