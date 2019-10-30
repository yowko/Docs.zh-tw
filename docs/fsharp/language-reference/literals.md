---
title: 常值
description: 瞭解程式F#設計語言中的常數值型別。
ms.date: 06/28/2019
ms.openlocfilehash: 9792a24ac28eb402e35e78574cd6a2bf9526734d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041036"
---
# <a name="literals"></a><span data-ttu-id="c8df2-103">常值</span><span class="sxs-lookup"><span data-stu-id="c8df2-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="c8df2-104">本文中的 API 參考連結將帶您前往 MSDN （目前為）。</span><span class="sxs-lookup"><span data-stu-id="c8df2-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="c8df2-105">本主題提供的表格說明如何在中F#指定常值的型別。</span><span class="sxs-lookup"><span data-stu-id="c8df2-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="c8df2-106">常數值型別</span><span class="sxs-lookup"><span data-stu-id="c8df2-106">Literal Types</span></span>

<span data-ttu-id="c8df2-107">下表顯示中F#的常數值型別。</span><span class="sxs-lookup"><span data-stu-id="c8df2-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="c8df2-108">代表十六進位標記法中數位的字元不區分大小寫;識別類型的字元會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c8df2-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="c8df2-109">輸入</span><span class="sxs-lookup"><span data-stu-id="c8df2-109">Type</span></span>|<span data-ttu-id="c8df2-110">描述</span><span class="sxs-lookup"><span data-stu-id="c8df2-110">Description</span></span>|<span data-ttu-id="c8df2-111">尾碼或前置詞</span><span class="sxs-lookup"><span data-stu-id="c8df2-111">Suffix or prefix</span></span>|<span data-ttu-id="c8df2-112">範例</span><span class="sxs-lookup"><span data-stu-id="c8df2-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="c8df2-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="c8df2-113">sbyte</span></span>|<span data-ttu-id="c8df2-114">帶正負號的8位整數</span><span class="sxs-lookup"><span data-stu-id="c8df2-114">signed 8-bit integer</span></span>|<span data-ttu-id="c8df2-115">Y</span><span class="sxs-lookup"><span data-stu-id="c8df2-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="c8df2-116">byte</span><span class="sxs-lookup"><span data-stu-id="c8df2-116">byte</span></span>|<span data-ttu-id="c8df2-117">不帶正負號的8位自然數位</span><span class="sxs-lookup"><span data-stu-id="c8df2-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="c8df2-118">uy</span><span class="sxs-lookup"><span data-stu-id="c8df2-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="c8df2-119">int16</span><span class="sxs-lookup"><span data-stu-id="c8df2-119">int16</span></span>|<span data-ttu-id="c8df2-120">帶正負號的16位整數</span><span class="sxs-lookup"><span data-stu-id="c8df2-120">signed 16-bit integer</span></span>|<span data-ttu-id="c8df2-121">秒</span><span class="sxs-lookup"><span data-stu-id="c8df2-121">s</span></span>|`86s`|
|<span data-ttu-id="c8df2-122">uint16</span><span class="sxs-lookup"><span data-stu-id="c8df2-122">uint16</span></span>|<span data-ttu-id="c8df2-123">不帶正負號的16位自然數位</span><span class="sxs-lookup"><span data-stu-id="c8df2-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="c8df2-124">us</span><span class="sxs-lookup"><span data-stu-id="c8df2-124">us</span></span>|`86us`|
|<span data-ttu-id="c8df2-125">int</span><span class="sxs-lookup"><span data-stu-id="c8df2-125">int</span></span><br /><br /><span data-ttu-id="c8df2-126">int32</span><span class="sxs-lookup"><span data-stu-id="c8df2-126">int32</span></span>|<span data-ttu-id="c8df2-127">帶正負號的32位整數</span><span class="sxs-lookup"><span data-stu-id="c8df2-127">signed 32-bit integer</span></span>|<span data-ttu-id="c8df2-128">l 或 none</span><span class="sxs-lookup"><span data-stu-id="c8df2-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="c8df2-129">uint</span><span class="sxs-lookup"><span data-stu-id="c8df2-129">uint</span></span><br /><br /><span data-ttu-id="c8df2-130">uint32</span><span class="sxs-lookup"><span data-stu-id="c8df2-130">uint32</span></span>|<span data-ttu-id="c8df2-131">不帶正負號的32位自然數位</span><span class="sxs-lookup"><span data-stu-id="c8df2-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="c8df2-132">u 或 ul</span><span class="sxs-lookup"><span data-stu-id="c8df2-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="c8df2-133">nativeint</span><span class="sxs-lookup"><span data-stu-id="c8df2-133">nativeint</span></span>|<span data-ttu-id="c8df2-134">帶正負號之自然數位的原生指標</span><span class="sxs-lookup"><span data-stu-id="c8df2-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="c8df2-135">n</span><span class="sxs-lookup"><span data-stu-id="c8df2-135">n</span></span>|`123n`|
|<span data-ttu-id="c8df2-136">unativeint</span><span class="sxs-lookup"><span data-stu-id="c8df2-136">unativeint</span></span>|<span data-ttu-id="c8df2-137">原生指標做為不帶正負號的自然數</span><span class="sxs-lookup"><span data-stu-id="c8df2-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="c8df2-138">取消</span><span class="sxs-lookup"><span data-stu-id="c8df2-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="c8df2-139">int64</span><span class="sxs-lookup"><span data-stu-id="c8df2-139">int64</span></span>|<span data-ttu-id="c8df2-140">帶正負號的64位整數</span><span class="sxs-lookup"><span data-stu-id="c8df2-140">signed 64-bit integer</span></span>|<span data-ttu-id="c8df2-141">L</span><span class="sxs-lookup"><span data-stu-id="c8df2-141">L</span></span>|`86L`|
|<span data-ttu-id="c8df2-142">uint64</span><span class="sxs-lookup"><span data-stu-id="c8df2-142">uint64</span></span>|<span data-ttu-id="c8df2-143">不帶正負號的64位自然數位</span><span class="sxs-lookup"><span data-stu-id="c8df2-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="c8df2-144">UL</span><span class="sxs-lookup"><span data-stu-id="c8df2-144">UL</span></span>|`86UL`|
|<span data-ttu-id="c8df2-145">single、float32</span><span class="sxs-lookup"><span data-stu-id="c8df2-145">single, float32</span></span>|<span data-ttu-id="c8df2-146">32位浮點數字</span><span class="sxs-lookup"><span data-stu-id="c8df2-146">32-bit floating point number</span></span>|<span data-ttu-id="c8df2-147">F 或 f</span><span class="sxs-lookup"><span data-stu-id="c8df2-147">F or f</span></span>|<span data-ttu-id="c8df2-148">`4.14F` 或 `4.14f`</span><span class="sxs-lookup"><span data-stu-id="c8df2-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="c8df2-149">分行符號</span><span class="sxs-lookup"><span data-stu-id="c8df2-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="c8df2-150">float兩</span><span class="sxs-lookup"><span data-stu-id="c8df2-150">float; double</span></span>|<span data-ttu-id="c8df2-151">64位浮點數字</span><span class="sxs-lookup"><span data-stu-id="c8df2-151">64-bit floating point number</span></span>|<span data-ttu-id="c8df2-152">none</span><span class="sxs-lookup"><span data-stu-id="c8df2-152">none</span></span>|<span data-ttu-id="c8df2-153">`4.14`、`2.3E+32` 或 `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="c8df2-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="c8df2-154">分行符號</span><span class="sxs-lookup"><span data-stu-id="c8df2-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="c8df2-155">bigint</span><span class="sxs-lookup"><span data-stu-id="c8df2-155">bigint</span></span>|<span data-ttu-id="c8df2-156">整數不限於64位標記法</span><span class="sxs-lookup"><span data-stu-id="c8df2-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="c8df2-157">I</span><span class="sxs-lookup"><span data-stu-id="c8df2-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="c8df2-158">decimal</span><span class="sxs-lookup"><span data-stu-id="c8df2-158">decimal</span></span>|<span data-ttu-id="c8df2-159">以固定點或有理數表示的小數位數</span><span class="sxs-lookup"><span data-stu-id="c8df2-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="c8df2-160">M 或 m</span><span class="sxs-lookup"><span data-stu-id="c8df2-160">M or m</span></span>|<span data-ttu-id="c8df2-161">`0.7833M` 或 `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="c8df2-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="c8df2-162">Char</span><span class="sxs-lookup"><span data-stu-id="c8df2-162">Char</span></span>|<span data-ttu-id="c8df2-163">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="c8df2-163">Unicode character</span></span>|<span data-ttu-id="c8df2-164">none</span><span class="sxs-lookup"><span data-stu-id="c8df2-164">none</span></span>|<span data-ttu-id="c8df2-165">`'a'` 或 `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="c8df2-165">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="c8df2-166">String</span><span class="sxs-lookup"><span data-stu-id="c8df2-166">String</span></span>|<span data-ttu-id="c8df2-167">Unicode 字串</span><span class="sxs-lookup"><span data-stu-id="c8df2-167">Unicode string</span></span>|<span data-ttu-id="c8df2-168">none</span><span class="sxs-lookup"><span data-stu-id="c8df2-168">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="c8df2-169">或</span><span class="sxs-lookup"><span data-stu-id="c8df2-169">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="c8df2-170">或</span><span class="sxs-lookup"><span data-stu-id="c8df2-170">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="c8df2-171">或</span><span class="sxs-lookup"><span data-stu-id="c8df2-171">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="c8df2-172">另請參閱[字串](Strings.md)。</span><span class="sxs-lookup"><span data-stu-id="c8df2-172">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="c8df2-173">byte</span><span class="sxs-lookup"><span data-stu-id="c8df2-173">byte</span></span>|<span data-ttu-id="c8df2-174">ASCII 字元</span><span class="sxs-lookup"><span data-stu-id="c8df2-174">ASCII character</span></span>|<span data-ttu-id="c8df2-175">B</span><span class="sxs-lookup"><span data-stu-id="c8df2-175">B</span></span>|`'a'B`|
|<span data-ttu-id="c8df2-176">byte[]</span><span class="sxs-lookup"><span data-stu-id="c8df2-176">byte[]</span></span>|<span data-ttu-id="c8df2-177">ASCII 字串</span><span class="sxs-lookup"><span data-stu-id="c8df2-177">ASCII string</span></span>|<span data-ttu-id="c8df2-178">B</span><span class="sxs-lookup"><span data-stu-id="c8df2-178">B</span></span>|`"text"B`|
|<span data-ttu-id="c8df2-179">String 或 byte []</span><span class="sxs-lookup"><span data-stu-id="c8df2-179">String or byte[]</span></span>|<span data-ttu-id="c8df2-180">逐字字串</span><span class="sxs-lookup"><span data-stu-id="c8df2-180">verbatim string</span></span>|<span data-ttu-id="c8df2-181">@ 前置詞</span><span class="sxs-lookup"><span data-stu-id="c8df2-181">@ prefix</span></span>|<span data-ttu-id="c8df2-182">`@"\\server\share"` （Unicode）</span><span class="sxs-lookup"><span data-stu-id="c8df2-182">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="c8df2-183">`@"\\server\share"B` （ASCII）</span><span class="sxs-lookup"><span data-stu-id="c8df2-183">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="c8df2-184">命名的常值</span><span class="sxs-lookup"><span data-stu-id="c8df2-184">Named literals</span></span>

<span data-ttu-id="c8df2-185">要做為常數的值可以使用[Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)屬性來標記。</span><span class="sxs-lookup"><span data-stu-id="c8df2-185">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="c8df2-186">這個屬性具有導致值編譯為常數的效果。</span><span class="sxs-lookup"><span data-stu-id="c8df2-186">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="c8df2-187">在模式比對運算式中，以小寫字元開頭的識別碼一律會被視為要系結的變數，而不是常值，因此當您定義常值時，通常應該使用首字母大寫。</span><span class="sxs-lookup"><span data-stu-id="c8df2-187">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="c8df2-188">備註</span><span class="sxs-lookup"><span data-stu-id="c8df2-188">Remarks</span></span>

<span data-ttu-id="c8df2-189">Unicode 字串可以包含明確的編碼方式，您可以使用 `\u` 後面接著16位的十六進位碼（0000-FFFF），或您可以使用 `\U` 指定的 UTF-32 編碼，再加上代表任何 Unicode 的32位十六進位程式碼程式碼點（00000000-0010FFFF 之間）。</span><span class="sxs-lookup"><span data-stu-id="c8df2-189">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="c8df2-190">不允許使用 `|||` 以外的其他位運算子。</span><span class="sxs-lookup"><span data-stu-id="c8df2-190">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="c8df2-191">其他基底中的整數</span><span class="sxs-lookup"><span data-stu-id="c8df2-191">Integers in other bases</span></span>

<span data-ttu-id="c8df2-192">您也可以使用 `0x`、`0o` 或 `0b` 前置詞，分別指定十六進位、八進位或二進位格式的已簽署32位整數。</span><span class="sxs-lookup"><span data-stu-id="c8df2-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="c8df2-193">數值常值中的底線</span><span class="sxs-lookup"><span data-stu-id="c8df2-193">Underscores in numeric literals</span></span>

<span data-ttu-id="c8df2-194">您可以使用底線字元（`_`）來分隔數位。</span><span class="sxs-lookup"><span data-stu-id="c8df2-194">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="c8df2-195">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8df2-195">See also</span></span>

- [<span data-ttu-id="c8df2-196">LiteralAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="c8df2-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
