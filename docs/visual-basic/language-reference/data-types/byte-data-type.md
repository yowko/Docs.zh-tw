---
title: Byte 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400740"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="ab195-102">位元組資料類型（可視基本）</span><span class="sxs-lookup"><span data-stu-id="ab195-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="ab195-103">保存未簽名的 8 位（1 位元組）整數，其值範圍為 0 到 255。</span><span class="sxs-lookup"><span data-stu-id="ab195-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab195-104">備註</span><span class="sxs-lookup"><span data-stu-id="ab195-104">Remarks</span></span>

<span data-ttu-id="ab195-105">使用`Byte`資料類型包含二進位資料。</span><span class="sxs-lookup"><span data-stu-id="ab195-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="ab195-106">`Byte` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="ab195-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="ab195-107">文本分配</span><span class="sxs-lookup"><span data-stu-id="ab195-107">Literal assignments</span></span>

<span data-ttu-id="ab195-108">您可以通過為其分配十進位文本、`Byte`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="ab195-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ab195-109">如果積分文本超出 的範圍`Byte`（即，如果它小於<xref:System.Byte.MinValue?displayProperty=nameWithType>或大於<xref:System.Byte.MaxValue?displayProperty=nameWithType>），則會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab195-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="ab195-110">在下面的示例中，等於 201 的整數表示為十進位、十六進位和二進位文本，從[整數](integer-data-type.md)隱式轉換為`byte`值。</span><span class="sxs-lookup"><span data-stu-id="ab195-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="ab195-111">`&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。</span><span class="sxs-lookup"><span data-stu-id="ab195-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ab195-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="ab195-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ab195-113">從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="ab195-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="ab195-114">從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ab195-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ab195-115">例如：</span><span class="sxs-lookup"><span data-stu-id="ab195-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="ab195-116">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="ab195-116">Programming tips</span></span>

- <span data-ttu-id="ab195-117">**負數。**</span><span class="sxs-lookup"><span data-stu-id="ab195-117">**Negative Numbers.**</span></span> <span data-ttu-id="ab195-118">因為它是`Byte`無符號類型，它不能表示負數。</span><span class="sxs-lookup"><span data-stu-id="ab195-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="ab195-119">如果在計算為鍵入`-``Byte`的運算式上使用一元減號 （ ） 運算子，Visual Basic 將運算式轉換為`Short`第一個運算式。</span><span class="sxs-lookup"><span data-stu-id="ab195-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="ab195-120">**格式轉換。**</span><span class="sxs-lookup"><span data-stu-id="ab195-120">**Format Conversions.**</span></span> <span data-ttu-id="ab195-121">當 Visual Basic 讀取或寫入檔時，或者當它調用 DLL、方法和屬性時，它可以在資料格式之間自動轉換。</span><span class="sxs-lookup"><span data-stu-id="ab195-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="ab195-122">存儲在變數和陣列`Byte`中的二進位資料在此類格式轉換期間保留。</span><span class="sxs-lookup"><span data-stu-id="ab195-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="ab195-123">不應將`String`變數用於二進位資料，因為其內容在 ANSI 和 Unicode 格式之間的轉換過程中可能會損壞。</span><span class="sxs-lookup"><span data-stu-id="ab195-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="ab195-124">**擴大。**</span><span class="sxs-lookup"><span data-stu-id="ab195-124">**Widening.**</span></span> <span data-ttu-id="ab195-125">資料類型`Byte``Short`擴展到 、 `UShort` `Integer`、 、 `UInteger`、 `Long` `ULong`、 `Decimal` `Single`、 `Double`、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、</span><span class="sxs-lookup"><span data-stu-id="ab195-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="ab195-126">這意味著您可以轉換為`Byte`任何這些類型的，而不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab195-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="ab195-127">**鍵入字元。**</span><span class="sxs-lookup"><span data-stu-id="ab195-127">**Type Characters.**</span></span> <span data-ttu-id="ab195-128">`Byte`沒有常值型別字元或識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="ab195-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="ab195-129">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="ab195-129">**Framework Type.**</span></span> <span data-ttu-id="ab195-130">在 .NET Framework 中對應的類型為 <xref:System.Byte?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="ab195-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="ab195-131">範例</span><span class="sxs-lookup"><span data-stu-id="ab195-131">Example</span></span>

 <span data-ttu-id="ab195-132">在下面的示例中，`b`是一個`Byte`變數。</span><span class="sxs-lookup"><span data-stu-id="ab195-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="ab195-133">這些語句演示了變數的範圍以及位移位運算子對變數的應用。</span><span class="sxs-lookup"><span data-stu-id="ab195-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="ab195-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab195-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="ab195-135">資料類型</span><span class="sxs-lookup"><span data-stu-id="ab195-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="ab195-136">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="ab195-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="ab195-137">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="ab195-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="ab195-138">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="ab195-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
