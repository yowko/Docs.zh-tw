---
title: 常值
description: '瞭解 F # 程式設計語言中的常數值型別。'
ms.date: 06/28/2019
ms.openlocfilehash: 98d609a1cf0beb00c0dd4d45ea343aaa2280b62e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855019"
---
# <a name="literals"></a><span data-ttu-id="8ee0b-103">常值</span><span class="sxs-lookup"><span data-stu-id="8ee0b-103">Literals</span></span>

<span data-ttu-id="8ee0b-104">本文提供的表格說明如何以 F # 指定常值的型別。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

> [!NOTE]
> <span data-ttu-id="8ee0b-105">F # 的 docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-105">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="8ee0b-106">如果您遇到任何中斷的連結，請改為參考[F # 核心程式庫檔](https://fsharp.github.io/fsharp-core-docs/)。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-106">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="literal-types"></a><span data-ttu-id="8ee0b-107">常值類型</span><span class="sxs-lookup"><span data-stu-id="8ee0b-107">Literal types</span></span>

<span data-ttu-id="8ee0b-108">下表顯示 F # 中的常數值型別。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="8ee0b-109">代表十六進位標記法中數位的字元不區分大小寫;識別類型的字元會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="8ee0b-110">類型</span><span class="sxs-lookup"><span data-stu-id="8ee0b-110">Type</span></span>|<span data-ttu-id="8ee0b-111">描述</span><span class="sxs-lookup"><span data-stu-id="8ee0b-111">Description</span></span>|<span data-ttu-id="8ee0b-112">尾碼或前置詞</span><span class="sxs-lookup"><span data-stu-id="8ee0b-112">Suffix or prefix</span></span>|<span data-ttu-id="8ee0b-113">範例</span><span class="sxs-lookup"><span data-stu-id="8ee0b-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="8ee0b-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="8ee0b-114">sbyte</span></span>|<span data-ttu-id="8ee0b-115">帶正負號的8位整數</span><span class="sxs-lookup"><span data-stu-id="8ee0b-115">signed 8-bit integer</span></span>|<span data-ttu-id="8ee0b-116">y</span><span class="sxs-lookup"><span data-stu-id="8ee0b-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="8ee0b-117">byte</span><span class="sxs-lookup"><span data-stu-id="8ee0b-117">byte</span></span>|<span data-ttu-id="8ee0b-118">不帶正負號的8位自然數位</span><span class="sxs-lookup"><span data-stu-id="8ee0b-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="8ee0b-119">uy</span><span class="sxs-lookup"><span data-stu-id="8ee0b-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="8ee0b-120">int16</span><span class="sxs-lookup"><span data-stu-id="8ee0b-120">int16</span></span>|<span data-ttu-id="8ee0b-121">帶正負號的16位整數</span><span class="sxs-lookup"><span data-stu-id="8ee0b-121">signed 16-bit integer</span></span>|<span data-ttu-id="8ee0b-122">s</span><span class="sxs-lookup"><span data-stu-id="8ee0b-122">s</span></span>|`86s`|
|<span data-ttu-id="8ee0b-123">uint16</span><span class="sxs-lookup"><span data-stu-id="8ee0b-123">uint16</span></span>|<span data-ttu-id="8ee0b-124">不帶正負號的16位自然數位</span><span class="sxs-lookup"><span data-stu-id="8ee0b-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="8ee0b-125">us</span><span class="sxs-lookup"><span data-stu-id="8ee0b-125">us</span></span>|`86us`|
|<span data-ttu-id="8ee0b-126">int</span><span class="sxs-lookup"><span data-stu-id="8ee0b-126">int</span></span><br /><br /><span data-ttu-id="8ee0b-127">int32</span><span class="sxs-lookup"><span data-stu-id="8ee0b-127">int32</span></span>|<span data-ttu-id="8ee0b-128">帶正負號的32位整數</span><span class="sxs-lookup"><span data-stu-id="8ee0b-128">signed 32-bit integer</span></span>|<span data-ttu-id="8ee0b-129">l 或 none</span><span class="sxs-lookup"><span data-stu-id="8ee0b-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="8ee0b-130">uint</span><span class="sxs-lookup"><span data-stu-id="8ee0b-130">uint</span></span><br /><br /><span data-ttu-id="8ee0b-131">uint32</span><span class="sxs-lookup"><span data-stu-id="8ee0b-131">uint32</span></span>|<span data-ttu-id="8ee0b-132">不帶正負號的32位自然數位</span><span class="sxs-lookup"><span data-stu-id="8ee0b-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="8ee0b-133">u 或 ul</span><span class="sxs-lookup"><span data-stu-id="8ee0b-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="8ee0b-134">nativeint</span><span class="sxs-lookup"><span data-stu-id="8ee0b-134">nativeint</span></span>|<span data-ttu-id="8ee0b-135">帶正負號之自然數位的原生指標</span><span class="sxs-lookup"><span data-stu-id="8ee0b-135">native pointer to a signed natural number</span></span>|<span data-ttu-id="8ee0b-136">n</span><span class="sxs-lookup"><span data-stu-id="8ee0b-136">n</span></span>|`123n`|
|<span data-ttu-id="8ee0b-137">unativeint</span><span class="sxs-lookup"><span data-stu-id="8ee0b-137">unativeint</span></span>|<span data-ttu-id="8ee0b-138">原生指標做為不帶正負號的自然數</span><span class="sxs-lookup"><span data-stu-id="8ee0b-138">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="8ee0b-139">取消</span><span class="sxs-lookup"><span data-stu-id="8ee0b-139">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="8ee0b-140">int64</span><span class="sxs-lookup"><span data-stu-id="8ee0b-140">int64</span></span>|<span data-ttu-id="8ee0b-141">帶正負號的64位整數</span><span class="sxs-lookup"><span data-stu-id="8ee0b-141">signed 64-bit integer</span></span>|<span data-ttu-id="8ee0b-142">L</span><span class="sxs-lookup"><span data-stu-id="8ee0b-142">L</span></span>|`86L`|
|<span data-ttu-id="8ee0b-143">uint64</span><span class="sxs-lookup"><span data-stu-id="8ee0b-143">uint64</span></span>|<span data-ttu-id="8ee0b-144">不帶正負號的64位自然數位</span><span class="sxs-lookup"><span data-stu-id="8ee0b-144">unsigned 64-bit natural number</span></span>|<span data-ttu-id="8ee0b-145">UL</span><span class="sxs-lookup"><span data-stu-id="8ee0b-145">UL</span></span>|`86UL`|
|<span data-ttu-id="8ee0b-146">single、float32</span><span class="sxs-lookup"><span data-stu-id="8ee0b-146">single, float32</span></span>|<span data-ttu-id="8ee0b-147">32位浮點數字</span><span class="sxs-lookup"><span data-stu-id="8ee0b-147">32-bit floating point number</span></span>|<span data-ttu-id="8ee0b-148">F 或 f</span><span class="sxs-lookup"><span data-stu-id="8ee0b-148">F or f</span></span>|<span data-ttu-id="8ee0b-149">`4.14F` 或 `4.14f`</span><span class="sxs-lookup"><span data-stu-id="8ee0b-149">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="8ee0b-150">分行符號</span><span class="sxs-lookup"><span data-stu-id="8ee0b-150">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="8ee0b-151">float兩</span><span class="sxs-lookup"><span data-stu-id="8ee0b-151">float; double</span></span>|<span data-ttu-id="8ee0b-152">64位浮點數字</span><span class="sxs-lookup"><span data-stu-id="8ee0b-152">64-bit floating point number</span></span>|<span data-ttu-id="8ee0b-153">無</span><span class="sxs-lookup"><span data-stu-id="8ee0b-153">none</span></span>|<span data-ttu-id="8ee0b-154">`4.14`、`2.3E+32` 或 `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="8ee0b-154">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="8ee0b-155">分行符號</span><span class="sxs-lookup"><span data-stu-id="8ee0b-155">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="8ee0b-156">BIGINT</span><span class="sxs-lookup"><span data-stu-id="8ee0b-156">bigint</span></span>|<span data-ttu-id="8ee0b-157">整數不限於64位標記法</span><span class="sxs-lookup"><span data-stu-id="8ee0b-157">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="8ee0b-158">I</span><span class="sxs-lookup"><span data-stu-id="8ee0b-158">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="8ee0b-159">decimal</span><span class="sxs-lookup"><span data-stu-id="8ee0b-159">decimal</span></span>|<span data-ttu-id="8ee0b-160">以固定點或有理數表示的小數位數</span><span class="sxs-lookup"><span data-stu-id="8ee0b-160">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="8ee0b-161">M 或 m</span><span class="sxs-lookup"><span data-stu-id="8ee0b-161">M or m</span></span>|<span data-ttu-id="8ee0b-162">`0.7833M` 或 `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="8ee0b-162">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="8ee0b-163">Char</span><span class="sxs-lookup"><span data-stu-id="8ee0b-163">Char</span></span>|<span data-ttu-id="8ee0b-164">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="8ee0b-164">Unicode character</span></span>|<span data-ttu-id="8ee0b-165">無</span><span class="sxs-lookup"><span data-stu-id="8ee0b-165">none</span></span>|<span data-ttu-id="8ee0b-166">`'a'` 或 `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="8ee0b-166">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="8ee0b-167">String</span><span class="sxs-lookup"><span data-stu-id="8ee0b-167">String</span></span>|<span data-ttu-id="8ee0b-168">Unicode 字串</span><span class="sxs-lookup"><span data-stu-id="8ee0b-168">Unicode string</span></span>|<span data-ttu-id="8ee0b-169">無</span><span class="sxs-lookup"><span data-stu-id="8ee0b-169">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="8ee0b-170">或</span><span class="sxs-lookup"><span data-stu-id="8ee0b-170">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="8ee0b-171">或</span><span class="sxs-lookup"><span data-stu-id="8ee0b-171">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="8ee0b-172">或</span><span class="sxs-lookup"><span data-stu-id="8ee0b-172">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="8ee0b-173">另請參閱[字串](Strings.md)。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-173">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="8ee0b-174">byte</span><span class="sxs-lookup"><span data-stu-id="8ee0b-174">byte</span></span>|<span data-ttu-id="8ee0b-175">ASCII 字元</span><span class="sxs-lookup"><span data-stu-id="8ee0b-175">ASCII character</span></span>|<span data-ttu-id="8ee0b-176">B</span><span class="sxs-lookup"><span data-stu-id="8ee0b-176">B</span></span>|`'a'B`|
|<span data-ttu-id="8ee0b-177">byte[]</span><span class="sxs-lookup"><span data-stu-id="8ee0b-177">byte[]</span></span>|<span data-ttu-id="8ee0b-178">ASCII 字串</span><span class="sxs-lookup"><span data-stu-id="8ee0b-178">ASCII string</span></span>|<span data-ttu-id="8ee0b-179">B</span><span class="sxs-lookup"><span data-stu-id="8ee0b-179">B</span></span>|`"text"B`|
|<span data-ttu-id="8ee0b-180">String 或 byte []</span><span class="sxs-lookup"><span data-stu-id="8ee0b-180">String or byte[]</span></span>|<span data-ttu-id="8ee0b-181">逐字字串</span><span class="sxs-lookup"><span data-stu-id="8ee0b-181">verbatim string</span></span>|<span data-ttu-id="8ee0b-182">@ 前置詞</span><span class="sxs-lookup"><span data-stu-id="8ee0b-182">@ prefix</span></span>|<span data-ttu-id="8ee0b-183">`@"\\server\share"` (Unicode) </span><span class="sxs-lookup"><span data-stu-id="8ee0b-183">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="8ee0b-184">`@"\\server\share"B` (ASCII) </span><span class="sxs-lookup"><span data-stu-id="8ee0b-184">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="8ee0b-185">命名的常值</span><span class="sxs-lookup"><span data-stu-id="8ee0b-185">Named literals</span></span>

<span data-ttu-id="8ee0b-186">要做為常數的值可以使用[Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)屬性來標記。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-186">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="8ee0b-187">這個屬性具有導致值編譯為常數的效果。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-187">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="8ee0b-188">在模式比對運算式中，以小寫字元開頭的識別碼一律會被視為要系結的變數，而不是常值，因此當您定義常值時，通常應該使用首字母大寫。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-188">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="8ee0b-189">備註</span><span class="sxs-lookup"><span data-stu-id="8ee0b-189">Remarks</span></span>

<span data-ttu-id="8ee0b-190">Unicode 字串可以包含明確的編碼方式，您可以使用 `\u` 後面接著16位的十六進位程式碼， (0000-FFFF) ，或您可以使用來指定的 UTF-32 編碼，再加上 `\U` 代表任何 Unicode 程式碼點 (00000000-0010ffff 之間) 的32位十六進位碼。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-190">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="8ee0b-191">不允許使用以外的其他位運算子 `|||` 。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-191">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="8ee0b-192">其他基底中的整數</span><span class="sxs-lookup"><span data-stu-id="8ee0b-192">Integers in other bases</span></span>

<span data-ttu-id="8ee0b-193">您也可以使用 `0x` 、或前置詞，分別在十六進位、八進位或二進位中指定已簽署的32位整數 `0o` `0b` 。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-193">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="8ee0b-194">數值常值中的底線</span><span class="sxs-lookup"><span data-stu-id="8ee0b-194">Underscores in numeric literals</span></span>

<span data-ttu-id="8ee0b-195">您可以使用 () 的底線字元來分隔數位 `_` 。</span><span class="sxs-lookup"><span data-stu-id="8ee0b-195">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="8ee0b-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ee0b-196">See also</span></span>

- [<span data-ttu-id="8ee0b-197">LiteralAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="8ee0b-197">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
