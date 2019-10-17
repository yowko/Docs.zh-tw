---
title: 字串函式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 32a31a881573cc9dc481fc07fc4067569a96a963
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395831"
---
# <a name="string-functions-visual-basic"></a><span data-ttu-id="4c163-102">字串函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c163-102">String Functions (Visual Basic)</span></span>

<span data-ttu-id="4c163-103">下表列出 Visual Basic 在 @no__t 0 類別中提供用來搜尋和操作字串的函數。</span><span class="sxs-lookup"><span data-stu-id="4c163-103">The following table lists the functions that Visual Basic provides in the <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> class to search and manipulate strings.</span></span> <span data-ttu-id="4c163-104">它們可以視為 Visual Basic 內建函式;也就是說，您不需要將它們當做類別的明確成員呼叫，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="4c163-104">They can be regarded as Visual Basic intrinsic functions; that is, you do not have to call them as explicit members of a class, as the examples show.</span></span> <span data-ttu-id="4c163-105">其他方法，在某些情況下是互補方法，可在 <xref:System.String?displayProperty=nameWithType> 類別中取得。</span><span class="sxs-lookup"><span data-stu-id="4c163-105">Additional methods, and in some cases complementary methods, are available in the <xref:System.String?displayProperty=nameWithType> class.</span></span> 
  
|<span data-ttu-id="4c163-106">.NET Framework 方法</span><span class="sxs-lookup"><span data-stu-id="4c163-106">.NET Framework method</span></span>|<span data-ttu-id="4c163-107">描述</span><span class="sxs-lookup"><span data-stu-id="4c163-107">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4c163-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>、 <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="4c163-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>|<span data-ttu-id="4c163-109">傳回表示對應于字元之字元碼的 @no__t 0 值。</span><span class="sxs-lookup"><span data-stu-id="4c163-109">Returns an `Integer` value representing the character code corresponding to a character.</span></span>|  
|<span data-ttu-id="4c163-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>、 <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="4c163-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>|<span data-ttu-id="4c163-111">傳回與指定的字元碼相關聯的字元。</span><span class="sxs-lookup"><span data-stu-id="4c163-111">Returns the character associated with the specified character code.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|<span data-ttu-id="4c163-112">根據指定的篩選準則，傳回以零為基底的陣列，其中包含 @no__t 0 陣列的子集。</span><span class="sxs-lookup"><span data-stu-id="4c163-112">Returns a zero-based array containing a subset of a `String` array based on specified filter criteria.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|<span data-ttu-id="4c163-113">根據包含在格式 `String` 運算式中的指示，傳回已格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-113">Returns a string formatted according to instructions contained in a format `String` expression.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|<span data-ttu-id="4c163-114">使用系統控制台中定義的貨幣符號，傳回格式化為貨幣值的運算式。</span><span class="sxs-lookup"><span data-stu-id="4c163-114">Returns an expression formatted as a currency value using the currency symbol defined in the system control panel.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|<span data-ttu-id="4c163-115">傳回表示日期/時間值的字串運算式。</span><span class="sxs-lookup"><span data-stu-id="4c163-115">Returns a string expression representing a date/time value.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|<span data-ttu-id="4c163-116">傳回格式化為數位的運算式。</span><span class="sxs-lookup"><span data-stu-id="4c163-116">Returns an expression formatted as a number.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|<span data-ttu-id="4c163-117">傳回格式化為百分比 (也就是乘以 100) 且尾端包含 % 字元的運算式。</span><span class="sxs-lookup"><span data-stu-id="4c163-117">Returns an expression formatted as a percentage (that is, multiplied by 100) with a trailing % character.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|<span data-ttu-id="4c163-118">傳回整數，指定一個字串在另一個字串中第一次出現的開始位置。</span><span class="sxs-lookup"><span data-stu-id="4c163-118">Returns an integer specifying the start position of the first occurrence of one string within another.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|<span data-ttu-id="4c163-119">從字串的右邊開始，傳回一個字串在另一個字串中第一次出現的位置。</span><span class="sxs-lookup"><span data-stu-id="4c163-119">Returns the position of the first occurrence of one string within another, starting from the right side of the string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|<span data-ttu-id="4c163-120">傳回由聯結陣列中包含的多個子字串所建立的字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-120">Returns a string created by joining a number of substrings contained in an array.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|<span data-ttu-id="4c163-121">傳回轉換成小寫的字串或字元。</span><span class="sxs-lookup"><span data-stu-id="4c163-121">Returns a string or character converted to lowercase.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|<span data-ttu-id="4c163-122">從字串的左邊傳回包含指定字元數的字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-122">Returns a string containing a specified number of characters from the left side of a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|<span data-ttu-id="4c163-123">傳回一個整數，其中包含字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="4c163-123">Returns an integer that contains the number of characters in a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|<span data-ttu-id="4c163-124">傳回靠左對齊的字串，其中包含已調整為指定之長度的指定字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-124">Returns a left-aligned string containing the specified string adjusted to the specified length.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|<span data-ttu-id="4c163-125">傳回字串，其中包含指定之字串的複本，但沒有開頭空白。</span><span class="sxs-lookup"><span data-stu-id="4c163-125">Returns a string containing a copy of a specified string with no leading spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|<span data-ttu-id="4c163-126">從字串中傳回包含指定字元數的字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-126">Returns a string containing a specified number of characters from a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|<span data-ttu-id="4c163-127">傳回字串，其中指定的子字串已由另一個子字串取代為指定的次數。</span><span class="sxs-lookup"><span data-stu-id="4c163-127">Returns a string in which a specified substring has been replaced with another substring a specified number of times.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|<span data-ttu-id="4c163-128">從字串的右邊傳回包含指定字元數的字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-128">Returns a string containing a specified number of characters from the right side of a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|<span data-ttu-id="4c163-129">傳回靠右對齊的字串，其中包含已調整為指定之長度的指定字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-129">Returns a right-aligned string containing the specified string adjusted to the specified length.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|<span data-ttu-id="4c163-130">傳回字串，其中包含指定之字串的複本，但沒有尾端空格。</span><span class="sxs-lookup"><span data-stu-id="4c163-130">Returns a string containing a copy of a specified string with no trailing spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|<span data-ttu-id="4c163-131">傳回由指定的空格數目所組成的字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-131">Returns a string consisting of the specified number of spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|<span data-ttu-id="4c163-132">傳回以零為基底的一維陣列，其中包含指定數目的子字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-132">Returns a zero-based, one-dimensional array containing a specified number of substrings.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|<span data-ttu-id="4c163-133">根據字串比較的結果，傳回-1、0或1。</span><span class="sxs-lookup"><span data-stu-id="4c163-133">Returns -1, 0, or 1, based on the result of a string comparison.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|<span data-ttu-id="4c163-134">傳回以指定方式轉換的字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-134">Returns a string converted as specified.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|<span data-ttu-id="4c163-135">傳回由重複指定次數的指定字元所組成的字串或物件。</span><span class="sxs-lookup"><span data-stu-id="4c163-135">Returns a string or object consisting of the specified character repeated the specified number of times.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|<span data-ttu-id="4c163-136">傳回字串，其中指定之字串的字元順序會反轉。</span><span class="sxs-lookup"><span data-stu-id="4c163-136">Returns a string in which the character order of a specified string is reversed.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|<span data-ttu-id="4c163-137">傳回字串，其中包含指定字串的複本，其中沒有開頭或尾端空格。</span><span class="sxs-lookup"><span data-stu-id="4c163-137">Returns a string containing a copy of a specified string with no leading or trailing spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|<span data-ttu-id="4c163-138">傳回字串或字元，其中包含轉換成大寫的指定字串。</span><span class="sxs-lookup"><span data-stu-id="4c163-138">Returns a string or character containing the specified string converted to uppercase.</span></span>|  
  
 <span data-ttu-id="4c163-139">您可以使用[Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)語句來設定是否要使用由系統地區設定（`Text`）所決定的區分大小寫文字排序次序來比較字串，或以字元的內部二進位標記法（`Binary`）。</span><span class="sxs-lookup"><span data-stu-id="4c163-139">You can use the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) statement to set whether strings are compared using a case-insensitive text sort order determined by your system's locale (`Text`) or by the internal binary representations of the characters (`Binary`).</span></span> <span data-ttu-id="4c163-140">預設的文字比較方法為 `Binary`。</span><span class="sxs-lookup"><span data-stu-id="4c163-140">The default text comparison method is `Binary`.</span></span>  
  
## <a name="example-ucase"></a><span data-ttu-id="4c163-141">範例： UCase</span><span class="sxs-lookup"><span data-stu-id="4c163-141">Example: UCase</span></span>

<span data-ttu-id="4c163-142">這個範例會使用 `UCase` 函式來傳回字串的大寫版本。</span><span class="sxs-lookup"><span data-stu-id="4c163-142">This example uses the `UCase` function to return an uppercase version of a string.</span></span>  
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]  
  
## <a name="example-ltrim"></a><span data-ttu-id="4c163-143">範例： LTrim</span><span class="sxs-lookup"><span data-stu-id="4c163-143">Example: LTrim</span></span>

<span data-ttu-id="4c163-144">這個範例會使用 `LTrim` 函式來去除開頭的空格，並使用 `RTrim` 函式來去除字串變數的尾端空格。</span><span class="sxs-lookup"><span data-stu-id="4c163-144">This example uses the `LTrim` function to strip leading spaces and the `RTrim` function to strip trailing spaces from a string variable.</span></span> <span data-ttu-id="4c163-145">它會使用 `Trim` 函式來去除這兩種類型的空間。</span><span class="sxs-lookup"><span data-stu-id="4c163-145">It uses the `Trim` function to strip both types of spaces.</span></span>  
  
[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]  
  
## <a name="example-mid"></a><span data-ttu-id="4c163-146">範例：中間</span><span class="sxs-lookup"><span data-stu-id="4c163-146">Example: Mid</span></span>

<span data-ttu-id="4c163-147">這個範例使用 `Mid` 函數，從字串傳回指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="4c163-147">This example uses the `Mid` function to return a specified number of characters from a string.</span></span>  

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]  

## <a name="example-len"></a><span data-ttu-id="4c163-148">範例： Len</span><span class="sxs-lookup"><span data-stu-id="4c163-148">Example: Len</span></span>

<span data-ttu-id="4c163-149">這個範例會使用 `Len` 來傳回字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="4c163-149">This example uses `Len` to return the number of characters in a string.</span></span>  
  
[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]  
  
## <a name="example-instr"></a><span data-ttu-id="4c163-150">範例： InStr</span><span class="sxs-lookup"><span data-stu-id="4c163-150">Example: InStr</span></span>

<span data-ttu-id="4c163-151">這個範例會使用 `InStr` 函式來傳回另一個字串在另一個字串中第一次出現的位置。</span><span class="sxs-lookup"><span data-stu-id="4c163-151">This example uses the `InStr` function to return the position of the first occurrence of one string within another.</span></span>  
  
[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]  
  
## <a name="example-format"></a><span data-ttu-id="4c163-152">範例：格式</span><span class="sxs-lookup"><span data-stu-id="4c163-152">Example: Format</span></span>

<span data-ttu-id="4c163-153">這個範例會示範使用 `String` 格式和使用者定義格式來格式化值的 @no__t 0 函數的各種用法。</span><span class="sxs-lookup"><span data-stu-id="4c163-153">This example shows various uses of the `Format` function to format values using both `String` formats and user-defined formats.</span></span> <span data-ttu-id="4c163-154">針對日期分隔符號（`/`）、時間分隔符號（`:`）和 AM/PM 指標（`t` 和 `tt`），您系統所顯示的實際格式化輸出取決於程式碼所使用的地區設定。</span><span class="sxs-lookup"><span data-stu-id="4c163-154">For the date separator (`/`), time separator (`:`), and the AM/PM indicators (`t` and `tt`), the actual formatted output displayed by your system depends on the locale settings the code is using.</span></span> <span data-ttu-id="4c163-155">在開發環境中顯示時間和日期時，會使用程式碼地區設定的簡短時間格式和簡短日期格式。</span><span class="sxs-lookup"><span data-stu-id="4c163-155">When times and dates are displayed in the development environment, the short time format and short date format of the code locale are used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c163-156">針對使用24小時制的地區設定，AM/PM 指標（`t` 和 `tt`）不會顯示任何內容。</span><span class="sxs-lookup"><span data-stu-id="4c163-156">For locales that use a 24-hour clock, the AM/PM indicators (`t` and `tt`) display nothing.</span></span>  
  
 [!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="4c163-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c163-157">See also</span></span>

- [<span data-ttu-id="4c163-158">關鍵字</span><span class="sxs-lookup"><span data-stu-id="4c163-158">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="4c163-159">Visual Basic 執行階段程式庫成員</span><span class="sxs-lookup"><span data-stu-id="4c163-159">Visual Basic Runtime Library Members</span></span>](../../../visual-basic/language-reference/runtime-library-members.md)
- [<span data-ttu-id="4c163-160">字串操作摘要</span><span class="sxs-lookup"><span data-stu-id="4c163-160">String Manipulation Summary</span></span>](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
- [<span data-ttu-id="4c163-161">System.string 類別方法</span><span class="sxs-lookup"><span data-stu-id="4c163-161">System.String class methods</span></span>](xref:System.String#methods)
