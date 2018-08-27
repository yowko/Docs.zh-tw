---
title: Char 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 09b0162068bc068bd77612816626897ec4a151d9
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911963"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="542f3-102">Char 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="542f3-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="542f3-103">保存不帶正負號的 16 位元 （2 個位元組） 字碼指標值範圍從 0 到 65535。</span><span class="sxs-lookup"><span data-stu-id="542f3-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="542f3-104">每個*字碼指標*，或字元碼表示單一 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="542f3-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="542f3-105">備註</span><span class="sxs-lookup"><span data-stu-id="542f3-105">Remarks</span></span>  
 <span data-ttu-id="542f3-106">使用`Char`資料類型，當您需要保留只會有一個字元，且不需要的額外負荷`String`。</span><span class="sxs-lookup"><span data-stu-id="542f3-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="542f3-107">在某些情況下，您可以使用`Char()`，陣列`Char`項目，來保留多個字元。</span><span class="sxs-lookup"><span data-stu-id="542f3-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="542f3-108">預設值`Char`是為 0 之字碼指標的字元。</span><span class="sxs-lookup"><span data-stu-id="542f3-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="542f3-109">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="542f3-109">Unicode Characters</span></span>  
 <span data-ttu-id="542f3-110">Unicode 的前 128 個字碼指標 (0-127) 對應至的字母和美式標準鍵盤上的符號。</span><span class="sxs-lookup"><span data-stu-id="542f3-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="542f3-111">這些第 128 個字碼指標都會與 ASCII 字元集定義相同。</span><span class="sxs-lookup"><span data-stu-id="542f3-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="542f3-112">第二個 128 個字碼指標 (128-255) 代表特殊字元，例如拉丁文字母、 腔調字、 貨幣符號和分數。</span><span class="sxs-lookup"><span data-stu-id="542f3-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="542f3-113">Unicode 會使用其餘的字碼指標 (256-65535) 的各種不同的符號，包括全球文字字元、 變音符號和數學和技術的符號。</span><span class="sxs-lookup"><span data-stu-id="542f3-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="542f3-114">您可以使用類似的方法<xref:System.Char.IsDigit%2A>並<xref:System.Char.IsPunctuation%2A>上`Char`變數，以判斷其 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="542f3-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="542f3-115">類型轉換</span><span class="sxs-lookup"><span data-stu-id="542f3-115">Type Conversions</span></span>  
 <span data-ttu-id="542f3-116">Visual Basic 不會直接之間轉換`Char`和數字的類型。</span><span class="sxs-lookup"><span data-stu-id="542f3-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="542f3-117">您可以使用<xref:Microsoft.VisualBasic.Strings.Asc%2A>或是<xref:Microsoft.VisualBasic.Strings.AscW%2A>函式來轉換`Char`值`Integer`表示其字碼指標。</span><span class="sxs-lookup"><span data-stu-id="542f3-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="542f3-118">您可以使用<xref:Microsoft.VisualBasic.Strings.Chr%2A>或是<xref:Microsoft.VisualBasic.Strings.ChrW%2A>函式來轉換`Integer`值`Char`具有該字碼指標。</span><span class="sxs-lookup"><span data-stu-id="542f3-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="542f3-119">如果類型檢查參數 ([Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)) 時，您必須將常值類型字元附加至單一字元字串常值，指出它為`Char`資料型別。</span><span class="sxs-lookup"><span data-stu-id="542f3-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="542f3-120">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="542f3-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="542f3-121">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="542f3-121">Programming Tips</span></span>  
  
-   <span data-ttu-id="542f3-122">**負數的數字。**</span><span class="sxs-lookup"><span data-stu-id="542f3-122">**Negative Numbers.**</span></span> <span data-ttu-id="542f3-123">`Char` 是不帶正負號的類型，無法表示為負數值。</span><span class="sxs-lookup"><span data-stu-id="542f3-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="542f3-124">在任何情況下，您不應該使用`Char`來保存數字值。</span><span class="sxs-lookup"><span data-stu-id="542f3-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="542f3-125">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="542f3-125">**Interop Considerations.**</span></span> <span data-ttu-id="542f3-126">如果您不是針對.NET Framework 中，撰寫的元件介面例如 Automation 或 COM 物件，請記住，字元類型有不同的資料寬度 （8 位元） 在其他環境中。</span><span class="sxs-lookup"><span data-stu-id="542f3-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="542f3-127">如果您將 8 位元引數傳遞給這類元件時，將它宣告為`Byte`而不是`Char`中新的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="542f3-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="542f3-128">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="542f3-128">**Widening.**</span></span> <span data-ttu-id="542f3-129">`Char`資料類型可擴展為`String`。</span><span class="sxs-lookup"><span data-stu-id="542f3-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="542f3-130">這表示您可以將轉換`Char`要`String`並不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="542f3-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="542f3-131">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="542f3-131">**Type Characters.**</span></span> <span data-ttu-id="542f3-132">附加的常值類型字元`C`為單一字元字串常值會強制其成為`Char`資料型別。</span><span class="sxs-lookup"><span data-stu-id="542f3-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="542f3-133">`Char` 有任何識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="542f3-133">`Char` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="542f3-134">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="542f3-134">**Framework Type.**</span></span> <span data-ttu-id="542f3-135">在 .NET Framework 中對應的類型為 <xref:System.Char?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="542f3-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542f3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="542f3-136">See Also</span></span>  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="542f3-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="542f3-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="542f3-138">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="542f3-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="542f3-139">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="542f3-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="542f3-140">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="542f3-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="542f3-141">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="542f3-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="542f3-142">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="542f3-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
