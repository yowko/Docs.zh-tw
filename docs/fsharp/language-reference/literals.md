---
title: 常值
description: '瞭解 F # 程式設計語言中的常數值型別。'
ms.date: 08/15/2020
ms.openlocfilehash: 15f73db3c36f7c60ab1eeba96c63a28ebc6d7f01
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559150"
---
# <a name="literals"></a><span data-ttu-id="316e0-103">常值</span><span class="sxs-lookup"><span data-stu-id="316e0-103">Literals</span></span>

<span data-ttu-id="316e0-104">本文提供的表格顯示如何以 F # 指定常值的類型。</span><span class="sxs-lookup"><span data-stu-id="316e0-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="316e0-105">常值類型</span><span class="sxs-lookup"><span data-stu-id="316e0-105">Literal types</span></span>

<span data-ttu-id="316e0-106">下表顯示 F # 中的常數值型別。</span><span class="sxs-lookup"><span data-stu-id="316e0-106">The following table shows the literal types in F#.</span></span> <span data-ttu-id="316e0-107">以十六進位標記法表示數位的字元不區分大小寫;識別類型的字元會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="316e0-107">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="316e0-108">類型</span><span class="sxs-lookup"><span data-stu-id="316e0-108">Type</span></span>|<span data-ttu-id="316e0-109">描述</span><span class="sxs-lookup"><span data-stu-id="316e0-109">Description</span></span>|<span data-ttu-id="316e0-110">尾碼或前置詞</span><span class="sxs-lookup"><span data-stu-id="316e0-110">Suffix or prefix</span></span>|<span data-ttu-id="316e0-111">範例</span><span class="sxs-lookup"><span data-stu-id="316e0-111">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="316e0-112">sbyte</span><span class="sxs-lookup"><span data-stu-id="316e0-112">sbyte</span></span>|<span data-ttu-id="316e0-113">帶正負號的8位整數</span><span class="sxs-lookup"><span data-stu-id="316e0-113">signed 8-bit integer</span></span>|<span data-ttu-id="316e0-114">y</span><span class="sxs-lookup"><span data-stu-id="316e0-114">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="316e0-115">byte</span><span class="sxs-lookup"><span data-stu-id="316e0-115">byte</span></span>|<span data-ttu-id="316e0-116">不帶正負號的8位自然數位</span><span class="sxs-lookup"><span data-stu-id="316e0-116">unsigned 8-bit natural number</span></span>|<span data-ttu-id="316e0-117">uy</span><span class="sxs-lookup"><span data-stu-id="316e0-117">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="316e0-118">int16</span><span class="sxs-lookup"><span data-stu-id="316e0-118">int16</span></span>|<span data-ttu-id="316e0-119">帶正負號的16位整數</span><span class="sxs-lookup"><span data-stu-id="316e0-119">signed 16-bit integer</span></span>|<span data-ttu-id="316e0-120">s</span><span class="sxs-lookup"><span data-stu-id="316e0-120">s</span></span>|`86s`|
|<span data-ttu-id="316e0-121">uint16</span><span class="sxs-lookup"><span data-stu-id="316e0-121">uint16</span></span>|<span data-ttu-id="316e0-122">不帶正負號的16位自然數位</span><span class="sxs-lookup"><span data-stu-id="316e0-122">unsigned 16-bit natural number</span></span>|<span data-ttu-id="316e0-123">us</span><span class="sxs-lookup"><span data-stu-id="316e0-123">us</span></span>|`86us`|
|<span data-ttu-id="316e0-124">int</span><span class="sxs-lookup"><span data-stu-id="316e0-124">int</span></span><br /><br /><span data-ttu-id="316e0-125">int32</span><span class="sxs-lookup"><span data-stu-id="316e0-125">int32</span></span>|<span data-ttu-id="316e0-126">帶正負號的32位整數</span><span class="sxs-lookup"><span data-stu-id="316e0-126">signed 32-bit integer</span></span>|<span data-ttu-id="316e0-127">l 或 none</span><span class="sxs-lookup"><span data-stu-id="316e0-127">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="316e0-128">uint</span><span class="sxs-lookup"><span data-stu-id="316e0-128">uint</span></span><br /><br /><span data-ttu-id="316e0-129">uint32</span><span class="sxs-lookup"><span data-stu-id="316e0-129">uint32</span></span>|<span data-ttu-id="316e0-130">不帶正負號的32位自然數位</span><span class="sxs-lookup"><span data-stu-id="316e0-130">unsigned 32-bit natural number</span></span>|<span data-ttu-id="316e0-131">u 或 ul</span><span class="sxs-lookup"><span data-stu-id="316e0-131">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="316e0-132">nativeint</span><span class="sxs-lookup"><span data-stu-id="316e0-132">nativeint</span></span>|<span data-ttu-id="316e0-133">帶正負號之自然數的原生指標</span><span class="sxs-lookup"><span data-stu-id="316e0-133">native pointer to a signed natural number</span></span>|<span data-ttu-id="316e0-134">n</span><span class="sxs-lookup"><span data-stu-id="316e0-134">n</span></span>|`123n`|
|<span data-ttu-id="316e0-135">unativeint</span><span class="sxs-lookup"><span data-stu-id="316e0-135">unativeint</span></span>|<span data-ttu-id="316e0-136">原生指標做為不帶正負號的自然數位</span><span class="sxs-lookup"><span data-stu-id="316e0-136">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="316e0-137">聯合國</span><span class="sxs-lookup"><span data-stu-id="316e0-137">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="316e0-138">int64</span><span class="sxs-lookup"><span data-stu-id="316e0-138">int64</span></span>|<span data-ttu-id="316e0-139">帶正負號的64位整數</span><span class="sxs-lookup"><span data-stu-id="316e0-139">signed 64-bit integer</span></span>|<span data-ttu-id="316e0-140">L</span><span class="sxs-lookup"><span data-stu-id="316e0-140">L</span></span>|`86L`|
|<span data-ttu-id="316e0-141">uint64</span><span class="sxs-lookup"><span data-stu-id="316e0-141">uint64</span></span>|<span data-ttu-id="316e0-142">不帶正負號的64位自然數位</span><span class="sxs-lookup"><span data-stu-id="316e0-142">unsigned 64-bit natural number</span></span>|<span data-ttu-id="316e0-143">UL</span><span class="sxs-lookup"><span data-stu-id="316e0-143">UL</span></span>|`86UL`|
|<span data-ttu-id="316e0-144">single、float32</span><span class="sxs-lookup"><span data-stu-id="316e0-144">single, float32</span></span>|<span data-ttu-id="316e0-145">32位浮點數</span><span class="sxs-lookup"><span data-stu-id="316e0-145">32-bit floating point number</span></span>|<span data-ttu-id="316e0-146">F 或 f</span><span class="sxs-lookup"><span data-stu-id="316e0-146">F or f</span></span>|<span data-ttu-id="316e0-147">`4.14F` 或 `4.14f`</span><span class="sxs-lookup"><span data-stu-id="316e0-147">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="316e0-148">如果</span><span class="sxs-lookup"><span data-stu-id="316e0-148">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="316e0-149">浮點雙</span><span class="sxs-lookup"><span data-stu-id="316e0-149">float; double</span></span>|<span data-ttu-id="316e0-150">64位浮點數</span><span class="sxs-lookup"><span data-stu-id="316e0-150">64-bit floating point number</span></span>|<span data-ttu-id="316e0-151">無</span><span class="sxs-lookup"><span data-stu-id="316e0-151">none</span></span>|<span data-ttu-id="316e0-152">`4.14`、`2.3E+32` 或 `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="316e0-152">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="316e0-153">如果</span><span class="sxs-lookup"><span data-stu-id="316e0-153">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="316e0-154">BIGINT</span><span class="sxs-lookup"><span data-stu-id="316e0-154">bigint</span></span>|<span data-ttu-id="316e0-155">整數，不限於64位標記法</span><span class="sxs-lookup"><span data-stu-id="316e0-155">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="316e0-156">I</span><span class="sxs-lookup"><span data-stu-id="316e0-156">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="316e0-157">decimal</span><span class="sxs-lookup"><span data-stu-id="316e0-157">decimal</span></span>|<span data-ttu-id="316e0-158">以固定點或有理數表示的小數位數</span><span class="sxs-lookup"><span data-stu-id="316e0-158">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="316e0-159">M 或 m</span><span class="sxs-lookup"><span data-stu-id="316e0-159">M or m</span></span>|<span data-ttu-id="316e0-160">`0.7833M` 或 `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="316e0-160">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="316e0-161">Char</span><span class="sxs-lookup"><span data-stu-id="316e0-161">Char</span></span>|<span data-ttu-id="316e0-162">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="316e0-162">Unicode character</span></span>|<span data-ttu-id="316e0-163">無</span><span class="sxs-lookup"><span data-stu-id="316e0-163">none</span></span>|<span data-ttu-id="316e0-164">`'a'` 或 `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="316e0-164">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="316e0-165">String</span><span class="sxs-lookup"><span data-stu-id="316e0-165">String</span></span>|<span data-ttu-id="316e0-166">Unicode 字串</span><span class="sxs-lookup"><span data-stu-id="316e0-166">Unicode string</span></span>|<span data-ttu-id="316e0-167">無</span><span class="sxs-lookup"><span data-stu-id="316e0-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="316e0-168">或</span><span class="sxs-lookup"><span data-stu-id="316e0-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="316e0-169">或</span><span class="sxs-lookup"><span data-stu-id="316e0-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="316e0-170">或</span><span class="sxs-lookup"><span data-stu-id="316e0-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="316e0-171">另請參閱 [字串](Strings.md)。</span><span class="sxs-lookup"><span data-stu-id="316e0-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="316e0-172">byte</span><span class="sxs-lookup"><span data-stu-id="316e0-172">byte</span></span>|<span data-ttu-id="316e0-173">ASCII 字元</span><span class="sxs-lookup"><span data-stu-id="316e0-173">ASCII character</span></span>|<span data-ttu-id="316e0-174">B</span><span class="sxs-lookup"><span data-stu-id="316e0-174">B</span></span>|`'a'B`|
|<span data-ttu-id="316e0-175">byte[]</span><span class="sxs-lookup"><span data-stu-id="316e0-175">byte[]</span></span>|<span data-ttu-id="316e0-176">ASCII 字串</span><span class="sxs-lookup"><span data-stu-id="316e0-176">ASCII string</span></span>|<span data-ttu-id="316e0-177">B</span><span class="sxs-lookup"><span data-stu-id="316e0-177">B</span></span>|`"text"B`|
|<span data-ttu-id="316e0-178">String 或 byte []</span><span class="sxs-lookup"><span data-stu-id="316e0-178">String or byte[]</span></span>|<span data-ttu-id="316e0-179">逐字字串</span><span class="sxs-lookup"><span data-stu-id="316e0-179">verbatim string</span></span>|<span data-ttu-id="316e0-180">@ 前置詞</span><span class="sxs-lookup"><span data-stu-id="316e0-180">@ prefix</span></span>|<span data-ttu-id="316e0-181">`@"\\server\share"` (Unicode) </span><span class="sxs-lookup"><span data-stu-id="316e0-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="316e0-182">`@"\\server\share"B` (ASCII) </span><span class="sxs-lookup"><span data-stu-id="316e0-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="316e0-183">命名常值</span><span class="sxs-lookup"><span data-stu-id="316e0-183">Named literals</span></span>

<span data-ttu-id="316e0-184">要做為常數的值可以用 [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) 屬性標記。</span><span class="sxs-lookup"><span data-stu-id="316e0-184">Values that are intended to be constants can be marked with the [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) attribute.</span></span> <span data-ttu-id="316e0-185">這個屬性的效果會導致將值編譯為常數。</span><span class="sxs-lookup"><span data-stu-id="316e0-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="316e0-186">在模式比對運算式中，以小寫字元開頭的識別碼一律會被視為要系結的變數（而不是常值），因此當您定義常值時，通常應該使用初始大寫字母。</span><span class="sxs-lookup"><span data-stu-id="316e0-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="316e0-187">備註</span><span class="sxs-lookup"><span data-stu-id="316e0-187">Remarks</span></span>

<span data-ttu-id="316e0-188">Unicode 字串可以包含您可以使用來指定的明確編碼方式， `\u` 後面接著16位的十六進位程式碼 (0000-FFFF) 或您可以使用指定的32編碼， `\U` 並在後面接著32位的十六進位程式碼，表示任何 Unicode 程式碼點 (00000000 0010FFFF) 。</span><span class="sxs-lookup"><span data-stu-id="316e0-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="316e0-189">不允許使用以外的其他位運算子 `|||` 。</span><span class="sxs-lookup"><span data-stu-id="316e0-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="316e0-190">其他基底中的整數</span><span class="sxs-lookup"><span data-stu-id="316e0-190">Integers in other bases</span></span>

<span data-ttu-id="316e0-191">您也可以 `0x` `0o` 分別使用或前置詞，以十六進位、八進位或二進位檔來指定已簽署的32位整數 `0b` 。</span><span class="sxs-lookup"><span data-stu-id="316e0-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="316e0-192">數值常值中的底線</span><span class="sxs-lookup"><span data-stu-id="316e0-192">Underscores in numeric literals</span></span>

<span data-ttu-id="316e0-193">您可以使用底線字元 () 來分隔數位 `_` 。</span><span class="sxs-lookup"><span data-stu-id="316e0-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```
