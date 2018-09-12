---
title: Byte 資料類型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b106005ff07f55e05ae66dba94041cd8b5c24bb
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700692"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="e6c30-102">Byte 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6c30-102">Byte data type (Visual Basic)</span></span>
<span data-ttu-id="e6c30-103">保留範圍從 0 到 255 的不帶正負號的 8 位元 （1 個位元組） 整數。</span><span class="sxs-lookup"><span data-stu-id="e6c30-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6c30-104">備註</span><span class="sxs-lookup"><span data-stu-id="e6c30-104">Remarks</span></span>

<span data-ttu-id="e6c30-105">使用`Byte`包含二進位資料的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e6c30-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="e6c30-106">`Byte` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="e6c30-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="e6c30-107">常值的指派</span><span class="sxs-lookup"><span data-stu-id="e6c30-107">Literal assignments</span></span>

<span data-ttu-id="e6c30-108">您可以宣告並初始化`Byte`變數指派十進位常值、 十六進位常值、 八進位的常值，或 （Visual Basic 2017 年起） 二進位常值。</span><span class="sxs-lookup"><span data-stu-id="e6c30-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="e6c30-109">如果整數常值超出範圍`Byte`(亦即，如果是小於<xref:System.Byte.MinValue?displayProperty=nameWithType>或大於<xref:System.Byte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6c30-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="e6c30-110">在下列範例中，以十進位、 十六進位表示的 201 和二進位常值會以隱含方式轉換來自[整數](integer-data-type.md)到`byte`值。</span><span class="sxs-lookup"><span data-stu-id="e6c30-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="e6c30-111">使用前置詞`&h`或是`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位的常值。</span><span class="sxs-lookup"><span data-stu-id="e6c30-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="e6c30-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="e6c30-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="e6c30-113">從 Visual Basic 2017 開始，您也可以使用底線字元`_`，作為數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e6c30-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="e6c30-114">從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 作為前置分隔符號之間的前置詞和十六進位、 二進位或八進位數字。</span><span class="sxs-lookup"><span data-stu-id="e6c30-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="e6c30-115">例如: </span><span class="sxs-lookup"><span data-stu-id="e6c30-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="e6c30-116">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="e6c30-116">Programming tips</span></span>

-   <span data-ttu-id="e6c30-117">**負數的數字。**</span><span class="sxs-lookup"><span data-stu-id="e6c30-117">**Negative Numbers.**</span></span> <span data-ttu-id="e6c30-118">因為`Byte`是不帶正負號的型別，它無法表示負數。</span><span class="sxs-lookup"><span data-stu-id="e6c30-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="e6c30-119">如果您使用一元減號 (`-`) 運算子的運算式，評估為類型`Byte`，Visual Basic 會將轉換的運算式`Short`第一次。</span><span class="sxs-lookup"><span data-stu-id="e6c30-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
-   <span data-ttu-id="e6c30-120">**格式轉換。**</span><span class="sxs-lookup"><span data-stu-id="e6c30-120">**Format Conversions.**</span></span> <span data-ttu-id="e6c30-121">當 Visual Basic 中讀取或寫入檔案，或呼叫的 Dll、 方法和屬性時，它可以自動資料格式之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="e6c30-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="e6c30-122">二進位資料儲存在`Byte`這種格式轉換期間會保留變數和陣列。</span><span class="sxs-lookup"><span data-stu-id="e6c30-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="e6c30-123">您不應該使用`String`變數的二進位資料，因為其內容可能會損毀，ANSI 和 Unicode 格式之間轉換時。</span><span class="sxs-lookup"><span data-stu-id="e6c30-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

-   <span data-ttu-id="e6c30-124">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="e6c30-124">**Widening.**</span></span> <span data-ttu-id="e6c30-125">`Byte`資料類型可擴展為`Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，或`Double`。</span><span class="sxs-lookup"><span data-stu-id="e6c30-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="e6c30-126">這表示您可以將轉換`Byte`任何一種類型，而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6c30-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="e6c30-127">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="e6c30-127">**Type Characters.**</span></span> <span data-ttu-id="e6c30-128">`Byte` 沒有任何常值類型字元或識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="e6c30-128">`Byte` has no literal type character or identifier type character.</span></span>

-   <span data-ttu-id="e6c30-129">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="e6c30-129">**Framework Type.**</span></span> <span data-ttu-id="e6c30-130">在 .NET Framework 中對應的類型為 <xref:System.Byte?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="e6c30-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="e6c30-131">範例</span><span class="sxs-lookup"><span data-stu-id="e6c30-131">Example</span></span>

 <span data-ttu-id="e6c30-132">在下列範例中，`b`是`Byte`變數。</span><span class="sxs-lookup"><span data-stu-id="e6c30-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="e6c30-133">陳述式示範變數的範圍和應用程式的位元移位運算子。</span><span class="sxs-lookup"><span data-stu-id="e6c30-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a><span data-ttu-id="e6c30-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6c30-134">See Also</span></span>

 <xref:System.Byte?displayProperty=nameWithType>  
 [<span data-ttu-id="e6c30-135">資料類型</span><span class="sxs-lookup"><span data-stu-id="e6c30-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="e6c30-136">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="e6c30-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="e6c30-137">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="e6c30-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="e6c30-138">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="e6c30-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
