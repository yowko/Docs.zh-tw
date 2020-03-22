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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400782"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="3a307-102">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="3a307-102">UInteger data type</span></span>

<span data-ttu-id="3a307-103">保存未簽名的 32 位（4 位元組）整數，其值範圍為 0 到 4，294，967，295。</span><span class="sxs-lookup"><span data-stu-id="3a307-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a307-104">備註</span><span class="sxs-lookup"><span data-stu-id="3a307-104">Remarks</span></span>

<span data-ttu-id="3a307-105">資料類型`UInteger`提供最有效的資料寬度中的最大未簽名值。</span><span class="sxs-lookup"><span data-stu-id="3a307-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="3a307-106">`UInteger` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="3a307-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="3a307-107">文本分配</span><span class="sxs-lookup"><span data-stu-id="3a307-107">Literal assignments</span></span>

<span data-ttu-id="3a307-108">您可以通過為其分配十進位文本、`UInteger`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="3a307-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="3a307-109">如果整數常值超出 `UInteger` 的範圍 (亦即，如果小於 <xref:System.UInt32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="3a307-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="3a307-110">在下列範例中，以十進位、十六進位和二進位常值表示的 3,000,000,000 整數，會指派給 `UInteger` 值。</span><span class="sxs-lookup"><span data-stu-id="3a307-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="3a307-111">`&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。</span><span class="sxs-lookup"><span data-stu-id="3a307-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="3a307-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="3a307-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="3a307-113">從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="3a307-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="3a307-114">從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3a307-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="3a307-115">例如：</span><span class="sxs-lookup"><span data-stu-id="3a307-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="3a307-116">數位文本還可以包括`UI`或`ui`[類型字元](../../programming-guide/language-features/data-types/type-characters.md)來表示`UInteger`資料類型，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="3a307-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="3a307-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="3a307-117">Programming tips</span></span>

<span data-ttu-id="3a307-118">和`UInteger``Integer`資料類型在 32 位處理器上提供最佳性能，因為較小的整數類型 （、、`UShort``Short``Byte`和`SByte`）即使使用較少的位，也需要更多的時間來載入、存儲和提取。</span><span class="sxs-lookup"><span data-stu-id="3a307-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="3a307-119">**負數。**</span><span class="sxs-lookup"><span data-stu-id="3a307-119">**Negative Numbers.**</span></span> <span data-ttu-id="3a307-120">因為它是`UInteger`無符號類型，它不能表示負數。</span><span class="sxs-lookup"><span data-stu-id="3a307-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="3a307-121">如果在計算為鍵入`-``UInteger`的運算式上使用一元減號 （ ） 運算子，Visual Basic 將運算式轉換為`Long`第一個運算式。</span><span class="sxs-lookup"><span data-stu-id="3a307-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="3a307-122">**CLS 合規性。**</span><span class="sxs-lookup"><span data-stu-id="3a307-122">**CLS Compliance.**</span></span> <span data-ttu-id="3a307-123">資料類型`UInteger`不是[通用語言規範](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（CLS） 的一部分，因此符合 CLS 的代碼不能使用使用它的元件。</span><span class="sxs-lookup"><span data-stu-id="3a307-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="3a307-124">**Interop 考量：**</span><span class="sxs-lookup"><span data-stu-id="3a307-124">**Interop Considerations.**</span></span> <span data-ttu-id="3a307-125">如果要與未為 .NET 框架編寫的元件（例如自動化或 COM 物件）介面，請記住，例如在其他`uint`環境中具有不同資料寬度（16 位）的類型。</span><span class="sxs-lookup"><span data-stu-id="3a307-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="3a307-126">如果要將 16 位參數傳遞給此類元件，請將其聲明為`UShort`託管 Visual `UInteger` Basic 代碼中而不是。</span><span class="sxs-lookup"><span data-stu-id="3a307-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="3a307-127">**擴大。**</span><span class="sxs-lookup"><span data-stu-id="3a307-127">**Widening.**</span></span> <span data-ttu-id="3a307-128">資料類型`UInteger`擴展到`Long` `ULong`、、、`Decimal``Single`和`Double`。</span><span class="sxs-lookup"><span data-stu-id="3a307-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="3a307-129">這意味著您可以轉換為`UInteger`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="3a307-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="3a307-130">**鍵入字元。**</span><span class="sxs-lookup"><span data-stu-id="3a307-130">**Type Characters.**</span></span> <span data-ttu-id="3a307-131">將常值型別字元`UI`追加到文本強制它到`UInteger`資料類型。</span><span class="sxs-lookup"><span data-stu-id="3a307-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="3a307-132">`UInteger`沒有識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="3a307-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="3a307-133">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="3a307-133">**Framework Type.**</span></span> <span data-ttu-id="3a307-134">在 .NET Framework 中對應的類型為 <xref:System.UInt32?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="3a307-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a307-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a307-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="3a307-136">資料類型</span><span class="sxs-lookup"><span data-stu-id="3a307-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="3a307-137">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="3a307-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="3a307-138">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="3a307-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="3a307-139">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="3a307-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="3a307-140">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="3a307-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
