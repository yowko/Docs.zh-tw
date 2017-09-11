---
title: "字串資料類型 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.String
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings, string data type
- literals, string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals
- data types [Visual Basic], assigning
- String literals
- identifier type characters, $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5d7a4272169ae7b2749d038e1116818d2cfbad95
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="756de-102">String 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="756de-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="756de-103">保存不帶正負號的 16 位元 （2 個位元組） 字碼指標順序該範圍從 0 到 65535 的值。</span><span class="sxs-lookup"><span data-stu-id="756de-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="756de-104">每個*程式碼點*，或字元的代碼，表示單一 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="756de-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="756de-105">字串可以包含從 0 到約二十億 (2 ^31) 的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="756de-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="756de-106">備註</span><span class="sxs-lookup"><span data-stu-id="756de-106">Remarks</span></span>  
 <span data-ttu-id="756de-107">使用`String`資料型別來存放多個字元的陣列管理負擔不`Char()`，陣列`Char`項目。</span><span class="sxs-lookup"><span data-stu-id="756de-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="756de-108">預設值的`String`是`Nothing`（null 參考）。</span><span class="sxs-lookup"><span data-stu-id="756de-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="756de-109">請注意，這是不相同則為空字串 (值`""`)。</span><span class="sxs-lookup"><span data-stu-id="756de-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="756de-110">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="756de-110">Unicode Characters</span></span>  
 <span data-ttu-id="756de-111">Unicode 的前 128 個字碼指標 (0-127) 對應至的字母和標準美式鍵盤上的符號。</span><span class="sxs-lookup"><span data-stu-id="756de-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="756de-112">這些第 128 個字碼指標是所定義的 ASCII 字元集的相同。</span><span class="sxs-lookup"><span data-stu-id="756de-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="756de-113">第二個 128 個字碼指標 (128-255) 代表特殊字元，例如拉丁文字母、 腔調字、 貨幣符號和句號。</span><span class="sxs-lookup"><span data-stu-id="756de-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="756de-114">Unicode 使用其餘的字碼指標 (256-65535) 的各種不同的符號。</span><span class="sxs-lookup"><span data-stu-id="756de-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="756de-115">這包括各國文字字元、 變音符號以及數學和技術的符號。</span><span class="sxs-lookup"><span data-stu-id="756de-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="756de-116">您可以使用的方法，例如<xref:System.Char.IsDigit%2A>和<xref:System.Char.IsPunctuation%2A>上中的個別字元`String`變數，以判斷其 Unicode 分類。</xref:System.Char.IsPunctuation%2A> </xref:System.Char.IsDigit%2A></span><span class="sxs-lookup"><span data-stu-id="756de-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="756de-117">格式需求</span><span class="sxs-lookup"><span data-stu-id="756de-117">Format Requirements</span></span>  
 <span data-ttu-id="756de-118">您必須將`String`常值雙引號 (`" "`)。</span><span class="sxs-lookup"><span data-stu-id="756de-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="756de-119">如果您必須為一個字元字串中包含引號，則會使用兩個雙引號 (`""`)。</span><span class="sxs-lookup"><span data-stu-id="756de-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="756de-120">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="756de-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="756de-121">請注意連續引號表示字串中的引號無關的開頭和結尾引號`String`常值。</span><span class="sxs-lookup"><span data-stu-id="756de-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="756de-122">字串操作</span><span class="sxs-lookup"><span data-stu-id="756de-122">String Manipulations</span></span>  
 <span data-ttu-id="756de-123">一旦指派字串給`String`變數時，該字串是*變*，這表示您無法變更其長度或內容。</span><span class="sxs-lookup"><span data-stu-id="756de-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="756de-124">當您改變任何方式的字串時，Visual Basic 來建立新的字串和放棄前一個。</span><span class="sxs-lookup"><span data-stu-id="756de-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="756de-125">`String`變數接著會指向新的字串。</span><span class="sxs-lookup"><span data-stu-id="756de-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="756de-126">您可以管理的內容`String`變數使用各種不同的字串函式。</span><span class="sxs-lookup"><span data-stu-id="756de-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="756de-127">下列範例說明<xref:Microsoft.VisualBasic.Strings.Left%2A>函式</xref:Microsoft.VisualBasic.Strings.Left%2A></span><span class="sxs-lookup"><span data-stu-id="756de-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="756de-128">另一個元件所建立的字串可能會填補前置或尾端空格。</span><span class="sxs-lookup"><span data-stu-id="756de-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="756de-129">如果您收到此類字串，您可以使用<xref:Microsoft.VisualBasic.Strings.Trim%2A>， <xref:Microsoft.VisualBasic.Strings.LTrim%2A>，和<xref:Microsoft.VisualBasic.Strings.RTrim%2A>函式來移除這些空格。</xref:Microsoft.VisualBasic.Strings.RTrim%2A> </xref:Microsoft.VisualBasic.Strings.LTrim%2A> </xref:Microsoft.VisualBasic.Strings.Trim%2A></span><span class="sxs-lookup"><span data-stu-id="756de-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="756de-130">如需字串操作的詳細資訊，請參閱[字串](../../../visual-basic/programming-guide/language-features/strings/index.md)。</span><span class="sxs-lookup"><span data-stu-id="756de-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="756de-131">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="756de-131">Programming Tips</span></span>  
  
-   <span data-ttu-id="756de-132">**負的數字。**</span><span class="sxs-lookup"><span data-stu-id="756de-132">**Negative Numbers.**</span></span> <span data-ttu-id="756de-133">請記住所持有的字元`String`是不帶正負號和不能代表負數值。</span><span class="sxs-lookup"><span data-stu-id="756de-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="756de-134">在任何情況下，您不應該使用`String`來保存數值。</span><span class="sxs-lookup"><span data-stu-id="756de-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="756de-135">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="756de-135">**Interop Considerations.**</span></span> <span data-ttu-id="756de-136">如果您要使用的元件不是撰寫.NET framework 中，例如 Automation 或 COM 物件，請記得字串字元具有不同的資料寬度 （8 位元） 在其他環境中。</span><span class="sxs-lookup"><span data-stu-id="756de-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="756de-137">如果您要將 8 位元的字元字串引數傳遞至這類元件，將它宣告為`Byte()`，陣列`Byte`項目，而不是`String`新的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="756de-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="756de-138">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="756de-138">**Type Characters.**</span></span> <span data-ttu-id="756de-139">將識別項類型字元附加`$`到任何識別項會強制其成為`String`資料型別。</span><span class="sxs-lookup"><span data-stu-id="756de-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="756de-140">`String`有任何常值類型的字元。</span><span class="sxs-lookup"><span data-stu-id="756de-140">`String` has no literal type character.</span></span> <span data-ttu-id="756de-141">不過，編譯器會以引號括住的常值 (`" "`) 做為`String`。</span><span class="sxs-lookup"><span data-stu-id="756de-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
-   <span data-ttu-id="756de-142">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="756de-142">**Framework Type.**</span></span> <span data-ttu-id="756de-143">.NET Framework 中對應的類型是<xref:System.String?displayProperty=fullName>類別。</xref:System.String?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="756de-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=fullName> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756de-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="756de-144">See Also</span></span>  
 <span data-ttu-id="756de-145"><xref:System.String?displayProperty=fullName></xref:System.String?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="756de-145"><xref:System.String?displayProperty=fullName></span></span>   
<span data-ttu-id="756de-146"> [資料型別](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="756de-146"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="756de-147"> [Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="756de-147"> [Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md) </span></span>  
<span data-ttu-id="756de-148"> [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="756de-148"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="756de-149"> [轉換的摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="756de-149"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="756de-150"> [如何︰ 呼叫 Windows 函式會採用不帶正負號的類型](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span><span class="sxs-lookup"><span data-stu-id="756de-150"> [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span></span>  
<span data-ttu-id="756de-151"> [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="756de-151"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>

