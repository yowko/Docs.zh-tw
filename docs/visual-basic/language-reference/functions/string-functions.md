---
title: 字串函式
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 778e57eadd75baf1aabd100f9d8d41a490f79a04
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406284"
---
# <a name="string-functions-visual-basic"></a><span data-ttu-id="82696-102">字串函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82696-102">String Functions (Visual Basic)</span></span>

<span data-ttu-id="82696-103">下表列出 Visual Basic 在類別中提供用 <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> 來搜尋和操作字串的函式。</span><span class="sxs-lookup"><span data-stu-id="82696-103">The following table lists the functions that Visual Basic provides in the <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> class to search and manipulate strings.</span></span> <span data-ttu-id="82696-104">它們可以視為 Visual Basic 內建函式;也就是說，您不需要將它們當做類別的明確成員呼叫，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="82696-104">They can be regarded as Visual Basic intrinsic functions; that is, you do not have to call them as explicit members of a class, as the examples show.</span></span> <span data-ttu-id="82696-105">類別中也提供其他方法，在某些情況下互補方法 <xref:System.String?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="82696-105">Additional methods, and in some cases complementary methods, are available in the <xref:System.String?displayProperty=nameWithType> class.</span></span>

|<span data-ttu-id="82696-106">.NET Framework 方法</span><span class="sxs-lookup"><span data-stu-id="82696-106">.NET Framework method</span></span>|<span data-ttu-id="82696-107">Description</span><span class="sxs-lookup"><span data-stu-id="82696-107">Description</span></span>|
|---------------------------|-----------------|
|<span data-ttu-id="82696-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="82696-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>|<span data-ttu-id="82696-109">傳回 `Integer` 值，表示對應至字元的字元碼。</span><span class="sxs-lookup"><span data-stu-id="82696-109">Returns an `Integer` value representing the character code corresponding to a character.</span></span>|
|<span data-ttu-id="82696-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="82696-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>|<span data-ttu-id="82696-111">傳回與指定的字元碼關聯的字元。</span><span class="sxs-lookup"><span data-stu-id="82696-111">Returns the character associated with the specified character code.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|<span data-ttu-id="82696-112">傳回以零起始的陣列，其中包含以指定篩選準則為依據的 `String` 陣列子集。</span><span class="sxs-lookup"><span data-stu-id="82696-112">Returns a zero-based array containing a subset of a `String` array based on specified filter criteria.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|<span data-ttu-id="82696-113">傳回字串，其格式化方式是根據格式 `String` 運算式內包含的指令。</span><span class="sxs-lookup"><span data-stu-id="82696-113">Returns a string formatted according to instructions contained in a format `String` expression.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|<span data-ttu-id="82696-114">使用 [系統] 控制台中定義的貨幣符號，傳回格式化成貨幣值的運算式。</span><span class="sxs-lookup"><span data-stu-id="82696-114">Returns an expression formatted as a currency value using the currency symbol defined in the system control panel.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|<span data-ttu-id="82696-115">傳回表示日期/時間值的字串運算式。</span><span class="sxs-lookup"><span data-stu-id="82696-115">Returns a string expression representing a date/time value.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|<span data-ttu-id="82696-116">傳回格式化成數字的運算式。</span><span class="sxs-lookup"><span data-stu-id="82696-116">Returns an expression formatted as a number.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|<span data-ttu-id="82696-117">傳回格式化為百分比 (也就是乘以 100) 且尾端包含 % 字元的運算式。</span><span class="sxs-lookup"><span data-stu-id="82696-117">Returns an expression formatted as a percentage (that is, multiplied by 100) with a trailing % character.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|<span data-ttu-id="82696-118">傳回整數，指定一個字串在另一個字串內第一次出現的起始位置。</span><span class="sxs-lookup"><span data-stu-id="82696-118">Returns an integer specifying the start position of the first occurrence of one string within another.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|<span data-ttu-id="82696-119">傳回某個字串在另一個字串中第一次出現的位置，從字串的右邊開始。</span><span class="sxs-lookup"><span data-stu-id="82696-119">Returns the position of the first occurrence of one string within another, starting from the right side of the string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|<span data-ttu-id="82696-120">傳回結合包含在陣列中幾個子字串所建立的字串。</span><span class="sxs-lookup"><span data-stu-id="82696-120">Returns a string created by joining a number of substrings contained in an array.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|<span data-ttu-id="82696-121">傳回已轉換成小寫的字串或字元。</span><span class="sxs-lookup"><span data-stu-id="82696-121">Returns a string or character converted to lowercase.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|<span data-ttu-id="82696-122">傳回字串，其中包含從字串的左邊開始的指定數目的字元。</span><span class="sxs-lookup"><span data-stu-id="82696-122">Returns a string containing a specified number of characters from the left side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|<span data-ttu-id="82696-123">傳回一個整數，其中包含字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="82696-123">Returns an integer that contains the number of characters in a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|<span data-ttu-id="82696-124">傳回靠左對齊的字串，其中包含調整為指定之長度的指定字串。</span><span class="sxs-lookup"><span data-stu-id="82696-124">Returns a left-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|<span data-ttu-id="82696-125">傳回字串，其中包含指定之字串的複本，但沒有開頭空白。</span><span class="sxs-lookup"><span data-stu-id="82696-125">Returns a string containing a copy of a specified string with no leading spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|<span data-ttu-id="82696-126">從字串中傳回包含指定字元數的字串。</span><span class="sxs-lookup"><span data-stu-id="82696-126">Returns a string containing a specified number of characters from a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|<span data-ttu-id="82696-127">傳回字串，其中的指定之子字串已經被另一個子字串取代了指定的次數。</span><span class="sxs-lookup"><span data-stu-id="82696-127">Returns a string in which a specified substring has been replaced with another substring a specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|<span data-ttu-id="82696-128">傳回字串，其中包含從字串的右邊開始的指定數目的字元。</span><span class="sxs-lookup"><span data-stu-id="82696-128">Returns a string containing a specified number of characters from the right side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|<span data-ttu-id="82696-129">傳回靠右對齊的字串，其中包含調整為指定之長度的指定字串。</span><span class="sxs-lookup"><span data-stu-id="82696-129">Returns a right-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|<span data-ttu-id="82696-130">傳回字串，其中包含指定之字串的複本，但沒有尾端空格。</span><span class="sxs-lookup"><span data-stu-id="82696-130">Returns a string containing a copy of a specified string with no trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|<span data-ttu-id="82696-131">傳回字串，此字串是由指定之空格數所組成。</span><span class="sxs-lookup"><span data-stu-id="82696-131">Returns a string consisting of the specified number of spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|<span data-ttu-id="82696-132">傳回以零起始的一維陣列，其中包含指定之子字串數目。</span><span class="sxs-lookup"><span data-stu-id="82696-132">Returns a zero-based, one-dimensional array containing a specified number of substrings.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|<span data-ttu-id="82696-133">根據字串比較的結果傳回 -1、0 或 1。</span><span class="sxs-lookup"><span data-stu-id="82696-133">Returns -1, 0, or 1, based on the result of a string comparison.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|<span data-ttu-id="82696-134">傳回依照指定方式轉換的字串。</span><span class="sxs-lookup"><span data-stu-id="82696-134">Returns a string converted as specified.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|<span data-ttu-id="82696-135">傳回由重複指定次數的指定字元所組成的字串或物件。</span><span class="sxs-lookup"><span data-stu-id="82696-135">Returns a string or object consisting of the specified character repeated the specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|<span data-ttu-id="82696-136">傳回字串，其中的指定之字串的字元順序會顛倒。</span><span class="sxs-lookup"><span data-stu-id="82696-136">Returns a string in which the character order of a specified string is reversed.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|<span data-ttu-id="82696-137">傳回字串，其中包含指定字串的複本，其中沒有開頭或尾端空格。</span><span class="sxs-lookup"><span data-stu-id="82696-137">Returns a string containing a copy of a specified string with no leading or trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|<span data-ttu-id="82696-138">傳回包含已轉換成大寫之指定字串的字串或字元。</span><span class="sxs-lookup"><span data-stu-id="82696-138">Returns a string or character containing the specified string converted to uppercase.</span></span>|

<span data-ttu-id="82696-139">您可以使用[Option Compare](../statements/option-compare-statement.md)語句來設定是否要使用由系統的地區設定（）所決定的區分大小寫文字排序次序， `Text` 或字元（）的內部二進位標記法來比較字串 `Binary` 。</span><span class="sxs-lookup"><span data-stu-id="82696-139">You can use the [Option Compare](../statements/option-compare-statement.md) statement to set whether strings are compared using a case-insensitive text sort order determined by your system's locale (`Text`) or by the internal binary representations of the characters (`Binary`).</span></span> <span data-ttu-id="82696-140">預設的文字比較方法是 `Binary` 。</span><span class="sxs-lookup"><span data-stu-id="82696-140">The default text comparison method is `Binary`.</span></span>

## <a name="example-ucase"></a><span data-ttu-id="82696-141">範例： UCase</span><span class="sxs-lookup"><span data-stu-id="82696-141">Example: UCase</span></span>

<span data-ttu-id="82696-142">此範例使用 `UCase` 函式，傳回大寫字母版本的字串。</span><span class="sxs-lookup"><span data-stu-id="82696-142">This example uses the `UCase` function to return an uppercase version of a string.</span></span>
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]

## <a name="example-ltrim"></a><span data-ttu-id="82696-143">範例： LTrim</span><span class="sxs-lookup"><span data-stu-id="82696-143">Example: LTrim</span></span>

<span data-ttu-id="82696-144">此範例使用 `LTrim` 函式刪除字串變數中的前置空格，並使用 `RTrim` 函式刪除字串變數中的尾端空格。</span><span class="sxs-lookup"><span data-stu-id="82696-144">This example uses the `LTrim` function to strip leading spaces and the `RTrim` function to strip trailing spaces from a string variable.</span></span> <span data-ttu-id="82696-145">它會使用 `Trim` 函式刪除這兩種類型的空格。</span><span class="sxs-lookup"><span data-stu-id="82696-145">It uses the `Trim` function to strip both types of spaces.</span></span>

[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]

## <a name="example-mid"></a><span data-ttu-id="82696-146">範例：中間</span><span class="sxs-lookup"><span data-stu-id="82696-146">Example: Mid</span></span>

<span data-ttu-id="82696-147">這個範例會使用 `Mid` 函數，從字串中傳回指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="82696-147">This example uses the `Mid` function to return a specified number of characters from a string.</span></span>

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]

## <a name="example-len"></a><span data-ttu-id="82696-148">範例： Len</span><span class="sxs-lookup"><span data-stu-id="82696-148">Example: Len</span></span>

<span data-ttu-id="82696-149">這個範例使用 `Len` 傳回字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="82696-149">This example uses `Len` to return the number of characters in a string.</span></span>

[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]

## <a name="example-instr"></a><span data-ttu-id="82696-150">範例： InStr</span><span class="sxs-lookup"><span data-stu-id="82696-150">Example: InStr</span></span>

<span data-ttu-id="82696-151">此範例使用 `InStr` 函式傳回某個字串在另一個字串中第一次出現的位置。</span><span class="sxs-lookup"><span data-stu-id="82696-151">This example uses the `InStr` function to return the position of the first occurrence of one string within another.</span></span>

[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]

## <a name="example-format"></a><span data-ttu-id="82696-152">範例：格式</span><span class="sxs-lookup"><span data-stu-id="82696-152">Example: Format</span></span>

<span data-ttu-id="82696-153">此範例將示範 `Format` 函式的各種使用方式，以透過 `String` 格式及使用者定義的格式，將值格式化。</span><span class="sxs-lookup"><span data-stu-id="82696-153">This example shows various uses of the `Format` function to format values using both `String` formats and user-defined formats.</span></span> <span data-ttu-id="82696-154">對於日期分隔符號 (`/`)、時間分隔符號 (`:`) 和 AM/PM 指示器 (`t` 和 `tt`) 而言，系統顯示的實際格式化輸出需視程式碼使用的地區設定而定。</span><span class="sxs-lookup"><span data-stu-id="82696-154">For the date separator (`/`), time separator (`:`), and the AM/PM indicators (`t` and `tt`), the actual formatted output displayed by your system depends on the locale settings the code is using.</span></span> <span data-ttu-id="82696-155">當時間和日期顯示在開發環境內時，會使用程式碼地區設定的簡短時間格式和簡短日期格式。</span><span class="sxs-lookup"><span data-stu-id="82696-155">When times and dates are displayed in the development environment, the short time format and short date format of the code locale are used.</span></span>

> [!NOTE]
> <span data-ttu-id="82696-156">若為使用 24 小時制的地區設定，AM/PM 指示器 (`t` 和 `tt`) 不會顯示任何內容。</span><span class="sxs-lookup"><span data-stu-id="82696-156">For locales that use a 24-hour clock, the AM/PM indicators (`t` and `tt`) display nothing.</span></span>

[!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]

## <a name="see-also"></a><span data-ttu-id="82696-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82696-157">See also</span></span>

- [<span data-ttu-id="82696-158">關鍵字</span><span class="sxs-lookup"><span data-stu-id="82696-158">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="82696-159">Visual Basic 執行階段程式庫成員</span><span class="sxs-lookup"><span data-stu-id="82696-159">Visual Basic Runtime Library Members</span></span>](../runtime-library-members.md)
- [<span data-ttu-id="82696-160">字串操作摘要</span><span class="sxs-lookup"><span data-stu-id="82696-160">String Manipulation Summary</span></span>](../keywords/string-manipulation-summary.md)
- [<span data-ttu-id="82696-161">System.string 類別方法</span><span class="sxs-lookup"><span data-stu-id="82696-161">System.String class methods</span></span>](xref:System.String#methods)
