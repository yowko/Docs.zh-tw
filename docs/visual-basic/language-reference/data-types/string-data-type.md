---
title: String 資料類型
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: cd4b64c101ae56928e84a04649e49c17b6f4023c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415501"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="d3c29-102">String 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3c29-102">String Data Type (Visual Basic)</span></span>

<span data-ttu-id="d3c29-103">保留不帶正負號16位（2位元組）程式碼點的序列，其範圍介於0到65535之間。</span><span class="sxs-lookup"><span data-stu-id="d3c29-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="d3c29-104">每個程式*代碼點*或字元碼都代表一個 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="d3c29-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="d3c29-105">字串可包含0到大約2000000000（2 ^ 31）個 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="d3c29-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3c29-106">備註</span><span class="sxs-lookup"><span data-stu-id="d3c29-106">Remarks</span></span>  

 <span data-ttu-id="d3c29-107">使用 `String` 資料類型來保存多個字元，而不需要的陣列管理額外負荷，也就 `Char()` 是元素的陣列 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="d3c29-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="d3c29-108">的預設值 `String` 為 `Nothing` （null 參考）。</span><span class="sxs-lookup"><span data-stu-id="d3c29-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="d3c29-109">請注意，這與空字串（值 `""` ）不同。</span><span class="sxs-lookup"><span data-stu-id="d3c29-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="d3c29-110">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="d3c29-110">Unicode Characters</span></span>  

 <span data-ttu-id="d3c29-111">Unicode 的第一個128程式碼點（0–127）對應到標準美式鍵盤上的字母和符號。</span><span class="sxs-lookup"><span data-stu-id="d3c29-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="d3c29-112">這些前128個程式碼點與 ASCII 字元集所定義的相同。</span><span class="sxs-lookup"><span data-stu-id="d3c29-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="d3c29-113">第二個128程式碼片段（128–255）代表特殊字元，例如以拉丁為基礎的字母、重音、貨幣符號和分數。</span><span class="sxs-lookup"><span data-stu-id="d3c29-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="d3c29-114">Unicode 會針對各種不同的符號使用其餘的程式碼點（256-65535）。</span><span class="sxs-lookup"><span data-stu-id="d3c29-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="d3c29-115">這包括全球文字字元、變音符號和數學和技術符號。</span><span class="sxs-lookup"><span data-stu-id="d3c29-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="d3c29-116">您可以在 <xref:System.Char.IsDigit%2A> <xref:System.Char.IsPunctuation%2A> 變數中的個別字元上使用和之類的方法， `String` 以判斷其 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="d3c29-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="d3c29-117">格式需求</span><span class="sxs-lookup"><span data-stu-id="d3c29-117">Format Requirements</span></span>  

 <span data-ttu-id="d3c29-118">您必須將常值括 `String` 在引號內（ `" "` ）。</span><span class="sxs-lookup"><span data-stu-id="d3c29-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="d3c29-119">如果您必須在字串中包含引號做為其中一個字元，您可以使用兩個連續的引號（ `""` ）。</span><span class="sxs-lookup"><span data-stu-id="d3c29-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="d3c29-120">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="d3c29-120">The following example illustrates this.</span></span>  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="d3c29-121">請注意，在字串中代表引號的連續引號，與開始和結束常值的引號無關 `String` 。</span><span class="sxs-lookup"><span data-stu-id="d3c29-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="d3c29-122">字串操作</span><span class="sxs-lookup"><span data-stu-id="d3c29-122">String Manipulations</span></span>  

 <span data-ttu-id="d3c29-123">一旦您將字串指派給 `String` 變數，該字串就是*不可變*的，這表示您無法變更其長度或內容。</span><span class="sxs-lookup"><span data-stu-id="d3c29-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="d3c29-124">當您以任何方式改變字串時，Visual Basic 會建立新的字串，並放棄上一個字串。</span><span class="sxs-lookup"><span data-stu-id="d3c29-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="d3c29-125">`String`然後，變數會指向新的字串。</span><span class="sxs-lookup"><span data-stu-id="d3c29-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="d3c29-126">您可以 `String` 使用各種字串函數來操作變數的內容。</span><span class="sxs-lookup"><span data-stu-id="d3c29-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="d3c29-127">下列範例說明函式 <xref:Microsoft.VisualBasic.Strings.Left%2A></span><span class="sxs-lookup"><span data-stu-id="d3c29-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="d3c29-128">另一個元件所建立的字串可能會以前置或尾端空格填補。</span><span class="sxs-lookup"><span data-stu-id="d3c29-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="d3c29-129">如果您收到這類字串，您可以使用 <xref:Microsoft.VisualBasic.Strings.Trim%2A> 、 <xref:Microsoft.VisualBasic.Strings.LTrim%2A> 和 <xref:Microsoft.VisualBasic.Strings.RTrim%2A> 函數來移除這些空格。</span><span class="sxs-lookup"><span data-stu-id="d3c29-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="d3c29-130">如需有關字串操作的詳細資訊，請參閱[字串](../../programming-guide/language-features/strings/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c29-130">For more information about string manipulations, see [Strings](../../programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="d3c29-131">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="d3c29-131">Programming Tips</span></span>  
  
- <span data-ttu-id="d3c29-132">**負數。**</span><span class="sxs-lookup"><span data-stu-id="d3c29-132">**Negative Numbers.**</span></span> <span data-ttu-id="d3c29-133">請記住，保留的字元 `String` 是不帶正負號的，而且不能代表負數值。</span><span class="sxs-lookup"><span data-stu-id="d3c29-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="d3c29-134">在任何情況下，您都不應該使用 `String` 來保存數值。</span><span class="sxs-lookup"><span data-stu-id="d3c29-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
- <span data-ttu-id="d3c29-135">**Interop 考量：**</span><span class="sxs-lookup"><span data-stu-id="d3c29-135">**Interop Considerations.**</span></span> <span data-ttu-id="d3c29-136">如果您要使用的元件不是針對 .NET Framework 所撰寫（例如 Automation 或 COM 物件），請記住，在其他環境中，字串字元具有不同的資料寬度（8位）。</span><span class="sxs-lookup"><span data-stu-id="d3c29-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="d3c29-137">如果您要將8位字元的字串引數傳遞給這類元件，請將它宣告為 `Byte()` 、 `Byte` 元素陣列，而不是 `String` 新的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d3c29-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="d3c29-138">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="d3c29-138">**Type Characters.**</span></span> <span data-ttu-id="d3c29-139">將識別項型別字元附加 `$` 至任何識別碼，會強制其成為 `String` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="d3c29-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="d3c29-140">`String`沒有常數值型別字元。</span><span class="sxs-lookup"><span data-stu-id="d3c29-140">`String` has no literal type character.</span></span> <span data-ttu-id="d3c29-141">不過，編譯器會將以引號（）括住的常值視為 `" "` `String` 。</span><span class="sxs-lookup"><span data-stu-id="d3c29-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
- <span data-ttu-id="d3c29-142">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="d3c29-142">**Framework Type.**</span></span> <span data-ttu-id="d3c29-143">.NET Framework 中的對應類型是 <xref:System.String?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="d3c29-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c29-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3c29-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="d3c29-145">資料類型</span><span class="sxs-lookup"><span data-stu-id="d3c29-145">Data Types</span></span>](index.md)
- [<span data-ttu-id="d3c29-146">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="d3c29-146">Char Data Type</span></span>](char-data-type.md)
- [<span data-ttu-id="d3c29-147">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="d3c29-147">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="d3c29-148">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="d3c29-148">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="d3c29-149">作法：呼叫不帶正負號的類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="d3c29-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="d3c29-150">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="d3c29-150">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
