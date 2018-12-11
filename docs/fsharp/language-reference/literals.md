---
title: 常值 (F#)
description: 深入了解中的常值型別F#程式設計語言。
ms.date: 05/16/2016
ms.openlocfilehash: 7a531cd63c5a4dc1123834d481fc998216b0d82d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131335"
---
# <a name="literals"></a><span data-ttu-id="e0917-103">常值</span><span class="sxs-lookup"><span data-stu-id="e0917-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="e0917-104">這篇文章中的 API 參考連結將帶您前往 MSDN （適用於目前）。</span><span class="sxs-lookup"><span data-stu-id="e0917-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="e0917-105">本主題提供示範如何指定類型的常值中的資料表F#。</span><span class="sxs-lookup"><span data-stu-id="e0917-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="e0917-106">常值類型</span><span class="sxs-lookup"><span data-stu-id="e0917-106">Literal Types</span></span>

<span data-ttu-id="e0917-107">下表顯示中的常值型別F#。</span><span class="sxs-lookup"><span data-stu-id="e0917-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="e0917-108">表示之數字的十六進位表示法的字元不區分大小寫，識別類型的字元會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e0917-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="e0917-109">類型</span><span class="sxs-lookup"><span data-stu-id="e0917-109">Type</span></span>|<span data-ttu-id="e0917-110">描述</span><span class="sxs-lookup"><span data-stu-id="e0917-110">Description</span></span>|<span data-ttu-id="e0917-111">後置字元或前置詞</span><span class="sxs-lookup"><span data-stu-id="e0917-111">Suffix or prefix</span></span>|<span data-ttu-id="e0917-112">範例</span><span class="sxs-lookup"><span data-stu-id="e0917-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="e0917-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="e0917-113">sbyte</span></span>|<span data-ttu-id="e0917-114">帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="e0917-114">signed 8-bit integer</span></span>|<span data-ttu-id="e0917-115">y</span><span class="sxs-lookup"><span data-stu-id="e0917-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="e0917-116">byte</span><span class="sxs-lookup"><span data-stu-id="e0917-116">byte</span></span>|<span data-ttu-id="e0917-117">不帶正負號的 8 位元自然數</span><span class="sxs-lookup"><span data-stu-id="e0917-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="e0917-118">uy</span><span class="sxs-lookup"><span data-stu-id="e0917-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="e0917-119">int16</span><span class="sxs-lookup"><span data-stu-id="e0917-119">int16</span></span>|<span data-ttu-id="e0917-120">帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="e0917-120">signed 16-bit integer</span></span>|<span data-ttu-id="e0917-121">秒</span><span class="sxs-lookup"><span data-stu-id="e0917-121">s</span></span>|`86s`|
|<span data-ttu-id="e0917-122">uint16</span><span class="sxs-lookup"><span data-stu-id="e0917-122">uint16</span></span>|<span data-ttu-id="e0917-123">不帶正負號的 16 位元自然數</span><span class="sxs-lookup"><span data-stu-id="e0917-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="e0917-124">us</span><span class="sxs-lookup"><span data-stu-id="e0917-124">us</span></span>|`86us`|
|<span data-ttu-id="e0917-125">int</span><span class="sxs-lookup"><span data-stu-id="e0917-125">int</span></span><br /><br /><span data-ttu-id="e0917-126">int32</span><span class="sxs-lookup"><span data-stu-id="e0917-126">int32</span></span>|<span data-ttu-id="e0917-127">帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="e0917-127">signed 32-bit integer</span></span>|<span data-ttu-id="e0917-128">l 或 none</span><span class="sxs-lookup"><span data-stu-id="e0917-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="e0917-129">uint</span><span class="sxs-lookup"><span data-stu-id="e0917-129">uint</span></span><br /><br /><span data-ttu-id="e0917-130">uint32</span><span class="sxs-lookup"><span data-stu-id="e0917-130">uint32</span></span>|<span data-ttu-id="e0917-131">不帶正負號的 32 位元自然數</span><span class="sxs-lookup"><span data-stu-id="e0917-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="e0917-132">u 或 ul</span><span class="sxs-lookup"><span data-stu-id="e0917-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="e0917-133">unativeint</span><span class="sxs-lookup"><span data-stu-id="e0917-133">unativeint</span></span>|<span data-ttu-id="e0917-134">為不帶正負號自然數的原生指標</span><span class="sxs-lookup"><span data-stu-id="e0917-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="e0917-135">取消</span><span class="sxs-lookup"><span data-stu-id="e0917-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="e0917-136">int64</span><span class="sxs-lookup"><span data-stu-id="e0917-136">int64</span></span>|<span data-ttu-id="e0917-137">帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="e0917-137">signed 64-bit integer</span></span>|<span data-ttu-id="e0917-138">L</span><span class="sxs-lookup"><span data-stu-id="e0917-138">L</span></span>|`86L`|
|<span data-ttu-id="e0917-139">uint64</span><span class="sxs-lookup"><span data-stu-id="e0917-139">uint64</span></span>|<span data-ttu-id="e0917-140">不帶正負號的 64 位元自然數</span><span class="sxs-lookup"><span data-stu-id="e0917-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="e0917-141">UL</span><span class="sxs-lookup"><span data-stu-id="e0917-141">UL</span></span>|`86UL`|
|<span data-ttu-id="e0917-142">single、float32</span><span class="sxs-lookup"><span data-stu-id="e0917-142">single, float32</span></span>|<span data-ttu-id="e0917-143">32 位元浮點數</span><span class="sxs-lookup"><span data-stu-id="e0917-143">32-bit floating point number</span></span>|<span data-ttu-id="e0917-144">F 或 f</span><span class="sxs-lookup"><span data-stu-id="e0917-144">F or f</span></span>|<span data-ttu-id="e0917-145">`4.14F` 或 `4.14f`</span><span class="sxs-lookup"><span data-stu-id="e0917-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="e0917-146">lf</span><span class="sxs-lookup"><span data-stu-id="e0917-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="e0917-147">浮點數;double</span><span class="sxs-lookup"><span data-stu-id="e0917-147">float; double</span></span>|<span data-ttu-id="e0917-148">64 位元浮點數</span><span class="sxs-lookup"><span data-stu-id="e0917-148">64-bit floating point number</span></span>|<span data-ttu-id="e0917-149">無</span><span class="sxs-lookup"><span data-stu-id="e0917-149">none</span></span>|<span data-ttu-id="e0917-150">`4.14`、`2.3E+32` 或 `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="e0917-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="e0917-151">LF</span><span class="sxs-lookup"><span data-stu-id="e0917-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="e0917-152">bigint</span><span class="sxs-lookup"><span data-stu-id="e0917-152">bigint</span></span>|<span data-ttu-id="e0917-153">不限於 64 位元表示的整數</span><span class="sxs-lookup"><span data-stu-id="e0917-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="e0917-154">I</span><span class="sxs-lookup"><span data-stu-id="e0917-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="e0917-155">decimal</span><span class="sxs-lookup"><span data-stu-id="e0917-155">decimal</span></span>|<span data-ttu-id="e0917-156">以固定點或有理數表示的小數數字</span><span class="sxs-lookup"><span data-stu-id="e0917-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="e0917-157">M 或 m</span><span class="sxs-lookup"><span data-stu-id="e0917-157">M or m</span></span>|<span data-ttu-id="e0917-158">`0.7833M` 或 `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="e0917-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="e0917-159">Char</span><span class="sxs-lookup"><span data-stu-id="e0917-159">Char</span></span>|<span data-ttu-id="e0917-160">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="e0917-160">Unicode character</span></span>|<span data-ttu-id="e0917-161">無</span><span class="sxs-lookup"><span data-stu-id="e0917-161">none</span></span>|`'a'`|
|<span data-ttu-id="e0917-162">String</span><span class="sxs-lookup"><span data-stu-id="e0917-162">String</span></span>|<span data-ttu-id="e0917-163">Unicode 字串</span><span class="sxs-lookup"><span data-stu-id="e0917-163">Unicode string</span></span>|<span data-ttu-id="e0917-164">無</span><span class="sxs-lookup"><span data-stu-id="e0917-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="e0917-165">或</span><span class="sxs-lookup"><span data-stu-id="e0917-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="e0917-166">或</span><span class="sxs-lookup"><span data-stu-id="e0917-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="e0917-167">或</span><span class="sxs-lookup"><span data-stu-id="e0917-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="e0917-168">另請參閱[字串](Strings.md)。</span><span class="sxs-lookup"><span data-stu-id="e0917-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="e0917-169">byte</span><span class="sxs-lookup"><span data-stu-id="e0917-169">byte</span></span>|<span data-ttu-id="e0917-170">ASCII 字元</span><span class="sxs-lookup"><span data-stu-id="e0917-170">ASCII character</span></span>|<span data-ttu-id="e0917-171">B</span><span class="sxs-lookup"><span data-stu-id="e0917-171">B</span></span>|`'a'B`|
|<span data-ttu-id="e0917-172">byte[]</span><span class="sxs-lookup"><span data-stu-id="e0917-172">byte[]</span></span>|<span data-ttu-id="e0917-173">ASCII 字串</span><span class="sxs-lookup"><span data-stu-id="e0917-173">ASCII string</span></span>|<span data-ttu-id="e0917-174">B</span><span class="sxs-lookup"><span data-stu-id="e0917-174">B</span></span>|`"text"B`|
|<span data-ttu-id="e0917-175">字串或 byte]</span><span class="sxs-lookup"><span data-stu-id="e0917-175">String or byte[]</span></span>|<span data-ttu-id="e0917-176">逐字字串</span><span class="sxs-lookup"><span data-stu-id="e0917-176">verbatim string</span></span>|<span data-ttu-id="e0917-177">@ 前置詞</span><span class="sxs-lookup"><span data-stu-id="e0917-177">@ prefix</span></span>|<span data-ttu-id="e0917-178">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="e0917-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="e0917-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="e0917-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0917-180">備註</span><span class="sxs-lookup"><span data-stu-id="e0917-180">Remarks</span></span>

<span data-ttu-id="e0917-181">Unicode 字串可以包含您可以使用指定的明確編碼`\u`後面的 16 位元的十六進位碼或您可以使用指定的 UTF-32 編碼`\U`後面接著 32 位元的十六進位代碼，表示 Unicodesurrogate 字組。</span><span class="sxs-lookup"><span data-stu-id="e0917-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="e0917-182">從F#3.1 中，您可以使用`+`登入合併字串常值。</span><span class="sxs-lookup"><span data-stu-id="e0917-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="e0917-183">您也可以使用位元或 (`|||`) 運算子合併列舉旗標。</span><span class="sxs-lookup"><span data-stu-id="e0917-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="e0917-184">例如，下列程式碼是合法的在F#3.1:</span><span class="sxs-lookup"><span data-stu-id="e0917-184">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let literal1 = "a" + "b"

[<Literal>]
let fileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let literal2 = 1 ||| 64

[<Literal>]
let literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="e0917-185">不允許使用其他位元運算子。</span><span class="sxs-lookup"><span data-stu-id="e0917-185">The use of other bitwise operators isn't allowed.</span></span>

## <a name="named-literals"></a><span data-ttu-id="e0917-186">具名常值</span><span class="sxs-lookup"><span data-stu-id="e0917-186">Named Literals</span></span>

<span data-ttu-id="e0917-187">預定要當做常數的值都可以使用標記[常值](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)屬性。</span><span class="sxs-lookup"><span data-stu-id="e0917-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="e0917-188">此屬性會有效果會使要編譯成常數的值。</span><span class="sxs-lookup"><span data-stu-id="e0917-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="e0917-189">在模式比對運算式，開頭為小寫字元的識別碼都被視為變數繫結，而非做為常值，因此您通常應該使用第一個字母大寫定義常值。</span><span class="sxs-lookup"><span data-stu-id="e0917-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="e0917-190">在其他基底的整數</span><span class="sxs-lookup"><span data-stu-id="e0917-190">Integers In Other Bases</span></span>

<span data-ttu-id="e0917-191">帶正負號的 32 位元整數也 zadat 中使用十六進位、 八進位或二進位`0x`，`0o`或`0b`分別的前置詞。</span><span class="sxs-lookup"><span data-stu-id="e0917-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="e0917-192">數值常值中的底線</span><span class="sxs-lookup"><span data-stu-id="e0917-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="e0917-193">開頭為F#4.1，您可以使用底線字元來分隔數字 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="e0917-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="e0917-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0917-194">See also</span></span>

- [<span data-ttu-id="e0917-195">Core.LiteralAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="e0917-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
