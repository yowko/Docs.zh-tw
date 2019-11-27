---
title: UInteger 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343893"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="2c0d2-102">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="2c0d2-102">UInteger data type</span></span>

<span data-ttu-id="2c0d2-103">保留不帶正負號的32位（4位元組）整數，範圍是從0到4294967295的值。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c0d2-104">備註</span><span class="sxs-lookup"><span data-stu-id="2c0d2-104">Remarks</span></span>

<span data-ttu-id="2c0d2-105">`UInteger` 資料類型會以最有效率的資料寬度提供最大不帶正負號的值。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="2c0d2-106">`UInteger` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="2c0d2-107">常值指派</span><span class="sxs-lookup"><span data-stu-id="2c0d2-107">Literal assignments</span></span>

<span data-ttu-id="2c0d2-108">您可以藉由指派十進位常值、十六進位常值、八進位常值，或二進位常值（從 Visual Basic 2017）來宣告和初始化 `UInteger` 變數。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="2c0d2-109">如果整數常值超出 `UInteger` 的範圍 (亦即，如果小於 <xref:System.UInt32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="2c0d2-110">在下列範例中，以十進位、十六進位和二進位常值表示的 3,000,000,000 整數，會指派給 `UInteger` 值。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="2c0d2-111">您可以使用前置詞 `&h` 或 `&H` 來表示十六進位常值、前置詞 `&b` 或 `&B` 來表示二進位常值，而前置詞 `&o` 或 `&O` 表示八進位常值。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="2c0d2-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2c0d2-113">從 Visual Basic 2017 開始，您也可以使用底線字元（`_`）做為數位分隔符號，以增強可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="2c0d2-114">從 Visual Basic 15.5 開始，您也可以使用底線字元（`_`）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="2c0d2-115">例如：</span><span class="sxs-lookup"><span data-stu-id="2c0d2-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="2c0d2-116">數值常值也可以包含 `UI` 或 `ui`[類型字元](../../programming-guide/language-features/data-types/type-characters.md)來表示 `UInteger` 資料類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="2c0d2-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="2c0d2-117">Programming tips</span></span>

<span data-ttu-id="2c0d2-118">`UInteger` 和 `Integer` 資料類型會在32位處理器上提供最佳效能，因為較小的整數類型（`UShort`、`Short`、`Byte`和 `SByte`），即使使用較少的位，也需要更多時間來載入、儲存和提取。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="2c0d2-119">**負數。**</span><span class="sxs-lookup"><span data-stu-id="2c0d2-119">**Negative Numbers.**</span></span> <span data-ttu-id="2c0d2-120">因為 `UInteger` 是不帶正負號的類型，所以不能代表負數。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="2c0d2-121">如果您在評估為類型 `UInteger`的運算式上使用一元減號（`-`）運算子，Visual Basic 會先將運算式轉換成 `Long`。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="2c0d2-122">**CLS 合規性。**</span><span class="sxs-lookup"><span data-stu-id="2c0d2-122">**CLS Compliance.**</span></span> <span data-ttu-id="2c0d2-123">`UInteger` 資料類型不是[Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) （CLS）的一部分，因此符合 cls 標準的程式碼無法使用它所使用的元件。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="2c0d2-124">**Interop 考慮。**</span><span class="sxs-lookup"><span data-stu-id="2c0d2-124">**Interop Considerations.**</span></span> <span data-ttu-id="2c0d2-125">如果您要使用的元件不是針對 .NET Framework 所撰寫（例如 Automation 或 COM 物件），請記住，`uint` 之類的類型在其他環境中可能會有不同的資料寬度（16位）。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="2c0d2-126">如果您要將16位引數傳遞至這類元件，請將它宣告為 `UShort`，而不是在您的 managed Visual Basic 程式碼中 `UInteger`。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="2c0d2-127">**加寬.**</span><span class="sxs-lookup"><span data-stu-id="2c0d2-127">**Widening.**</span></span> <span data-ttu-id="2c0d2-128">`UInteger` 資料類型會擴展到 `Long`、`ULong`、`Decimal`、`Single`和 `Double`。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="2c0d2-129">這表示您可以將 `UInteger` 轉換成這些類型的任何一種，而不會遇到 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="2c0d2-130">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="2c0d2-130">**Type Characters.**</span></span> <span data-ttu-id="2c0d2-131">將常數值型別字元附加到常值 `UI` 會強制其成為 `UInteger` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="2c0d2-132">`UInteger` 沒有識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="2c0d2-133">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="2c0d2-133">**Framework Type.**</span></span> <span data-ttu-id="2c0d2-134">在 .NET Framework 中對應的類型為 <xref:System.UInt32?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="2c0d2-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c0d2-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="2c0d2-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="2c0d2-136">資料類型</span><span class="sxs-lookup"><span data-stu-id="2c0d2-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="2c0d2-137">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="2c0d2-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="2c0d2-138">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="2c0d2-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="2c0d2-139">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="2c0d2-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="2c0d2-140">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="2c0d2-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
