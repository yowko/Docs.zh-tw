---
title: UShort 資料類型 (Visual Basic)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 520c21d4df5c340b41a8b1e9055b3fadddfdf6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="7d982-102">UShort 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d982-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="7d982-103">存放不帶正負號的 16 位元 （2 個位元組） 整數，範圍從 0 到 65,535。</span><span class="sxs-lookup"><span data-stu-id="7d982-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d982-104">備註</span><span class="sxs-lookup"><span data-stu-id="7d982-104">Remarks</span></span>

 <span data-ttu-id="7d982-105">使用`UShort`資料類型可包含二進位資料太大， `Byte`。</span><span class="sxs-lookup"><span data-stu-id="7d982-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="7d982-106">`UShort` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="7d982-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="7d982-107">常值的指派</span><span class="sxs-lookup"><span data-stu-id="7d982-107">Literal assignments</span></span>

<span data-ttu-id="7d982-108">您可以宣告和初始化`UShort`變數將其指派十進位常值、 十六進位常值、 八進位常值，或是 （從開始使用 Visual Basic 2017） 二進位常值。</span><span class="sxs-lookup"><span data-stu-id="7d982-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="7d982-109">如果整數常值超出 `UShort` 的範圍 (亦即，如果小於 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="7d982-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="7d982-110">在下列範例中，整數等於 65,034 以十進位、 十六進位表示，而二進位常值指派給`UShort`值。</span><span class="sxs-lookup"><span data-stu-id="7d982-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="7d982-111">使用前置詞`&h`或`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位常值。</span><span class="sxs-lookup"><span data-stu-id="7d982-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="7d982-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="7d982-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="7d982-113">從 Visual Basic 2017 開始，您也可以使用底線字元， `_`，當做數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7d982-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="7d982-114">從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 做為前置詞和十六進位、 二進位或八進位的數字之間的前置分隔符號。</span><span class="sxs-lookup"><span data-stu-id="7d982-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="7d982-115">例如: </span><span class="sxs-lookup"><span data-stu-id="7d982-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="7d982-116">數值常值也可以包含`US`或`us`[類型字元](../../programming-guide\language-features\data-types/type-characters.md)代表`UShort`資料類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7d982-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="7d982-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="7d982-117">Programming tips</span></span>
  
-   <span data-ttu-id="7d982-118">**負的數字。**</span><span class="sxs-lookup"><span data-stu-id="7d982-118">**Negative Numbers.**</span></span> <span data-ttu-id="7d982-119">因為`UShort`是不帶正負號的類型，它無法表示為負數。</span><span class="sxs-lookup"><span data-stu-id="7d982-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="7d982-120">如果您使用一元減號 (`-`) 運算子的運算式評估為輸入`UShort`，Visual Basic 會將轉換的運算式`Integer`第一次。</span><span class="sxs-lookup"><span data-stu-id="7d982-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="7d982-121">**Cls 符合性。**</span><span class="sxs-lookup"><span data-stu-id="7d982-121">**CLS Compliance.**</span></span> <span data-ttu-id="7d982-122">`UShort`資料類型不是屬於[Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) （cls） 標準，所以符合 CLS 標準的程式碼無法使用所使用的元件。</span><span class="sxs-lookup"><span data-stu-id="7d982-122">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="7d982-123">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="7d982-123">**Widening.**</span></span> <span data-ttu-id="7d982-124">`UShort`資料類型可擴展成`Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，和`Double`。</span><span class="sxs-lookup"><span data-stu-id="7d982-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="7d982-125">這表示您可以將轉換`UShort`而不會發生這些類型的任何<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="7d982-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="7d982-126">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="7d982-126">**Type Characters.**</span></span> <span data-ttu-id="7d982-127">將常值類型字元附加`US`到常值會強制其成為`UShort`資料型別。</span><span class="sxs-lookup"><span data-stu-id="7d982-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="7d982-128">`UShort` 有任何識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="7d982-128">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="7d982-129">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="7d982-129">**Framework Type.**</span></span> <span data-ttu-id="7d982-130">在 .NET Framework 中對應的類型為 <xref:System.UInt16?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="7d982-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d982-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d982-131">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="7d982-132">資料類型</span><span class="sxs-lookup"><span data-stu-id="7d982-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="7d982-133">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="7d982-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="7d982-134">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="7d982-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="7d982-135">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="7d982-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="7d982-136">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="7d982-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
