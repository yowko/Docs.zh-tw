---
title: Short 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.Short
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
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400726"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="c15e3-102">短資料類型（視覺基本）</span><span class="sxs-lookup"><span data-stu-id="c15e3-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="c15e3-103">持有 16 位（2 位元組）整數，其值範圍從 -32，768 到 32，767。</span><span class="sxs-lookup"><span data-stu-id="c15e3-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c15e3-104">備註</span><span class="sxs-lookup"><span data-stu-id="c15e3-104">Remarks</span></span>  

 <span data-ttu-id="c15e3-105">使用`Short`資料類型包含不需要 的完整資料寬度的`Integer`整數值。</span><span class="sxs-lookup"><span data-stu-id="c15e3-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="c15e3-106">在某些情況下，通用語言運行時可以將`Short`變數緊密打包在一起並節省記憶體消耗。</span><span class="sxs-lookup"><span data-stu-id="c15e3-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="c15e3-107">`Short` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="c15e3-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="c15e3-108">文本分配</span><span class="sxs-lookup"><span data-stu-id="c15e3-108">Literal assignments</span></span>

<span data-ttu-id="c15e3-109">您可以通過為其分配十進位文本、`Short`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="c15e3-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="c15e3-110">如果整數常值超出 `Short` 的範圍 (亦即，如果小於 <xref:System.Int16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="c15e3-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="c15e3-111">在下面的示例中，等於 1，034 的整數表示為十進位、十六進位和二進位文本，從[整數](integer-data-type.md)隱式轉換為`Short`值。</span><span class="sxs-lookup"><span data-stu-id="c15e3-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="c15e3-112">`&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。</span><span class="sxs-lookup"><span data-stu-id="c15e3-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="c15e3-113">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="c15e3-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c15e3-114">從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="c15e3-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="c15e3-115">從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c15e3-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="c15e3-116">例如：</span><span class="sxs-lookup"><span data-stu-id="c15e3-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="c15e3-117">數位文本還可以包括`S`表示`Short`資料類型[的類型字元](../../programming-guide/language-features/data-types/type-characters.md)，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="c15e3-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="c15e3-118">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="c15e3-118">Programming tips</span></span>

- <span data-ttu-id="c15e3-119">**擴大。**</span><span class="sxs-lookup"><span data-stu-id="c15e3-119">**Widening.**</span></span> <span data-ttu-id="c15e3-120">資料類型`Short`擴展到`Integer` `Long`、、、、、`Decimal``Single`或`Double`。</span><span class="sxs-lookup"><span data-stu-id="c15e3-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="c15e3-121">這表示，您可以將 `Short` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c15e3-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="c15e3-122">**鍵入字元。**</span><span class="sxs-lookup"><span data-stu-id="c15e3-122">**Type Characters.**</span></span> <span data-ttu-id="c15e3-123">將常值類型字元 `S` 附加到常值，會強制其成為 `Short` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c15e3-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="c15e3-124">`Short`沒有識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="c15e3-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="c15e3-125">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="c15e3-125">**Framework Type.**</span></span> <span data-ttu-id="c15e3-126">在 .NET Framework 中對應的類型為 <xref:System.Int16?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="c15e3-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c15e3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c15e3-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="c15e3-128">資料類型</span><span class="sxs-lookup"><span data-stu-id="c15e3-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="c15e3-129">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="c15e3-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="c15e3-130">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="c15e3-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="c15e3-131">整數資料類型</span><span class="sxs-lookup"><span data-stu-id="c15e3-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="c15e3-132">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="c15e3-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="c15e3-133">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="c15e3-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
