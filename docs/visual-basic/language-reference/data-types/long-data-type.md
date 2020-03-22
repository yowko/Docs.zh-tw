---
title: Long 資料類型
ms.date: 01/31/2018
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
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400810"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="9b694-102">長資料類型（可視基本）</span><span class="sxs-lookup"><span data-stu-id="9b694-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="9b694-103">持有已簽名的 64 位（8 位元組）整數，價值範圍為 -9，223，372，036，854，775，808 到 9，223，372，036，854，775，807 （9.2...E=18）。</span><span class="sxs-lookup"><span data-stu-id="9b694-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="9b694-104">備註</span><span class="sxs-lookup"><span data-stu-id="9b694-104">Remarks</span></span>

<span data-ttu-id="9b694-105">使用`Long`資料類型包含太大而不適合資料類型的`Integer`整數。</span><span class="sxs-lookup"><span data-stu-id="9b694-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="9b694-106">`Long` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="9b694-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="9b694-107">文本分配</span><span class="sxs-lookup"><span data-stu-id="9b694-107">Literal assignments</span></span>

<span data-ttu-id="9b694-108">您可以通過為其分配十進位文本、`Long`十六進位文本、八進位文本或（從 Visual Basic 2017 開頭）二進位文本來聲明和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="9b694-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="9b694-109">如果整數常值超出 `Long` 的範圍 (亦即，如果小於 <xref:System.Int64.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Int64.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b694-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="9b694-110">在下列範例中，如果整數等於 4,294,967,296，即表示 `Long` 值指派了十進位、十六進位和二進位常值。</span><span class="sxs-lookup"><span data-stu-id="9b694-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="9b694-111">`&h`您可以使用首碼或`&H`表示十六進位文本、首碼`&b`或`&B`表示二進位文本和首碼`&o`或`&O`表示八進位文本。</span><span class="sxs-lookup"><span data-stu-id="9b694-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="9b694-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="9b694-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="9b694-113">從 Visual Basic 2017 開始，您還可以使用底線`_`字元 ，作為數位分隔符號來增強可讀性，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="9b694-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="9b694-114">從 Visual Basic 15.5 開始，您還可以使用底線`_`字元 （ ） 作為首碼和十六進位、二進位或八進位數位之間的前導分隔符號。</span><span class="sxs-lookup"><span data-stu-id="9b694-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="9b694-115">例如：</span><span class="sxs-lookup"><span data-stu-id="9b694-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="9b694-116">數位文本還可以包括`L`表示`Long`資料類型[的類型字元](../../programming-guide/language-features/data-types/type-characters.md)，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="9b694-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="9b694-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="9b694-117">Programming tips</span></span>

- <span data-ttu-id="9b694-118">**Interop 考量：**</span><span class="sxs-lookup"><span data-stu-id="9b694-118">**Interop Considerations.**</span></span> <span data-ttu-id="9b694-119">如果要與未為 .NET 框架編寫的元件（例如自動化或 COM 物件）介面，請記住，`Long`在其他環境中具有不同的資料寬度（32 位）。</span><span class="sxs-lookup"><span data-stu-id="9b694-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="9b694-120">如果要將 32 位參數傳遞給此類元件，請將其聲明為`Integer`而不是在新的 Visual `Long` Basic 代碼中。</span><span class="sxs-lookup"><span data-stu-id="9b694-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="9b694-121">**擴大。**</span><span class="sxs-lookup"><span data-stu-id="9b694-121">**Widening.**</span></span> <span data-ttu-id="9b694-122">資料類型`Long`擴展到`Decimal`或`Single`。 `Double`</span><span class="sxs-lookup"><span data-stu-id="9b694-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="9b694-123">這表示，您可以將 `Long` 轉換成這些類型的任何一種，而不會發生 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b694-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="9b694-124">**鍵入字元。**</span><span class="sxs-lookup"><span data-stu-id="9b694-124">**Type Characters.**</span></span> <span data-ttu-id="9b694-125">將常值類型字元 `L` 附加到常值，會強制其成為 `Long` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="9b694-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="9b694-126">將識別項類型字元 `&` 附加到任何識別項，會強制其成為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="9b694-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="9b694-127">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="9b694-127">**Framework Type.**</span></span> <span data-ttu-id="9b694-128">在 .NET Framework 中對應的類型為 <xref:System.Int64?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="9b694-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b694-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b694-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="9b694-130">資料類型</span><span class="sxs-lookup"><span data-stu-id="9b694-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="9b694-131">整數資料類型</span><span class="sxs-lookup"><span data-stu-id="9b694-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="9b694-132">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="9b694-132">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="9b694-133">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="9b694-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="9b694-134">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="9b694-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="9b694-135">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="9b694-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
