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
ms.openlocfilehash: e672402535215ca30d19cc480e39b42b0364f137
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590802"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="779fa-102">Char 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="779fa-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="779fa-103">保存不帶正負號的 16 位元 （2 個位元組） 字碼指標值範圍從 0 到 65535 之間。</span><span class="sxs-lookup"><span data-stu-id="779fa-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="779fa-104">每個*程式碼點*，或字元碼，表示單一 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="779fa-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="779fa-105">備註</span><span class="sxs-lookup"><span data-stu-id="779fa-105">Remarks</span></span>  
 <span data-ttu-id="779fa-106">使用`Char`資料類型，當您需要保存只有一個字元，而且不需要的額外負荷`String`。</span><span class="sxs-lookup"><span data-stu-id="779fa-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="779fa-107">在某些情況下，您可以使用`Char()`，陣列`Char`項目，來保留多個字元。</span><span class="sxs-lookup"><span data-stu-id="779fa-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="779fa-108">預設值`Char`是與字碼指標為 0 的字元。</span><span class="sxs-lookup"><span data-stu-id="779fa-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="779fa-109">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="779fa-109">Unicode Characters</span></span>  
 <span data-ttu-id="779fa-110">Unicode 的第一個 128 個字碼指標 (0-127) 對應至的字母和標準美國鍵盤上的符號。</span><span class="sxs-lookup"><span data-stu-id="779fa-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="779fa-111">這些第一個 128 個字碼指標是相同 ASCII 字元集所定義。</span><span class="sxs-lookup"><span data-stu-id="779fa-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="779fa-112">第二個 128 個字碼指標 (128-255) 代表特殊字元，例如拉丁文字母字元、 重音符號、 貨幣符號和分數。</span><span class="sxs-lookup"><span data-stu-id="779fa-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="779fa-113">Unicode 會使用各種不同的符號，包括全球文字字元、 變音符號和數學和技術符號剩餘的字碼指標 (256-65535)。</span><span class="sxs-lookup"><span data-stu-id="779fa-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="779fa-114">您可以使用類似的方法<xref:System.Char.IsDigit%2A>和<xref:System.Char.IsPunctuation%2A>上`Char`變數，以判斷其 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="779fa-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="779fa-115">類型轉換</span><span class="sxs-lookup"><span data-stu-id="779fa-115">Type Conversions</span></span>  
 <span data-ttu-id="779fa-116">Visual Basic 不會直接之間轉換`Char`和數字類型。</span><span class="sxs-lookup"><span data-stu-id="779fa-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="779fa-117">您可以使用<xref:Microsoft.VisualBasic.Strings.Asc%2A>或<xref:Microsoft.VisualBasic.Strings.AscW%2A>函式將轉換`Char`值設定為`Integer`表示其字碼指標。</span><span class="sxs-lookup"><span data-stu-id="779fa-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="779fa-118">您可以使用<xref:Microsoft.VisualBasic.Strings.Chr%2A>或<xref:Microsoft.VisualBasic.Strings.ChrW%2A>函式將轉換`Integer`值設定為`Char`具有該字碼指標。</span><span class="sxs-lookup"><span data-stu-id="779fa-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="779fa-119">如果類型檢查參數 ([Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)) 已開啟，您必須將常值類型字元附加至單一字元字串常值，以便將它做為識別`Char`資料型別。</span><span class="sxs-lookup"><span data-stu-id="779fa-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="779fa-120">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="779fa-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="779fa-121">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="779fa-121">Programming Tips</span></span>  
  
-   <span data-ttu-id="779fa-122">**負的數字。**</span><span class="sxs-lookup"><span data-stu-id="779fa-122">**Negative Numbers.**</span></span> <span data-ttu-id="779fa-123">`Char` 是不帶正負號的類型，因此無法表示負數值。</span><span class="sxs-lookup"><span data-stu-id="779fa-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="779fa-124">在任何情況下，您不應該使用`Char`來保存數值。</span><span class="sxs-lookup"><span data-stu-id="779fa-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="779fa-125">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="779fa-125">**Interop Considerations.**</span></span> <span data-ttu-id="779fa-126">如果您正在使用不是針對.NET Framework 中，撰寫的元件例如 Automation 或 COM 物件，請記得字元類型具有不同資料寬度 （8 位元） 在其他環境中。</span><span class="sxs-lookup"><span data-stu-id="779fa-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="779fa-127">如果您將 8 位元引數傳遞至這類元件時，將它宣告為`Byte`而不是`Char`新的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="779fa-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="779fa-128">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="779fa-128">**Widening.**</span></span> <span data-ttu-id="779fa-129">`Char`資料類型可擴展成`String`。</span><span class="sxs-lookup"><span data-stu-id="779fa-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="779fa-130">這表示您可以將轉換`Char`至`String`並不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="779fa-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="779fa-131">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="779fa-131">**Type Characters.**</span></span> <span data-ttu-id="779fa-132">將常值類型字元附加`C`為單一字元字串常值會強制其成為`Char`資料型別。</span><span class="sxs-lookup"><span data-stu-id="779fa-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="779fa-133">`Char` 有任何識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="779fa-133">`Char` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="779fa-134">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="779fa-134">**Framework Type.**</span></span> <span data-ttu-id="779fa-135">在 .NET Framework 中對應的類型為 <xref:System.Char?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="779fa-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="779fa-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="779fa-136">See Also</span></span>  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="779fa-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="779fa-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="779fa-138">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="779fa-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="779fa-139">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="779fa-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="779fa-140">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="779fa-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="779fa-141">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="779fa-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="779fa-142">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="779fa-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
