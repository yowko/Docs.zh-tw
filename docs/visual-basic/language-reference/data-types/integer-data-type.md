---
title: Integer 資料類型
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
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400733"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="a170c-102">整數資料類型（可視基本）</span><span class="sxs-lookup"><span data-stu-id="a170c-102">Integer data type (Visual Basic)</span></span>

<span data-ttu-id="a170c-103">保存帶正負號的 32 位元 (4 位元組) 整數，值的範圍從 -2,147,483,648 到 2,147,483,647。</span><span class="sxs-lookup"><span data-stu-id="a170c-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a170c-104">備註</span><span class="sxs-lookup"><span data-stu-id="a170c-104">Remarks</span></span>

 <span data-ttu-id="a170c-105">`Integer` 資料類型可對 32 位元處理器提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="a170c-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="a170c-106">其他整數類資料類型在記憶體中載入和儲存的速度較慢。</span><span class="sxs-lookup"><span data-stu-id="a170c-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="a170c-107">`Integer` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="a170c-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="a170c-108">文本分配</span><span class="sxs-lookup"><span data-stu-id="a170c-108">Literal assignments</span></span>

<span data-ttu-id="a170c-109">您可以通過為其分配十進位文本、`Integer`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="a170c-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="a170c-110">如果整數常值超出 `Integer` 的範圍 (亦即，如果小於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="a170c-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="a170c-111">在下列範例中，以十進位、十六進位和二進位常值表示的 90,946 整數，會指派給 `Integer` 值。</span><span class="sxs-lookup"><span data-stu-id="a170c-111">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="a170c-112">`&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。</span><span class="sxs-lookup"><span data-stu-id="a170c-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="a170c-113">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="a170c-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="a170c-114">從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="a170c-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="a170c-115">從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a170c-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="a170c-116">例如：</span><span class="sxs-lookup"><span data-stu-id="a170c-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="a170c-117">數位文本還可以包括`I`表示`Integer`資料類型[的類型字元](../../programming-guide/language-features/data-types/type-characters.md)，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="a170c-117">Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="a170c-118">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="a170c-118">Programming tips</span></span>

- <span data-ttu-id="a170c-119">**Interop 考量：**</span><span class="sxs-lookup"><span data-stu-id="a170c-119">**Interop Considerations.**</span></span> <span data-ttu-id="a170c-120">如果要與未為 .NET 框架編寫的元件（如自動化或 COM 物件）介面，請記住，`Integer`在其他環境中具有不同的資料寬度（16 位）。</span><span class="sxs-lookup"><span data-stu-id="a170c-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="a170c-121">如果您要將 16 位元引數傳遞至這類元件，請在新的 Visual Basic 程式碼中將它宣告為 `Short`，而不是 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="a170c-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="a170c-122">**擴大。**</span><span class="sxs-lookup"><span data-stu-id="a170c-122">**Widening.**</span></span> <span data-ttu-id="a170c-123">`Integer` 資料類型可擴展為 `Long`、`Decimal`、`Single` 或 `Double`。</span><span class="sxs-lookup"><span data-stu-id="a170c-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="a170c-124">這表示，您可以將 `Integer` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="a170c-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="a170c-125">**鍵入字元。**</span><span class="sxs-lookup"><span data-stu-id="a170c-125">**Type Characters.**</span></span> <span data-ttu-id="a170c-126">將常值類型字元 `I` 附加到常值，會強制其成為 `Integer` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="a170c-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="a170c-127">將識別項類型字元 `%` 附加到任何識別項，會強制其成為 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="a170c-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
- <span data-ttu-id="a170c-128">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="a170c-128">**Framework Type.**</span></span> <span data-ttu-id="a170c-129">在 .NET Framework 中對應的類型為 <xref:System.Int32?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="a170c-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="a170c-130">範圍</span><span class="sxs-lookup"><span data-stu-id="a170c-130">Range</span></span>

<span data-ttu-id="a170c-131">如果您嘗試將整數類資料類型的變數設定為超出該類型範圍的數字，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a170c-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="a170c-132">如果您嘗試將它設定為分數，則數字就會四捨五入為最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="a170c-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="a170c-133">如果數字與兩個整數值同樣接近，則該直將會四捨五入為最接近的雙數。</span><span class="sxs-lookup"><span data-stu-id="a170c-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="a170c-134">這種行為會將一致四捨五入單向中點值得出的四捨五入錯誤降至最低。</span><span class="sxs-lookup"><span data-stu-id="a170c-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="a170c-135">下列程式碼將示範四捨五入的範例。</span><span class="sxs-lookup"><span data-stu-id="a170c-135">The following code shows examples of rounding.</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="a170c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a170c-136">See also</span></span>

- <xref:System.Int32?displayProperty=nameWithType>
- [<span data-ttu-id="a170c-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="a170c-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a170c-138">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="a170c-138">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="a170c-139">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="a170c-139">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="a170c-140">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="a170c-140">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a170c-141">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="a170c-141">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="a170c-142">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="a170c-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
