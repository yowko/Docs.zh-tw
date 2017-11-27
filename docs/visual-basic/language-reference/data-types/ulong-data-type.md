---
title: "ULong 資料類型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afc52bfd16541feed599d5445adad7aba04f8e9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="ce2ad-102">ULong 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce2ad-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="ce2ad-103">保存不帶正負號的 64 位元 （8 個位元組） 整數值範圍從 0 到 18446744073709551615 (超過 1.84 乘以 10 ^19)。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce2ad-104">備註</span><span class="sxs-lookup"><span data-stu-id="ce2ad-104">Remarks</span></span>

<span data-ttu-id="ce2ad-105">使用`ULong`資料類型可包含二進位資料太大， `UInteger`，或最大可能的不帶正負號的整數值。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>  
  
<span data-ttu-id="ce2ad-106">`ULong` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="ce2ad-107">常值的指派</span><span class="sxs-lookup"><span data-stu-id="ce2ad-107">Literal assignments</span></span>

<span data-ttu-id="ce2ad-108">您可以宣告和初始化`ULong`變數將其指派十進位常值、 十六進位常值、 八進位常值，或是 （從開始使用 Visual Basic 2017） 二進位常值。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ce2ad-109">如果整數常值超出 `ULong` 的範圍 (亦即，如果小於 <xref:System.UInt64.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ce2ad-110">在下列範例中，以十進位、十六進位和二進位常值表示的 7,934,076,125 整數，會指派給 `ULong` 值。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> <span data-ttu-id="ce2ad-111">使用前置詞`&h`或`&H`來表示十六進位常值前置詞`&b`或`&B`代表二進位常值，以及前置詞`&o`或`&O`代表八進位常值。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ce2ad-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ce2ad-113">從 Visual Basic 2017 開始，您也可以使用底線字元， `_`，當做數字分隔符號，以提升可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="ce2ad-114">數值常值也可以包含`UL`或`ul`[類型字元](../../programming-guide\language-features\data-types/type-characters.md)代表`ULong`資料類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-114">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="ce2ad-115">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="ce2ad-115">Programming tips</span></span>
  
-   <span data-ttu-id="ce2ad-116">**負的數字。**</span><span class="sxs-lookup"><span data-stu-id="ce2ad-116">**Negative Numbers.**</span></span> <span data-ttu-id="ce2ad-117">因為`ULong`是不帶正負號的類型，它無法表示為負數。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-117">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="ce2ad-118">如果您使用一元減號 (`-`) 運算子的運算式評估為輸入`ULong`，Visual Basic 會將轉換的運算式`Decimal`第一次。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-118">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>  
  
-   <span data-ttu-id="ce2ad-119">**Cls 符合性。**</span><span class="sxs-lookup"><span data-stu-id="ce2ad-119">**CLS Compliance.**</span></span> <span data-ttu-id="ce2ad-120">`ULong`資料類型不是屬於[Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) （cls） 標準，所以符合 CLS 標準的程式碼無法使用所使用的元件。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-120">The `ULong` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="ce2ad-121">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="ce2ad-121">**Interop Considerations.**</span></span> <span data-ttu-id="ce2ad-122">如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住，這類類型`ulong`在其他環境中可以有不同的資料寬度 （32 位元）。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="ce2ad-123">如果您要將 32 位元引數至這類元件，將它宣告為`UInteger`而不是`ULong`受管理的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-123">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>  
  
     <span data-ttu-id="ce2ad-124">此外，自動化不支援 Windows 95、 Windows 98、 Windows ME 或 Windows 2000 上 64 位元整數。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-124">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="ce2ad-125">您無法將 Visual Basic`ULong`至 Automation 元件在這些平台上的引數。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-125">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>  
  
-   <span data-ttu-id="ce2ad-126">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="ce2ad-126">**Widening.**</span></span> <span data-ttu-id="ce2ad-127">`ULong`資料類型可擴展成`Decimal`， `Single`，和`Double`。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-127">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="ce2ad-128">這表示您可以將轉換`ULong`而不會發生這些類型的任何<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-128">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="ce2ad-129">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="ce2ad-129">**Type Characters.**</span></span> <span data-ttu-id="ce2ad-130">將常值類型字元附加`UL`到常值會強制其成為`ULong`資料型別。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-130">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="ce2ad-131">`ULong`有任何識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-131">`ULong` has no identifier type character.</span></span>
  
-   <span data-ttu-id="ce2ad-132">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="ce2ad-132">**Framework Type.**</span></span> <span data-ttu-id="ce2ad-133">在 .NET Framework 中對應的類型為 <xref:System.UInt64?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="ce2ad-133">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2ad-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce2ad-134">See also</span></span>

 <xref:System.UInt64>  
 [<span data-ttu-id="ce2ad-135">資料類型</span><span class="sxs-lookup"><span data-stu-id="ce2ad-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="ce2ad-136">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="ce2ad-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="ce2ad-137">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="ce2ad-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="ce2ad-138">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="ce2ad-138">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="ce2ad-139">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="ce2ad-139">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
