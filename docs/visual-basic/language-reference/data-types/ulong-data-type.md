---
title: ULong 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: ee9297ae917345d44d8e630bd09beea2245b56da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415514"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="1754a-102">ULONG 資料型別（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1754a-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="1754a-103">保留不帶正負號的64位（8位元組）整數，範圍介於0到18446744073709551615之間（超過1.84 倍 10 ^ 19）。</span><span class="sxs-lookup"><span data-stu-id="1754a-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="1754a-104">備註</span><span class="sxs-lookup"><span data-stu-id="1754a-104">Remarks</span></span>

<span data-ttu-id="1754a-105">使用 `ULong` 資料類型可包含對而言太大的二進位資料 `UInteger` ，或是可能不帶正負號的最大整數值。</span><span class="sxs-lookup"><span data-stu-id="1754a-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="1754a-106">`ULong` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="1754a-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="1754a-107">常值指派</span><span class="sxs-lookup"><span data-stu-id="1754a-107">Literal assignments</span></span>

<span data-ttu-id="1754a-108">您可以藉 `ULong` 由指派十進位常值、十六進位常值、八進位常值，或二進位常值（從 Visual Basic 2017）來宣告和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="1754a-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="1754a-109">如果整數常值超出 `ULong` 的範圍 (亦即，如果小於 <xref:System.UInt64.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="1754a-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="1754a-110">在下列範例中，以十進位、十六進位和二進位常值表示的 7,934,076,125 整數，會指派給 `ULong` 值。</span><span class="sxs-lookup"><span data-stu-id="1754a-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="1754a-111">您可以使用前置詞 `&h` 或 `&H` 來表示十六進位常值、前置詞 `&b` 或表示 `&B` 二進位常值，以及前置詞 `&o` 或 `&O` 來表示八進位常值。</span><span class="sxs-lookup"><span data-stu-id="1754a-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="1754a-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="1754a-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="1754a-113">從 Visual Basic 2017 開始，您也可以使用底線字元 `_` 做為數位分隔符號來增強可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1754a-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="1754a-114">從 Visual Basic 15.5 開始，您也可以使用底線字元（ `_` ）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。</span><span class="sxs-lookup"><span data-stu-id="1754a-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="1754a-115">例如：</span><span class="sxs-lookup"><span data-stu-id="1754a-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="1754a-116">數值常值也可以包含 `UL` 或 `ul` [類型字元](../../programming-guide/language-features/data-types/type-characters.md)來表示 `ULong` 資料類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1754a-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="1754a-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="1754a-117">Programming tips</span></span>

- <span data-ttu-id="1754a-118">**負數。**</span><span class="sxs-lookup"><span data-stu-id="1754a-118">**Negative Numbers.**</span></span> <span data-ttu-id="1754a-119">因為 `ULong` 是不帶正負號的類型，所以不能代表負數。</span><span class="sxs-lookup"><span data-stu-id="1754a-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="1754a-120">如果您 `-` 在評估為類型的運算式上使用一元減號（）運算子 `ULong` ，Visual Basic 會將運算式轉換為 `Decimal` first。</span><span class="sxs-lookup"><span data-stu-id="1754a-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="1754a-121">**CLS 合規性。**</span><span class="sxs-lookup"><span data-stu-id="1754a-121">**CLS Compliance.**</span></span> <span data-ttu-id="1754a-122">`ULong`資料類型不是[Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) （CLS）的一部分，因此符合 cls 標準的程式碼無法使用使用它的元件。</span><span class="sxs-lookup"><span data-stu-id="1754a-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="1754a-123">**Interop 考量：**</span><span class="sxs-lookup"><span data-stu-id="1754a-123">**Interop Considerations.**</span></span> <span data-ttu-id="1754a-124">如果您要使用的元件不是針對 .NET Framework 所撰寫（例如 Automation 或 COM 物件），請記住，之類的類型 `ulong` 在其他環境中可能會有不同的資料寬度（32位）。</span><span class="sxs-lookup"><span data-stu-id="1754a-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="1754a-125">如果您要將32位引數傳遞至這類元件，請 `UInteger` `ULong` 在 managed Visual Basic 程式碼中將它宣告為而不是。</span><span class="sxs-lookup"><span data-stu-id="1754a-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="1754a-126">此外，自動化不支援 Windows 95、Windows 98、Windows ME 或 Windows 2000 上的64位整數。</span><span class="sxs-lookup"><span data-stu-id="1754a-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="1754a-127">您無法將 Visual Basic `ULong` 引數傳遞至這些平臺上的 Automation 元件。</span><span class="sxs-lookup"><span data-stu-id="1754a-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="1754a-128">**加寬.**</span><span class="sxs-lookup"><span data-stu-id="1754a-128">**Widening.**</span></span> <span data-ttu-id="1754a-129">`ULong`資料類型會擴大為 `Decimal` 、 `Single` 和 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="1754a-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="1754a-130">這表示您可以轉換 `ULong` 成這些類型的任何一種，而不會遇到 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1754a-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="1754a-131">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="1754a-131">**Type Characters.**</span></span> <span data-ttu-id="1754a-132">將常數值型別字元附加 `UL` 到常值，會強制其成為 `ULong` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="1754a-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="1754a-133">`ULong`沒有識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="1754a-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="1754a-134">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="1754a-134">**Framework Type.**</span></span> <span data-ttu-id="1754a-135">在 .NET Framework 中對應的類型為 <xref:System.UInt64?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="1754a-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="1754a-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1754a-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="1754a-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="1754a-137">Data Types</span></span>](index.md)
- [<span data-ttu-id="1754a-138">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="1754a-138">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="1754a-139">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="1754a-139">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="1754a-140">作法：呼叫不帶正負號的類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="1754a-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="1754a-141">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="1754a-141">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
