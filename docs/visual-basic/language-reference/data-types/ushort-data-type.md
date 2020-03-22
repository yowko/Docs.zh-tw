---
title: UShort 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400691"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="cb967-102">UShort 資料類型（可視基本）</span><span class="sxs-lookup"><span data-stu-id="cb967-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="cb967-103">保存未簽名的 16 位（2 位元組）整數，其值範圍為 0 到 65，535。</span><span class="sxs-lookup"><span data-stu-id="cb967-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb967-104">備註</span><span class="sxs-lookup"><span data-stu-id="cb967-104">Remarks</span></span>

 <span data-ttu-id="cb967-105">使用`UShort`資料類型包含的二進位資料太大。 `Byte`</span><span class="sxs-lookup"><span data-stu-id="cb967-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="cb967-106">`UShort` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="cb967-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="cb967-107">文本分配</span><span class="sxs-lookup"><span data-stu-id="cb967-107">Literal assignments</span></span>

<span data-ttu-id="cb967-108">您可以通過為其分配十進位文本、`UShort`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="cb967-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="cb967-109">如果整數常值超出 `UShort` 的範圍 (亦即，如果小於 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="cb967-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="cb967-110">在下面的示例中，等於 65，034 的整數，表示為十進位、十六進位和二進位文本`UShort`。</span><span class="sxs-lookup"><span data-stu-id="cb967-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="cb967-111">`&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。</span><span class="sxs-lookup"><span data-stu-id="cb967-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="cb967-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="cb967-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="cb967-113">從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="cb967-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="cb967-114">從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。</span><span class="sxs-lookup"><span data-stu-id="cb967-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="cb967-115">例如：</span><span class="sxs-lookup"><span data-stu-id="cb967-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="cb967-116">數位文本還可以包括`US`或`us`[類型字元](../../programming-guide/language-features/data-types/type-characters.md)來表示`UShort`資料類型，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="cb967-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="cb967-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="cb967-117">Programming tips</span></span>
  
- <span data-ttu-id="cb967-118">**負數。**</span><span class="sxs-lookup"><span data-stu-id="cb967-118">**Negative Numbers.**</span></span> <span data-ttu-id="cb967-119">因為它是`UShort`無符號類型，它不能表示負數。</span><span class="sxs-lookup"><span data-stu-id="cb967-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="cb967-120">如果在計算為鍵入`-``UShort`的運算式上使用一元減號 （ ） 運算子，Visual Basic 將運算式轉換為`Integer`第一個運算式。</span><span class="sxs-lookup"><span data-stu-id="cb967-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="cb967-121">**CLS 合規性。**</span><span class="sxs-lookup"><span data-stu-id="cb967-121">**CLS Compliance.**</span></span> <span data-ttu-id="cb967-122">資料類型`UShort`不是[通用語言規範](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（CLS） 的一部分，因此符合 CLS 的代碼不能使用使用它的元件。</span><span class="sxs-lookup"><span data-stu-id="cb967-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="cb967-123">**擴大。**</span><span class="sxs-lookup"><span data-stu-id="cb967-123">**Widening.**</span></span> <span data-ttu-id="cb967-124">資料類型`UShort`擴展到`Integer`、、、、、、、、`Single``Double``UInteger``Long``ULong``Decimal`和 。</span><span class="sxs-lookup"><span data-stu-id="cb967-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="cb967-125">這意味著您可以轉換為`UShort`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="cb967-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="cb967-126">**鍵入字元。**</span><span class="sxs-lookup"><span data-stu-id="cb967-126">**Type Characters.**</span></span> <span data-ttu-id="cb967-127">將常值型別字元`US`追加到文本強制它到`UShort`資料類型。</span><span class="sxs-lookup"><span data-stu-id="cb967-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="cb967-128">`UShort`沒有識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="cb967-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="cb967-129">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="cb967-129">**Framework Type.**</span></span> <span data-ttu-id="cb967-130">在 .NET Framework 中對應的類型為 <xref:System.UInt16?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="cb967-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb967-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb967-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="cb967-132">資料類型</span><span class="sxs-lookup"><span data-stu-id="cb967-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="cb967-133">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="cb967-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="cb967-134">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="cb967-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="cb967-135">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="cb967-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="cb967-136">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="cb967-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
