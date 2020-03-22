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
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400698"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="e059d-102">ULONG 資料型別（可視基本）</span><span class="sxs-lookup"><span data-stu-id="e059d-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="e059d-103">持有未簽名的 64 位（8 位元組）整數，價值範圍為 0 到 18，446，744，073，709，551，615（超過 1.84 倍 10 = 19）。</span><span class="sxs-lookup"><span data-stu-id="e059d-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="e059d-104">備註</span><span class="sxs-lookup"><span data-stu-id="e059d-104">Remarks</span></span>

<span data-ttu-id="e059d-105">使用`ULong`資料類型包含對於 的`UInteger`二進位資料太大或最大可能的不帶正負號的整數值。</span><span class="sxs-lookup"><span data-stu-id="e059d-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="e059d-106">`ULong` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="e059d-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="e059d-107">文本分配</span><span class="sxs-lookup"><span data-stu-id="e059d-107">Literal assignments</span></span>

<span data-ttu-id="e059d-108">您可以通過為其分配十進位文本、`ULong`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="e059d-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="e059d-109">如果整數常值超出 `ULong` 的範圍 (亦即，如果小於 <xref:System.UInt64.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="e059d-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="e059d-110">在下列範例中，以十進位、十六進位和二進位常值表示的 7,934,076,125 整數，會指派給 `ULong` 值。</span><span class="sxs-lookup"><span data-stu-id="e059d-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="e059d-111">`&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。</span><span class="sxs-lookup"><span data-stu-id="e059d-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="e059d-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="e059d-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="e059d-113">從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="e059d-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="e059d-114">從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e059d-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="e059d-115">例如：</span><span class="sxs-lookup"><span data-stu-id="e059d-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="e059d-116">數位文本還可以包括`UL`或`ul`[類型字元](../../programming-guide/language-features/data-types/type-characters.md)來表示`ULong`資料類型，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="e059d-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="e059d-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="e059d-117">Programming tips</span></span>

- <span data-ttu-id="e059d-118">**負數。**</span><span class="sxs-lookup"><span data-stu-id="e059d-118">**Negative Numbers.**</span></span> <span data-ttu-id="e059d-119">因為它是`ULong`無符號類型，它不能表示負數。</span><span class="sxs-lookup"><span data-stu-id="e059d-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="e059d-120">如果在計算為鍵入`-``ULong`的運算式上使用一元減號 （ ） 運算子，Visual Basic 將運算式轉換為`Decimal`第一個運算式。</span><span class="sxs-lookup"><span data-stu-id="e059d-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="e059d-121">**CLS 合規性。**</span><span class="sxs-lookup"><span data-stu-id="e059d-121">**CLS Compliance.**</span></span> <span data-ttu-id="e059d-122">資料類型`ULong`不是[通用語言規範](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（CLS） 的一部分，因此符合 CLS 的代碼不能使用使用它的元件。</span><span class="sxs-lookup"><span data-stu-id="e059d-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="e059d-123">**Interop 考量：**</span><span class="sxs-lookup"><span data-stu-id="e059d-123">**Interop Considerations.**</span></span> <span data-ttu-id="e059d-124">如果要與未為 .NET 框架編寫的元件（例如自動化或 COM 物件）介面，請記住，例如在其他`ulong`環境中具有不同資料寬度（32 位）的類型。</span><span class="sxs-lookup"><span data-stu-id="e059d-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="e059d-125">如果要將 32 位參數傳遞給此類元件，請將其聲明為`UInteger`託管 Visual `ULong` Basic 代碼中而不是。</span><span class="sxs-lookup"><span data-stu-id="e059d-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="e059d-126">此外，自動化不支援 Windows 95、Windows 98、Windows ME 或 Windows 2000 上的 64 位整數。</span><span class="sxs-lookup"><span data-stu-id="e059d-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="e059d-127">不能將 Visual Basic`ULong`參數傳遞給這些平臺上的自動化元件。</span><span class="sxs-lookup"><span data-stu-id="e059d-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="e059d-128">**擴大。**</span><span class="sxs-lookup"><span data-stu-id="e059d-128">**Widening.**</span></span> <span data-ttu-id="e059d-129">資料類型`ULong`擴展到`Decimal`.`Single`和`Double`。</span><span class="sxs-lookup"><span data-stu-id="e059d-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="e059d-130">這意味著您可以轉換為`ULong`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="e059d-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="e059d-131">**鍵入字元。**</span><span class="sxs-lookup"><span data-stu-id="e059d-131">**Type Characters.**</span></span> <span data-ttu-id="e059d-132">將常值型別字元`UL`追加到文本強制它到`ULong`資料類型。</span><span class="sxs-lookup"><span data-stu-id="e059d-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="e059d-133">`ULong`沒有識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="e059d-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="e059d-134">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="e059d-134">**Framework Type.**</span></span> <span data-ttu-id="e059d-135">在 .NET Framework 中對應的類型為 <xref:System.UInt64?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="e059d-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="e059d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e059d-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="e059d-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="e059d-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="e059d-138">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="e059d-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="e059d-139">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="e059d-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="e059d-140">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="e059d-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="e059d-141">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="e059d-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
