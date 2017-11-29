---
title: "常值 (F#)"
description: "深入了解 F # 程式語言中的常值類型。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4b1d6e9d-f933-4cd4-966d-d643152c27e4
ms.openlocfilehash: 6bb1f233b6846e226c4e73aee00b8cf77735fe2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="literals"></a><span data-ttu-id="be44f-104">常值</span><span class="sxs-lookup"><span data-stu-id="be44f-104">Literals</span></span>

> [!NOTE]
<span data-ttu-id="be44f-105">本文章中的應用程式開發介面參考連結將您移至 MSDN （適用於立即）。</span><span class="sxs-lookup"><span data-stu-id="be44f-105">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="be44f-106">本主題提供的資料表將顯示如何在 F # 中指定的常值類型。</span><span class="sxs-lookup"><span data-stu-id="be44f-106">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="be44f-107">常值類型</span><span class="sxs-lookup"><span data-stu-id="be44f-107">Literal Types</span></span>
<span data-ttu-id="be44f-108">下表顯示 F # 中的常值類型。</span><span class="sxs-lookup"><span data-stu-id="be44f-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="be44f-109">表示數字的十六進位表示法的字元不區分大小寫。識別類型的字元會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="be44f-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="be44f-110">類型</span><span class="sxs-lookup"><span data-stu-id="be44f-110">Type</span></span>|<span data-ttu-id="be44f-111">描述</span><span class="sxs-lookup"><span data-stu-id="be44f-111">Description</span></span>|<span data-ttu-id="be44f-112">後置字元或前置詞</span><span class="sxs-lookup"><span data-stu-id="be44f-112">Suffix or prefix</span></span>|<span data-ttu-id="be44f-113">範例</span><span class="sxs-lookup"><span data-stu-id="be44f-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="be44f-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="be44f-114">sbyte</span></span>|<span data-ttu-id="be44f-115">8 位元帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="be44f-115">signed 8-bit integer</span></span>|<span data-ttu-id="be44f-116">y</span><span class="sxs-lookup"><span data-stu-id="be44f-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="be44f-117">byte</span><span class="sxs-lookup"><span data-stu-id="be44f-117">byte</span></span>|<span data-ttu-id="be44f-118">不帶正負號的 8 位元自然數字</span><span class="sxs-lookup"><span data-stu-id="be44f-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="be44f-119">uy</span><span class="sxs-lookup"><span data-stu-id="be44f-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="be44f-120">int16</span><span class="sxs-lookup"><span data-stu-id="be44f-120">int16</span></span>|<span data-ttu-id="be44f-121">16 位元帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="be44f-121">signed 16-bit integer</span></span>|<span data-ttu-id="be44f-122">s</span><span class="sxs-lookup"><span data-stu-id="be44f-122">s</span></span>|`86s`|
|<span data-ttu-id="be44f-123">uint16</span><span class="sxs-lookup"><span data-stu-id="be44f-123">uint16</span></span>|<span data-ttu-id="be44f-124">不帶正負號的 16 位元自然數字</span><span class="sxs-lookup"><span data-stu-id="be44f-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="be44f-125">us</span><span class="sxs-lookup"><span data-stu-id="be44f-125">us</span></span>|`86us`|
|<span data-ttu-id="be44f-126">int</span><span class="sxs-lookup"><span data-stu-id="be44f-126">int</span></span><br /><br /><span data-ttu-id="be44f-127">int32</span><span class="sxs-lookup"><span data-stu-id="be44f-127">int32</span></span>|<span data-ttu-id="be44f-128">32 位元帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="be44f-128">signed 32-bit integer</span></span>|<span data-ttu-id="be44f-129">l 或 none</span><span class="sxs-lookup"><span data-stu-id="be44f-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="be44f-130">uint</span><span class="sxs-lookup"><span data-stu-id="be44f-130">uint</span></span><br /><br /><span data-ttu-id="be44f-131">uint32</span><span class="sxs-lookup"><span data-stu-id="be44f-131">uint32</span></span>|<span data-ttu-id="be44f-132">不帶正負號的 32 位元自然數字</span><span class="sxs-lookup"><span data-stu-id="be44f-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="be44f-133">u 或 u l</span><span class="sxs-lookup"><span data-stu-id="be44f-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="be44f-134">unativeint</span><span class="sxs-lookup"><span data-stu-id="be44f-134">unativeint</span></span>|<span data-ttu-id="be44f-135">原生指標做為不帶正負號的自然號碼</span><span class="sxs-lookup"><span data-stu-id="be44f-135">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="be44f-136">取消</span><span class="sxs-lookup"><span data-stu-id="be44f-136">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="be44f-137">int64</span><span class="sxs-lookup"><span data-stu-id="be44f-137">int64</span></span>|<span data-ttu-id="be44f-138">64 位元帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="be44f-138">signed 64-bit integer</span></span>|<span data-ttu-id="be44f-139">L</span><span class="sxs-lookup"><span data-stu-id="be44f-139">L</span></span>|`86L`|
|<span data-ttu-id="be44f-140">uint64</span><span class="sxs-lookup"><span data-stu-id="be44f-140">uint64</span></span>|<span data-ttu-id="be44f-141">不帶正負號的 64 位元自然數字</span><span class="sxs-lookup"><span data-stu-id="be44f-141">unsigned 64-bit natural number</span></span>|<span data-ttu-id="be44f-142">UL</span><span class="sxs-lookup"><span data-stu-id="be44f-142">UL</span></span>|`86UL`|
|<span data-ttu-id="be44f-143">single、 float32</span><span class="sxs-lookup"><span data-stu-id="be44f-143">single, float32</span></span>|<span data-ttu-id="be44f-144">32 位元浮點數</span><span class="sxs-lookup"><span data-stu-id="be44f-144">32-bit floating point number</span></span>|<span data-ttu-id="be44f-145">F 或 f</span><span class="sxs-lookup"><span data-stu-id="be44f-145">F or f</span></span>|<span data-ttu-id="be44f-146">`4.14F` 或 `4.14f`</span><span class="sxs-lookup"><span data-stu-id="be44f-146">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="be44f-147">lf</span><span class="sxs-lookup"><span data-stu-id="be44f-147">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="be44f-148">浮點數。double</span><span class="sxs-lookup"><span data-stu-id="be44f-148">float; double</span></span>|<span data-ttu-id="be44f-149">64 位元浮點數</span><span class="sxs-lookup"><span data-stu-id="be44f-149">64-bit floating point number</span></span>|<span data-ttu-id="be44f-150">無</span><span class="sxs-lookup"><span data-stu-id="be44f-150">none</span></span>|<span data-ttu-id="be44f-151">`4.14`、`2.3E+32` 或 `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="be44f-151">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="be44f-152">LF</span><span class="sxs-lookup"><span data-stu-id="be44f-152">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="be44f-153">bigint</span><span class="sxs-lookup"><span data-stu-id="be44f-153">bigint</span></span>|<span data-ttu-id="be44f-154">不會限制為 64 位元表示的整數</span><span class="sxs-lookup"><span data-stu-id="be44f-154">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="be44f-155">I</span><span class="sxs-lookup"><span data-stu-id="be44f-155">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="be44f-156">decimal</span><span class="sxs-lookup"><span data-stu-id="be44f-156">decimal</span></span>|<span data-ttu-id="be44f-157">表示為固定的點或合理數的小數數字</span><span class="sxs-lookup"><span data-stu-id="be44f-157">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="be44f-158">M 或 m</span><span class="sxs-lookup"><span data-stu-id="be44f-158">M or m</span></span>|<span data-ttu-id="be44f-159">`0.7833M` 或 `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="be44f-159">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="be44f-160">Char</span><span class="sxs-lookup"><span data-stu-id="be44f-160">Char</span></span>|<span data-ttu-id="be44f-161">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="be44f-161">Unicode character</span></span>|<span data-ttu-id="be44f-162">無</span><span class="sxs-lookup"><span data-stu-id="be44f-162">none</span></span>|`'a'`|
|<span data-ttu-id="be44f-163">字串</span><span class="sxs-lookup"><span data-stu-id="be44f-163">String</span></span>|<span data-ttu-id="be44f-164">Unicode 字串</span><span class="sxs-lookup"><span data-stu-id="be44f-164">Unicode string</span></span>|<span data-ttu-id="be44f-165">無</span><span class="sxs-lookup"><span data-stu-id="be44f-165">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="be44f-166">或</span><span class="sxs-lookup"><span data-stu-id="be44f-166">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="be44f-167">或</span><span class="sxs-lookup"><span data-stu-id="be44f-167">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="be44f-168">或</span><span class="sxs-lookup"><span data-stu-id="be44f-168">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="be44f-169">另請參閱[字串](Strings.md)。</span><span class="sxs-lookup"><span data-stu-id="be44f-169">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="be44f-170">byte</span><span class="sxs-lookup"><span data-stu-id="be44f-170">byte</span></span>|<span data-ttu-id="be44f-171">ASCII 字元</span><span class="sxs-lookup"><span data-stu-id="be44f-171">ASCII character</span></span>|<span data-ttu-id="be44f-172">B</span><span class="sxs-lookup"><span data-stu-id="be44f-172">B</span></span>|`'a'B`|
|<span data-ttu-id="be44f-173">byte[]</span><span class="sxs-lookup"><span data-stu-id="be44f-173">byte[]</span></span>|<span data-ttu-id="be44f-174">ASCII 字串</span><span class="sxs-lookup"><span data-stu-id="be44f-174">ASCII string</span></span>|<span data-ttu-id="be44f-175">B</span><span class="sxs-lookup"><span data-stu-id="be44f-175">B</span></span>|`"text"B`|
|<span data-ttu-id="be44f-176">字串或 byte [</span><span class="sxs-lookup"><span data-stu-id="be44f-176">String or byte[]</span></span>|<span data-ttu-id="be44f-177">逐字字串</span><span class="sxs-lookup"><span data-stu-id="be44f-177">verbatim string</span></span>|<span data-ttu-id="be44f-178">@ 前置詞</span><span class="sxs-lookup"><span data-stu-id="be44f-178">@ prefix</span></span>|<span data-ttu-id="be44f-179">`@"\\server\share"`(Unicode)</span><span class="sxs-lookup"><span data-stu-id="be44f-179">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="be44f-180">`@"\\server\share"B`(ASCII)</span><span class="sxs-lookup"><span data-stu-id="be44f-180">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="be44f-181">備註</span><span class="sxs-lookup"><span data-stu-id="be44f-181">Remarks</span></span>
<span data-ttu-id="be44f-182">Unicode 字串可以包含明確的編碼方式，您可以指定使用`\u`後面跟著 16 位元的十六進位碼或您可以使用指定的 utf-32 編碼`\U`後面接著 32 位元的十六進位代碼，表示為 Unicodesurrogate 字組。</span><span class="sxs-lookup"><span data-stu-id="be44f-182">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="be44f-183">為準，F # 3.1，您可以使用`+`登結合字串常值。</span><span class="sxs-lookup"><span data-stu-id="be44f-183">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="be44f-184">您也可以使用位元或 (`|||`) 運算子來組合列舉旗標。</span><span class="sxs-lookup"><span data-stu-id="be44f-184">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="be44f-185">例如，下列程式碼是在 F # 3.1 中合法的：</span><span class="sxs-lookup"><span data-stu-id="be44f-185">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="be44f-186">不允許其他位元運算子的用法。</span><span class="sxs-lookup"><span data-stu-id="be44f-186">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="be44f-187">具名常值</span><span class="sxs-lookup"><span data-stu-id="be44f-187">Named Literals</span></span>
<span data-ttu-id="be44f-188">要作為 常數的值都可以使用標記[常值](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)屬性。</span><span class="sxs-lookup"><span data-stu-id="be44f-188">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="be44f-189">這個屬性具有造成編譯為常數的值。</span><span class="sxs-lookup"><span data-stu-id="be44f-189">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="be44f-190">在模式比對運算式中，以小寫字母字元開頭的識別項一律視為變數繫結，而不做為常值，所以通常應該使用第一個字母大寫時定義常值。</span><span class="sxs-lookup"><span data-stu-id="be44f-190">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="be44f-191">其他的基底的整數</span><span class="sxs-lookup"><span data-stu-id="be44f-191">Integers In Other Bases</span></span>

<span data-ttu-id="be44f-192">帶正負號的 32 位元整數，也可以指定在使用十六進位、 八進位或二進位`0x`，`0o`或`0b`分別前置詞。</span><span class="sxs-lookup"><span data-stu-id="be44f-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="be44f-193">數值常值中的底線</span><span class="sxs-lookup"><span data-stu-id="be44f-193">Underscores in Numeric Literals</span></span>

<span data-ttu-id="be44f-194">從 F # 4.1 開始，您可以分隔數字與底線字元 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="be44f-194">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="be44f-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be44f-195">See Also</span></span>

[<span data-ttu-id="be44f-196">Core.LiteralAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="be44f-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
