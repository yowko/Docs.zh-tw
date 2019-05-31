---
title: Date 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: 970c69b36eecd110dd81b6a3700fbb0a7eea2834
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424030"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="f2702-102">Date 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2702-102">Date Data Type (Visual Basic)</span></span>
<span data-ttu-id="f2702-103">具有 IEEE 64 位元 (8 位元組) 值，以代表從 0001 年 1 月 1 日到 9999 年 12 月 31 日的日期，以及從上午 (午夜) 12:00:00 到下午 11:59:59.9999999 的時間。</span><span class="sxs-lookup"><span data-stu-id="f2702-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="f2702-104">每個增量代表西曆日曆 1 年 1 月 1 日開始之後經過 100 奈秒的時間。</span><span class="sxs-lookup"><span data-stu-id="f2702-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="f2702-105">最大值代表 10000 年 1 月 1 開始之前的 100 奈秒。</span><span class="sxs-lookup"><span data-stu-id="f2702-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2702-106">備註</span><span class="sxs-lookup"><span data-stu-id="f2702-106">Remarks</span></span>  
 <span data-ttu-id="f2702-107">使用 `Date` 資料類型可包含日期值、時間值或日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="f2702-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>  
  
 <span data-ttu-id="f2702-108">`Date` 的預設值為 0001 年 1 月 1 日的 0:00:00 (午夜)。</span><span class="sxs-lookup"><span data-stu-id="f2702-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>  
  
 <span data-ttu-id="f2702-109">您可以從 <xref:Microsoft.VisualBasic.DateAndTime> 取得目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f2702-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="f2702-110">格式需求</span><span class="sxs-lookup"><span data-stu-id="f2702-110">Format Requirements</span></span>  
 <span data-ttu-id="f2702-111">您必須將 `Date` 常值包含在數字符號 (`# #`) 中。</span><span class="sxs-lookup"><span data-stu-id="f2702-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="f2702-112">您必須指定 M/d/yyyy 格式 (例如 `#5/31/1993#`) 或 yyyy-MM-dd (例如 `#1993-5-31#`) 的日期值。</span><span class="sxs-lookup"><span data-stu-id="f2702-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="f2702-113">先指定年份時可以使用斜線。</span><span class="sxs-lookup"><span data-stu-id="f2702-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="f2702-114">這項需求與您的地區設定和電腦的日期和時間格式設定無關。</span><span class="sxs-lookup"><span data-stu-id="f2702-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>  
  
 <span data-ttu-id="f2702-115">之所以有這項限制，是因為您程式碼的意義絕不應根據您的應用程式執行所在的地區設定而變更。</span><span class="sxs-lookup"><span data-stu-id="f2702-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="f2702-116">假設您對 `#3/4/1998#` 的 `Date` 常值進行硬式編碼，並想要讓它代表 1998 年 3 月 4 日。</span><span class="sxs-lookup"><span data-stu-id="f2702-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="f2702-117">在使用 mm/dd/yyyy 的地區設定中，3/4/1998 會依照您的需求進行編譯。</span><span class="sxs-lookup"><span data-stu-id="f2702-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="f2702-118">但是，假設您部署您的應用程式，在許多國家/地區。</span><span class="sxs-lookup"><span data-stu-id="f2702-118">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="f2702-119">在使用 dd/mm/yyyy 的地區設定中，您硬式編碼的常值會編譯為 1998 年 4 月 3 日。</span><span class="sxs-lookup"><span data-stu-id="f2702-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="f2702-120">在使用 yyyy/mm/dd 的地區設定中，常值將是無效的 (0003 年 4 月 1998 日)，而且會導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2702-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>  
  
## <a name="workarounds"></a><span data-ttu-id="f2702-121">替代解決辦法</span><span class="sxs-lookup"><span data-stu-id="f2702-121">Workarounds</span></span>  
 <span data-ttu-id="f2702-122">若要將 `Date` 常值轉換為您的地區設定或自訂格式，請將常值提供給 <xref:Microsoft.VisualBasic.Strings.Format%2A> 函式，以指定預先定義或使用者定義的日期格式。</span><span class="sxs-lookup"><span data-stu-id="f2702-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="f2702-123">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="f2702-123">The following example demonstrates this.</span></span>  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 <span data-ttu-id="f2702-124">或者，您可以使用 <xref:System.DateTime> 結構的其中一個多載建構函式，以組合日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="f2702-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="f2702-125">下列範例會建立一個值來代表 1993 年 5 月 31 日下午 12:14。</span><span class="sxs-lookup"><span data-stu-id="f2702-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a><span data-ttu-id="f2702-126">小時格式</span><span class="sxs-lookup"><span data-stu-id="f2702-126">Hour Format</span></span>  
 <span data-ttu-id="f2702-127">您可以指定 12 小時或 24 小時格式的時間值，例如 `#1:15:30 PM#` 或 `#13:15:30#`。</span><span class="sxs-lookup"><span data-stu-id="f2702-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="f2702-128">不過，若未指定分或秒，您必須指定 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="f2702-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>  
  
## <a name="date-and-time-defaults"></a><span data-ttu-id="f2702-129">日期和時間預設值</span><span class="sxs-lookup"><span data-stu-id="f2702-129">Date and Time Defaults</span></span>  
 <span data-ttu-id="f2702-130">如果您未在日期/時間常值中包含日期，Visual Basic 會將值的日期部分設為 0001 年 1 月 1 日。</span><span class="sxs-lookup"><span data-stu-id="f2702-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="f2702-131">如果您未在日期/時間常值中包含時間，Visual Basic 會將值的時間部分設為一天的開始，即午夜 (0:00:00)。</span><span class="sxs-lookup"><span data-stu-id="f2702-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="f2702-132">類型轉換</span><span class="sxs-lookup"><span data-stu-id="f2702-132">Type Conversions</span></span>  
 <span data-ttu-id="f2702-133">如果您將 `Date` 值轉換為 `String` 類型，Visual Basic 會根據執行階段地區設定所指定的簡短日期格式呈現日期，並根據執行階段地區設定所指定的時間格式 (12 小時制或 24 小時制) 呈現時間。</span><span class="sxs-lookup"><span data-stu-id="f2702-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="f2702-134">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="f2702-134">Programming Tips</span></span>  
  
- <span data-ttu-id="f2702-135">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="f2702-135">**Interop Considerations.**</span></span> <span data-ttu-id="f2702-136">如果您要使用的元件不是針對 .NET Framework 所撰寫 (例如 Automation 或 COM 物件)，請記住，其他環境中的日期/時間類型與 Visual Basic `Date` 類型並不相融。</span><span class="sxs-lookup"><span data-stu-id="f2702-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="f2702-137">如果您要將日期/時間引數傳遞至這類元件，請在新的 Visual Basic 程式碼中將它宣告為 `Double` (而不是 `Date`)，並使用轉換方法 <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> 和 <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f2702-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f2702-138">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="f2702-138">**Type Characters.**</span></span> <span data-ttu-id="f2702-139">`Date` 沒有任何常值類型字元或識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="f2702-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="f2702-140">不過，編譯器會將包含在數字符號 (`# #`) 內的常值視為 `Date`。</span><span class="sxs-lookup"><span data-stu-id="f2702-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>  
  
- <span data-ttu-id="f2702-141">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="f2702-141">**Framework Type.**</span></span> <span data-ttu-id="f2702-142">在 .NET Framework 中對應的類型為 <xref:System.DateTime?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="f2702-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2702-143">範例</span><span class="sxs-lookup"><span data-stu-id="f2702-143">Example</span></span>  
 <span data-ttu-id="f2702-144">`Date` 資料類型的變數或常數會同時包含日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f2702-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="f2702-145">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f2702-145">The following example illustrates this.</span></span>  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2702-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2702-146">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="f2702-147">資料類型</span><span class="sxs-lookup"><span data-stu-id="f2702-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f2702-148">標準日期和時間格式字串</span><span class="sxs-lookup"><span data-stu-id="f2702-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="f2702-149">自訂日期和時間格式字串</span><span class="sxs-lookup"><span data-stu-id="f2702-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="f2702-150">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="f2702-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f2702-151">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="f2702-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="f2702-152">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="f2702-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
