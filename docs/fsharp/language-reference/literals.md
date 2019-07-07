---
title: 常值
description: 深入了解中的常值型別F#程式設計語言。
ms.date: 06/28/2019
ms.openlocfilehash: 0c9ced0b505817a161ca39c6c9f853f94cedf410
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610147"
---
# <a name="literals"></a><span data-ttu-id="a3116-103">常值</span><span class="sxs-lookup"><span data-stu-id="a3116-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="a3116-104">這篇文章中的 API 參考連結將帶您前往 MSDN （適用於目前）。</span><span class="sxs-lookup"><span data-stu-id="a3116-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="a3116-105">本主題提供示範如何指定類型的常值中的資料表F#。</span><span class="sxs-lookup"><span data-stu-id="a3116-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="a3116-106">常值類型</span><span class="sxs-lookup"><span data-stu-id="a3116-106">Literal Types</span></span>

<span data-ttu-id="a3116-107">下表顯示中的常值型別F#。</span><span class="sxs-lookup"><span data-stu-id="a3116-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="a3116-108">表示之數字的十六進位表示法的字元不區分大小寫，識別類型的字元會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a3116-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="a3116-109">類型</span><span class="sxs-lookup"><span data-stu-id="a3116-109">Type</span></span>|<span data-ttu-id="a3116-110">描述</span><span class="sxs-lookup"><span data-stu-id="a3116-110">Description</span></span>|<span data-ttu-id="a3116-111">後置字元或前置詞</span><span class="sxs-lookup"><span data-stu-id="a3116-111">Suffix or prefix</span></span>|<span data-ttu-id="a3116-112">範例</span><span class="sxs-lookup"><span data-stu-id="a3116-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="a3116-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="a3116-113">sbyte</span></span>|<span data-ttu-id="a3116-114">帶正負號的 8 位元整數</span><span class="sxs-lookup"><span data-stu-id="a3116-114">signed 8-bit integer</span></span>|<span data-ttu-id="a3116-115">y</span><span class="sxs-lookup"><span data-stu-id="a3116-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="a3116-116">byte</span><span class="sxs-lookup"><span data-stu-id="a3116-116">byte</span></span>|<span data-ttu-id="a3116-117">不帶正負號的 8 位元自然數</span><span class="sxs-lookup"><span data-stu-id="a3116-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="a3116-118">uy</span><span class="sxs-lookup"><span data-stu-id="a3116-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="a3116-119">int16</span><span class="sxs-lookup"><span data-stu-id="a3116-119">int16</span></span>|<span data-ttu-id="a3116-120">帶正負號的 16 位元整數</span><span class="sxs-lookup"><span data-stu-id="a3116-120">signed 16-bit integer</span></span>|<span data-ttu-id="a3116-121">秒</span><span class="sxs-lookup"><span data-stu-id="a3116-121">s</span></span>|`86s`|
|<span data-ttu-id="a3116-122">uint16</span><span class="sxs-lookup"><span data-stu-id="a3116-122">uint16</span></span>|<span data-ttu-id="a3116-123">不帶正負號的 16 位元自然數</span><span class="sxs-lookup"><span data-stu-id="a3116-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="a3116-124">us</span><span class="sxs-lookup"><span data-stu-id="a3116-124">us</span></span>|`86us`|
|<span data-ttu-id="a3116-125">int</span><span class="sxs-lookup"><span data-stu-id="a3116-125">int</span></span><br /><br /><span data-ttu-id="a3116-126">int32</span><span class="sxs-lookup"><span data-stu-id="a3116-126">int32</span></span>|<span data-ttu-id="a3116-127">帶正負號的 32 位元整數</span><span class="sxs-lookup"><span data-stu-id="a3116-127">signed 32-bit integer</span></span>|<span data-ttu-id="a3116-128">l 或 none</span><span class="sxs-lookup"><span data-stu-id="a3116-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="a3116-129">uint</span><span class="sxs-lookup"><span data-stu-id="a3116-129">uint</span></span><br /><br /><span data-ttu-id="a3116-130">uint32</span><span class="sxs-lookup"><span data-stu-id="a3116-130">uint32</span></span>|<span data-ttu-id="a3116-131">不帶正負號的 32 位元自然數</span><span class="sxs-lookup"><span data-stu-id="a3116-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="a3116-132">u 或 ul</span><span class="sxs-lookup"><span data-stu-id="a3116-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="a3116-133">nativeint</span><span class="sxs-lookup"><span data-stu-id="a3116-133">nativeint</span></span>|<span data-ttu-id="a3116-134">帶正負號自然數的原生指標</span><span class="sxs-lookup"><span data-stu-id="a3116-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="a3116-135">n</span><span class="sxs-lookup"><span data-stu-id="a3116-135">n</span></span>|`123n`|
|<span data-ttu-id="a3116-136">unativeint</span><span class="sxs-lookup"><span data-stu-id="a3116-136">unativeint</span></span>|<span data-ttu-id="a3116-137">為不帶正負號自然數的原生指標</span><span class="sxs-lookup"><span data-stu-id="a3116-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="a3116-138">取消</span><span class="sxs-lookup"><span data-stu-id="a3116-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="a3116-139">int64</span><span class="sxs-lookup"><span data-stu-id="a3116-139">int64</span></span>|<span data-ttu-id="a3116-140">帶正負號的 64 位元整數</span><span class="sxs-lookup"><span data-stu-id="a3116-140">signed 64-bit integer</span></span>|<span data-ttu-id="a3116-141">L</span><span class="sxs-lookup"><span data-stu-id="a3116-141">L</span></span>|`86L`|
|<span data-ttu-id="a3116-142">uint64</span><span class="sxs-lookup"><span data-stu-id="a3116-142">uint64</span></span>|<span data-ttu-id="a3116-143">不帶正負號的 64 位元自然數</span><span class="sxs-lookup"><span data-stu-id="a3116-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="a3116-144">UL</span><span class="sxs-lookup"><span data-stu-id="a3116-144">UL</span></span>|`86UL`|
|<span data-ttu-id="a3116-145">single、float32</span><span class="sxs-lookup"><span data-stu-id="a3116-145">single, float32</span></span>|<span data-ttu-id="a3116-146">32 位元浮點數</span><span class="sxs-lookup"><span data-stu-id="a3116-146">32-bit floating point number</span></span>|<span data-ttu-id="a3116-147">F 或 f</span><span class="sxs-lookup"><span data-stu-id="a3116-147">F or f</span></span>|<span data-ttu-id="a3116-148">`4.14F` 或 `4.14f`</span><span class="sxs-lookup"><span data-stu-id="a3116-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="a3116-149">lf</span><span class="sxs-lookup"><span data-stu-id="a3116-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="a3116-150">浮點數;double</span><span class="sxs-lookup"><span data-stu-id="a3116-150">float; double</span></span>|<span data-ttu-id="a3116-151">64 位元浮點數</span><span class="sxs-lookup"><span data-stu-id="a3116-151">64-bit floating point number</span></span>|<span data-ttu-id="a3116-152">none</span><span class="sxs-lookup"><span data-stu-id="a3116-152">none</span></span>|<span data-ttu-id="a3116-153">`4.14` 或 `2.3E+32` 或 `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="a3116-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="a3116-154">LF</span><span class="sxs-lookup"><span data-stu-id="a3116-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="a3116-155">bigint</span><span class="sxs-lookup"><span data-stu-id="a3116-155">bigint</span></span>|<span data-ttu-id="a3116-156">不限於 64 位元表示的整數</span><span class="sxs-lookup"><span data-stu-id="a3116-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="a3116-157">I</span><span class="sxs-lookup"><span data-stu-id="a3116-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="a3116-158">decimal</span><span class="sxs-lookup"><span data-stu-id="a3116-158">decimal</span></span>|<span data-ttu-id="a3116-159">以固定點或有理數表示的小數數字</span><span class="sxs-lookup"><span data-stu-id="a3116-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="a3116-160">M 或 m</span><span class="sxs-lookup"><span data-stu-id="a3116-160">M or m</span></span>|<span data-ttu-id="a3116-161">`0.7833M` 或 `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="a3116-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="a3116-162">Char</span><span class="sxs-lookup"><span data-stu-id="a3116-162">Char</span></span>|<span data-ttu-id="a3116-163">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="a3116-163">Unicode character</span></span>|<span data-ttu-id="a3116-164">none</span><span class="sxs-lookup"><span data-stu-id="a3116-164">none</span></span>|`'a'`|
|<span data-ttu-id="a3116-165">String</span><span class="sxs-lookup"><span data-stu-id="a3116-165">String</span></span>|<span data-ttu-id="a3116-166">Unicode 字串</span><span class="sxs-lookup"><span data-stu-id="a3116-166">Unicode string</span></span>|<span data-ttu-id="a3116-167">none</span><span class="sxs-lookup"><span data-stu-id="a3116-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="a3116-168">或</span><span class="sxs-lookup"><span data-stu-id="a3116-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="a3116-169">或</span><span class="sxs-lookup"><span data-stu-id="a3116-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="a3116-170">或</span><span class="sxs-lookup"><span data-stu-id="a3116-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="a3116-171">另請參閱[字串](Strings.md)。</span><span class="sxs-lookup"><span data-stu-id="a3116-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="a3116-172">byte</span><span class="sxs-lookup"><span data-stu-id="a3116-172">byte</span></span>|<span data-ttu-id="a3116-173">ASCII 字元</span><span class="sxs-lookup"><span data-stu-id="a3116-173">ASCII character</span></span>|<span data-ttu-id="a3116-174">B</span><span class="sxs-lookup"><span data-stu-id="a3116-174">B</span></span>|`'a'B`|
|<span data-ttu-id="a3116-175">byte[]</span><span class="sxs-lookup"><span data-stu-id="a3116-175">byte[]</span></span>|<span data-ttu-id="a3116-176">ASCII 字串</span><span class="sxs-lookup"><span data-stu-id="a3116-176">ASCII string</span></span>|<span data-ttu-id="a3116-177">B</span><span class="sxs-lookup"><span data-stu-id="a3116-177">B</span></span>|`"text"B`|
|<span data-ttu-id="a3116-178">字串或 byte]</span><span class="sxs-lookup"><span data-stu-id="a3116-178">String or byte[]</span></span>|<span data-ttu-id="a3116-179">逐字字串</span><span class="sxs-lookup"><span data-stu-id="a3116-179">verbatim string</span></span>|<span data-ttu-id="a3116-180">@ prefix</span><span class="sxs-lookup"><span data-stu-id="a3116-180">@ prefix</span></span>|<span data-ttu-id="a3116-181">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="a3116-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="a3116-182">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="a3116-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="a3116-183">具名常值</span><span class="sxs-lookup"><span data-stu-id="a3116-183">Named literals</span></span>

<span data-ttu-id="a3116-184">預定要當做常數的值都可以使用標記[常值](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)屬性。</span><span class="sxs-lookup"><span data-stu-id="a3116-184">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="a3116-185">此屬性會有效果會使要編譯成常數的值。</span><span class="sxs-lookup"><span data-stu-id="a3116-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="a3116-186">在模式比對運算式，開頭為小寫字元的識別碼都被視為變數繫結，而非做為常值，因此您通常應該使用第一個字母大寫定義常值。</span><span class="sxs-lookup"><span data-stu-id="a3116-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a><span data-ttu-id="a3116-187">備註</span><span class="sxs-lookup"><span data-stu-id="a3116-187">Remarks</span></span>

<span data-ttu-id="a3116-188">Unicode 字串可以包含您可以使用指定的明確編碼`\u`後面的 16 位元十六進位字碼 (0000-FFFF) 或您可以使用指定的 UTF-32 編碼`\U`後面接著 32 位元的十六進位代碼，表示任何 Unicode 字碼指標 (00000000-0010FFFF)。</span><span class="sxs-lookup"><span data-stu-id="a3116-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="a3116-189">其他位元運算子，而不使用`|||`不允許。</span><span class="sxs-lookup"><span data-stu-id="a3116-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="a3116-190">在其他基底的整數</span><span class="sxs-lookup"><span data-stu-id="a3116-190">Integers in other bases</span></span>

<span data-ttu-id="a3116-191">帶正負號的 32 位元整數也 zadat 中使用十六進位、 八進位或二進位`0x`，`0o`或`0b`分別的前置詞。</span><span class="sxs-lookup"><span data-stu-id="a3116-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="a3116-192">數值常值中的底線</span><span class="sxs-lookup"><span data-stu-id="a3116-192">Underscores in numeric literals</span></span>

<span data-ttu-id="a3116-193">您可以使用底線字元來分隔數字 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="a3116-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="a3116-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3116-194">See also</span></span>

- [<span data-ttu-id="a3116-195">Core.LiteralAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="a3116-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
