---
title: UInteger 資料類型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: a79162c6171c764d4c4610fd10f14a5dac6ff1a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498995"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="f58bf-102">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="f58bf-102">UInteger data type</span></span>

<span data-ttu-id="f58bf-103">保存不帶正負號的 32 位元 （4 個位元組） 整數，範圍從 0 到 4,294,967,295。</span><span class="sxs-lookup"><span data-stu-id="f58bf-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f58bf-104">備註</span><span class="sxs-lookup"><span data-stu-id="f58bf-104">Remarks</span></span>

 <span data-ttu-id="f58bf-105">`UInteger`資料類型提供的不帶正負號的最大值，最有效率的資料寬度。</span><span class="sxs-lookup"><span data-stu-id="f58bf-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="f58bf-106">`UInteger` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="f58bf-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="f58bf-107">常值的指派</span><span class="sxs-lookup"><span data-stu-id="f58bf-107">Literal assignments</span></span>

<span data-ttu-id="f58bf-108">您可以宣告並初始化`UInteger`變數指派十進位常值、 十六進位常值、 八進位的常值，或 （Visual Basic 2017 年起） 二進位常值。</span><span class="sxs-lookup"><span data-stu-id="f58bf-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="f58bf-109">如果整數常值超出 `UInteger` 的範圍 (亦即，如果小於 <xref:System.UInt32.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="f58bf-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="f58bf-110">在下列範例中，以十進位、十六進位和二進位常值表示的 3,000,000,000 整數，會指派給 `UInteger` 值。</span><span class="sxs-lookup"><span data-stu-id="f58bf-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="f58bf-111">使用前置詞`&h`或是`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位的常值。</span><span class="sxs-lookup"><span data-stu-id="f58bf-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="f58bf-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="f58bf-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="f58bf-113">從 Visual Basic 2017 開始，您也可以使用底線字元`_`，作為數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f58bf-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="f58bf-114">從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 作為前置分隔符號之間的前置詞和十六進位、 二進位或八進位數字。</span><span class="sxs-lookup"><span data-stu-id="f58bf-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="f58bf-115">例如: </span><span class="sxs-lookup"><span data-stu-id="f58bf-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="f58bf-116">也可以包含數值常值`UI`或是`ui`[型別字元](../../programming-guide/language-features/data-types/type-characters.md)表示`UInteger`資料型別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f58bf-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="f58bf-117">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="f58bf-117">Programming tips</span></span>

 <span data-ttu-id="f58bf-118">`UInteger`並`Integer`資料類型提供最佳效能 32 位元的處理器，因為較小的整數類型 (`UShort`， `Short`， `Byte`，和`SByte`)，即使他們使用較少的位元，需要更多時間載入、 儲存和擷取。</span><span class="sxs-lookup"><span data-stu-id="f58bf-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
-   <span data-ttu-id="f58bf-119">**負數的數字。**</span><span class="sxs-lookup"><span data-stu-id="f58bf-119">**Negative Numbers.**</span></span> <span data-ttu-id="f58bf-120">因為`UInteger`是不帶正負號的型別，它無法表示負數。</span><span class="sxs-lookup"><span data-stu-id="f58bf-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="f58bf-121">如果您使用一元減號 (`-`) 運算子的運算式，評估為類型`UInteger`，Visual Basic 會將轉換的運算式`Long`第一次。</span><span class="sxs-lookup"><span data-stu-id="f58bf-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
-   <span data-ttu-id="f58bf-122">**CLS 合規性。**</span><span class="sxs-lookup"><span data-stu-id="f58bf-122">**CLS Compliance.**</span></span> <span data-ttu-id="f58bf-123">`UInteger`資料類型不是屬於[Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) （cls） 標準，所以符合 CLS 標準的程式碼無法取用使用它的元件。</span><span class="sxs-lookup"><span data-stu-id="f58bf-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="f58bf-124">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="f58bf-124">**Interop Considerations.**</span></span> <span data-ttu-id="f58bf-125">如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住，這類類型`uint`在其他環境中可以有不同的資料寬度 （16 位元）。</span><span class="sxs-lookup"><span data-stu-id="f58bf-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="f58bf-126">如果您將 16 位元引數傳遞給這類元件，將它宣告為`UShort`而不是`UInteger`中受管理的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f58bf-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
-   <span data-ttu-id="f58bf-127">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="f58bf-127">**Widening.**</span></span> <span data-ttu-id="f58bf-128">`UInteger`資料類型可擴展為`Long`， `ULong`， `Decimal`， `Single`，和`Double`。</span><span class="sxs-lookup"><span data-stu-id="f58bf-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="f58bf-129">這表示您可以將轉換`UInteger`任何一種類型，而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f58bf-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="f58bf-130">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="f58bf-130">**Type Characters.**</span></span> <span data-ttu-id="f58bf-131">將常值類型字元附加`UI`成常值會強制其成為`UInteger`資料型別。</span><span class="sxs-lookup"><span data-stu-id="f58bf-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="f58bf-132">`UInteger` 有任何識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="f58bf-132">`UInteger` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="f58bf-133">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="f58bf-133">**Framework Type.**</span></span> <span data-ttu-id="f58bf-134">在 .NET Framework 中對應的類型為 <xref:System.UInt32?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="f58bf-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f58bf-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f58bf-135">See also</span></span>
- <xref:System.UInt32>
- [<span data-ttu-id="f58bf-136">資料類型</span><span class="sxs-lookup"><span data-stu-id="f58bf-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f58bf-137">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="f58bf-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f58bf-138">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="f58bf-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="f58bf-139">如何：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="f58bf-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="f58bf-140">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="f58bf-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
