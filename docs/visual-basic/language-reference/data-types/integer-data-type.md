---
title: Integer 資料類型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc780cc845bfa6ef52fc9973ef3617d621167af1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867068"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="c3fc3-102">Integer 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3fc3-102">Integer data type (Visual Basic)</span></span>
<span data-ttu-id="c3fc3-103">保存帶正負號的 32 位元 (4 位元組) 整數，值的範圍從 -2,147,483,648 到 2,147,483,647。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3fc3-104">備註</span><span class="sxs-lookup"><span data-stu-id="c3fc3-104">Remarks</span></span>
 <span data-ttu-id="c3fc3-105">`Integer` 資料類型可對 32 位元處理器提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="c3fc3-106">其他整數類資料類型在記憶體中載入和儲存的速度較慢。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="c3fc3-107">`Integer` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="c3fc3-108">常值的指派</span><span class="sxs-lookup"><span data-stu-id="c3fc3-108">Literal assignments</span></span>

<span data-ttu-id="c3fc3-109">您可以宣告並初始化`Integer`變數指派十進位常值、 十六進位常值、 八進位的常值，或 （Visual Basic 2017 年起） 二進位常值。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="c3fc3-110">如果整數常值超出 `Integer` 的範圍 (亦即，如果小於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="c3fc3-111">在下列範例中，如果整數等於 16,342，即表示 `Integer` 值指派了十進位、十六進位和二進位常值。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-111">In the following example, integers equal to 16,342 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="c3fc3-112">使用前置詞`&h`或是`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位的常值。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="c3fc3-113">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c3fc3-114">從 Visual Basic 2017 開始，您也可以使用底線字元`_`，作為數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="c3fc3-115">從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 作為前置分隔符號之間的前置詞和十六進位、 二進位或八進位數字。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="c3fc3-116">例如: </span><span class="sxs-lookup"><span data-stu-id="c3fc3-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="c3fc3-117">也可以包含數值常值`I`[型別字元](../../programming-guide\language-features\data-types/type-characters.md)表示`Integer`資料型別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-117">Numeric literals can also include the `I` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="c3fc3-118">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="c3fc3-118">Programming tips</span></span>

-   <span data-ttu-id="c3fc3-119">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="c3fc3-119">**Interop Considerations.**</span></span> <span data-ttu-id="c3fc3-120">如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住，`Integer`在其他環境中有不同的資料寬度 （16 位元）。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="c3fc3-121">如果您要將 16 位元引數傳遞至這類元件，請在新的 Visual Basic 程式碼中將它宣告為 `Short`，而不是 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="c3fc3-122">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="c3fc3-122">**Widening.**</span></span> <span data-ttu-id="c3fc3-123">`Integer` 資料類型可擴展為 `Long`、`Decimal`、`Single` 或 `Double`。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="c3fc3-124">這表示，您可以將 `Integer` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="c3fc3-125">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="c3fc3-125">**Type Characters.**</span></span> <span data-ttu-id="c3fc3-126">將常值類型字元 `I` 附加到常值，會強制其成為 `Integer` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="c3fc3-127">將識別項類型字元 `%` 附加到任何識別項，會強制其成為 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
-   <span data-ttu-id="c3fc3-128">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="c3fc3-128">**Framework Type.**</span></span> <span data-ttu-id="c3fc3-129">在 .NET Framework 中對應的類型為 <xref:System.Int32?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="c3fc3-130">範圍</span><span class="sxs-lookup"><span data-stu-id="c3fc3-130">Range</span></span>

<span data-ttu-id="c3fc3-131">如果您嘗試將整數類資料類型的變數設定為超出該類型範圍的數字，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="c3fc3-132">如果您嘗試將它設定為分數，則數字就會四捨五入為最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="c3fc3-133">如果數字與兩個整數值同樣接近，則該直將會四捨五入為最接近的雙數。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="c3fc3-134">這種行為會將一致四捨五入單向中點值得出的四捨五入錯誤降至最低。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="c3fc3-135">下列程式碼將示範四捨五入的範例。</span><span class="sxs-lookup"><span data-stu-id="c3fc3-135">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="c3fc3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3fc3-136">See also</span></span>

<xref:System.Int32?displayProperty=nameWithType>   
 [<span data-ttu-id="c3fc3-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="c3fc3-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="c3fc3-138">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="c3fc3-138">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="c3fc3-139">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="c3fc3-139">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="c3fc3-140">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="c3fc3-140">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="c3fc3-141">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="c3fc3-141">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="c3fc3-142">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="c3fc3-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
