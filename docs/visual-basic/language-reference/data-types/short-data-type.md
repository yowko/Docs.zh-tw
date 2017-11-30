---
title: "Short 資料類型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
f1_keywords: vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: fef948debed69cf9fb7b0e6bb65eb0ddbe497a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="30e77-102">Short 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30e77-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="30e77-103">保存帶正負號的 16 位元 （2 個位元組） 整數，範圍從-32,768 到 32,767。</span><span class="sxs-lookup"><span data-stu-id="30e77-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30e77-104">備註</span><span class="sxs-lookup"><span data-stu-id="30e77-104">Remarks</span></span>  
 <span data-ttu-id="30e77-105">使用`Short`資料類型可包含不需要完整的資料寬度的整數值`Integer`。</span><span class="sxs-lookup"><span data-stu-id="30e77-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="30e77-106">組件的 common language runtime 可以在某些情況下，您`Short`緊密，並將記憶體耗用量儲存變數。</span><span class="sxs-lookup"><span data-stu-id="30e77-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="30e77-107">`Short` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="30e77-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="30e77-108">常值的指派</span><span class="sxs-lookup"><span data-stu-id="30e77-108">Literal assignments</span></span>

<span data-ttu-id="30e77-109">您可以宣告和初始化`Short`變數將其指派十進位常值、 十六進位常值、 八進位常值，或是 （從開始使用 Visual Basic 2017） 二進位常值。</span><span class="sxs-lookup"><span data-stu-id="30e77-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="30e77-110">如果整數常值超出 `Short` 的範圍 (亦即，如果小於 <xref:System.Int16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="30e77-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="30e77-111">在下列範例中，整數等於會以十進位、 十六進位表示的 1,034 和二進位常值會隱含地轉換從[整數](integer-data-type.md)至`Short`值。</span><span class="sxs-lookup"><span data-stu-id="30e77-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="30e77-112">使用前置詞`&h`或`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位常值。</span><span class="sxs-lookup"><span data-stu-id="30e77-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="30e77-113">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="30e77-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="30e77-114">從 Visual Basic 2017 開始，您也可以使用底線字元， `_`，當做數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="30e77-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="30e77-115">數值常值也可以包含`S`[類型字元](../../programming-guide\language-features\data-types/type-characters.md)代表`Short`資料類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="30e77-115">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H0326S
```

## <a name="programming-tips"></a><span data-ttu-id="30e77-116">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="30e77-116">Programming tips</span></span>

-   <span data-ttu-id="30e77-117">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="30e77-117">**Widening.**</span></span> <span data-ttu-id="30e77-118">`Short`資料類型可擴展成`Integer`， `Long`， `Decimal`， `Single`，或`Double`。</span><span class="sxs-lookup"><span data-stu-id="30e77-118">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="30e77-119">這表示，您可以將 `Short` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="30e77-119">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="30e77-120">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="30e77-120">**Type Characters.**</span></span> <span data-ttu-id="30e77-121">將常值類型字元 `S` 附加到常值，會強制其成為 `Short` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="30e77-121">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="30e77-122">`Short`有任何識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="30e77-122">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="30e77-123">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="30e77-123">**Framework Type.**</span></span> <span data-ttu-id="30e77-124">在 .NET Framework 中對應的類型為 <xref:System.Int16?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="30e77-124">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e77-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="30e77-125">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="30e77-126">資料類型</span><span class="sxs-lookup"><span data-stu-id="30e77-126">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="30e77-127">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="30e77-127">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="30e77-128">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="30e77-128">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="30e77-129">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="30e77-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="30e77-130">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="30e77-130">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="30e77-131">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="30e77-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
