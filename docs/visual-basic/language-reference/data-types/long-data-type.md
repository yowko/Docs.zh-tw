---
title: "Long 資料類型 (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51cf03afc6b2e77ccca74fc26365fc50110e1f71
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="9494c-102">Long 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9494c-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="9494c-103">保存帶正負號的 64 位元 （8 個位元組） 整數值範圍從-9223372036854775808 到 9,223,372,036,854,775,807 (9.2 … E + 18)。</span><span class="sxs-lookup"><span data-stu-id="9494c-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9494c-104">備註</span><span class="sxs-lookup"><span data-stu-id="9494c-104">Remarks</span></span>

 <span data-ttu-id="9494c-105">使用`Long`資料類型可包含整數的數字太大，無法納入`Integer`資料型別。</span><span class="sxs-lookup"><span data-stu-id="9494c-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>  
  
 <span data-ttu-id="9494c-106">`Long` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="9494c-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="9494c-107">常值的指派</span><span class="sxs-lookup"><span data-stu-id="9494c-107">Literal assignments</span></span> 

<span data-ttu-id="9494c-108">您可以宣告和初始化`Long`變數將其指派十進位常值、 十六進位常值、 八進位常值，或是 （從開始使用 Visual Basic 2017） 二進位常值。</span><span class="sxs-lookup"><span data-stu-id="9494c-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="9494c-109">如果整數常值超出 `Long` 的範圍 (亦即，如果小於 <xref:System.Int64.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int64.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="9494c-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="9494c-110">在下列範例中，如果整數等於 4,294,967,296，即表示 `Long` 值指派了十進位、十六進位和二進位常值。</span><span class="sxs-lookup"><span data-stu-id="9494c-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> <span data-ttu-id="9494c-111">使用前置詞`&h`或`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位常值。</span><span class="sxs-lookup"><span data-stu-id="9494c-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="9494c-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="9494c-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="9494c-113">從 Visual Basic 2017 開始，您也可以使用底線字元， `_`，當做數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9494c-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="9494c-114">從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 做為前置詞和十六進位、 二進位或八進位的數字之間的前置分隔符號。</span><span class="sxs-lookup"><span data-stu-id="9494c-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="9494c-115">例如: </span><span class="sxs-lookup"><span data-stu-id="9494c-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="9494c-116">數值常值也可以包含`L`[類型字元](../../programming-guide\language-features\data-types/type-characters.md)代表`Long`資料類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9494c-116">Numeric literals can also include the `L` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="9494c-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="9494c-117">Programming tips</span></span>

-   <span data-ttu-id="9494c-118">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="9494c-118">**Interop Considerations.**</span></span> <span data-ttu-id="9494c-119">如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住，`Long`在其他環境中都有不同的資料寬度 （32 位元）。</span><span class="sxs-lookup"><span data-stu-id="9494c-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="9494c-120">如果您要將 32 位元引數至這類元件，將它宣告為`Integer`而不是`Long`新的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9494c-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="9494c-121">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="9494c-121">**Widening.**</span></span> <span data-ttu-id="9494c-122">`Long`資料類型可擴展成`Decimal`， `Single`，或`Double`。</span><span class="sxs-lookup"><span data-stu-id="9494c-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="9494c-123">這表示，您可以將 `Long` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9494c-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="9494c-124">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="9494c-124">**Type Characters.**</span></span> <span data-ttu-id="9494c-125">將常值類型字元 `L` 附加到常值，會強制其成為 `Long` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="9494c-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="9494c-126">將識別項類型字元 `&` 附加到任何識別項，會強制其成為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="9494c-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>  
  
-   <span data-ttu-id="9494c-127">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="9494c-127">**Framework Type.**</span></span> <span data-ttu-id="9494c-128">在 .NET Framework 中對應的類型為 <xref:System.Int64?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="9494c-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>  

## <a name="see-also"></a><span data-ttu-id="9494c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9494c-129">See also</span></span>

<span data-ttu-id="9494c-130"><xref:System.Int64>[資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="9494c-130"><xref:System.Int64> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="9494c-131">[整數資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="9494c-131">[Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="9494c-132">[Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="9494c-132">[Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md) </span></span>  
<span data-ttu-id="9494c-133">[類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="9494c-133">[Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="9494c-134">[轉換的摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="9494c-134">[Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
[<span data-ttu-id="9494c-135">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="9494c-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
