---
title: HOW TO：從特定日期擷取一星期的哪一日
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- DateTime.DayOfWeek property
- DateTime.ToString method
- dates [.NET Framework], retrieving week information
- DateTimeOffset.DayOfWeek property
- dates [.NET Framework], day of week
- Weekday function
- day of week [.NET Framework]
- extracting day of week
- weekday names
- WeekdayName function
- numbers [.NET Framework], day of week
- formatting [.NET Framework], time
- DateTimeOffset.ToString method
- full weekday names
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2c422a75244302ae6433af933995b00bdfaa061
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537968"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a><span data-ttu-id="0d403-102">HOW TO：從特定日期擷取一星期的哪一日</span><span class="sxs-lookup"><span data-stu-id="0d403-102">How to: Extract the Day of the Week from a Specific Date</span></span>
<span data-ttu-id="0d403-103">.NET Framework 可方便判斷特定日期是一週的第幾天，並可顯示特定日期當地語系化的工作日名稱。</span><span class="sxs-lookup"><span data-stu-id="0d403-103">The .NET Framework makes it easy to determine the ordinal day of the week for a particular date, and to display the localized weekday name for a particular date.</span></span> <span data-ttu-id="0d403-104">您可以從 <xref:System.DateTime.DayOfWeek%2A> 或 <xref:System.DateTimeOffset.DayOfWeek%2A> 屬性取得指出對應於特定日期是星期幾的列舉值。</span><span class="sxs-lookup"><span data-stu-id="0d403-104">An enumerated value that indicates the day of the week corresponding to a particular date is available from the <xref:System.DateTime.DayOfWeek%2A> or <xref:System.DateTimeOffset.DayOfWeek%2A> property.</span></span> <span data-ttu-id="0d403-105">相對地，擷取工作日名稱是一種格式化作業，可藉由呼叫格式化方法來執行，例如日期和時間值的 `ToString` 方法或 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d403-105">In contrast, retrieving the weekday name is a formatting operation that can be performed by calling a formatting method, such as a date and time value's `ToString` method or the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0d403-106">本主題示範如何執行下列格式化作業：</span><span class="sxs-lookup"><span data-stu-id="0d403-106">This topic shows how to perform these formatting operations.</span></span>  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a><span data-ttu-id="0d403-107">從特定日期擷取指出星期幾的數字</span><span class="sxs-lookup"><span data-stu-id="0d403-107">To extract a number indicating the day of the week from a specific date</span></span>  
  
1.  <span data-ttu-id="0d403-108">如果您要處理日期的字串表示法，請使用靜態 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 方法，將其轉換成 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="0d403-108">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="0d403-109">使用 <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> 屬性，以擷取指出星期幾的 <xref:System.DayOfWeek> 值。</span><span class="sxs-lookup"><span data-stu-id="0d403-109">Use the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve a <xref:System.DayOfWeek> value that indicates the day of the week.</span></span>  
  
3.  <span data-ttu-id="0d403-110">若有需要，可將 <xref:System.DayOfWeek> 值轉型 (在 C# 中) 或轉換 (在 Visual Basic 中) 成整數。</span><span class="sxs-lookup"><span data-stu-id="0d403-110">If necessary, cast (in C#) or convert (in Visual Basic) the <xref:System.DayOfWeek> value to an integer.</span></span>  
  
 <span data-ttu-id="0d403-111">下列範例顯示代表特定日期是星期幾的整數。</span><span class="sxs-lookup"><span data-stu-id="0d403-111">The following example displays an integer that represents the day of the week of a specific date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a><span data-ttu-id="0d403-112">從特定日期擷取縮寫的工作日名稱。</span><span class="sxs-lookup"><span data-stu-id="0d403-112">To extract the abbreviated weekday name from a specific date</span></span>  
  
1.  <span data-ttu-id="0d403-113">如果您要處理日期的字串表示法，請使用靜態 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 方法，將其轉換成 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="0d403-113">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="0d403-114">您可以擷取目前文化特性或特定文化特性的工作日名稱縮寫。</span><span class="sxs-lookup"><span data-stu-id="0d403-114">You can extract the abbreviated weekday name of the current culture or of a specific culture:</span></span>  
  
    1.  <span data-ttu-id="0d403-115">若要擷取目前文化特性的工作日名稱縮寫，請呼叫日期和時間值的 <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> 執行個體方法，並傳遞字串 "ddd" 做為 `format` 參數。</span><span class="sxs-lookup"><span data-stu-id="0d403-115">To extract the abbreviated weekday name for the current culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="0d403-116">下列範例說明如何呼叫 <xref:System.DateTime.ToString%28System.String%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d403-116">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2.  <span data-ttu-id="0d403-117">若要擷取特定文化特性的工作日名稱縮寫，請呼叫日期和時間值的 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="0d403-117">To extract the abbreviated weekday name for a specific culture, call the date and time value’s <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="0d403-118">傳遞字串 "ddd" 做為 `format` 參數。</span><span class="sxs-lookup"><span data-stu-id="0d403-118">Pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="0d403-119">傳遞 <xref:System.Globalization.CultureInfo> 或 <xref:System.Globalization.DateTimeFormatInfo> 物件，其代表您想要將其工作日名稱當作 `provider` 參數來擷取的文化特性。</span><span class="sxs-lookup"><span data-stu-id="0d403-119">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="0d403-120">下列程式碼說明如何使用代表 fr-FR 文化特性的 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> 物件，來呼叫 <xref:System.Globalization.CultureInfo> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d403-120">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the fr-FR culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a><span data-ttu-id="0d403-121">從特定日期擷取完整的工作日名稱。</span><span class="sxs-lookup"><span data-stu-id="0d403-121">To extract the full weekday name from a specific date</span></span>  
  
1.  <span data-ttu-id="0d403-122">如果您要處理日期的字串表示法，請使用靜態 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 方法，將其轉換成 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="0d403-122">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="0d403-123">您可以擷取目前文化特性或特定文化特性的完整工作日名稱。</span><span class="sxs-lookup"><span data-stu-id="0d403-123">You can extract the full weekday name of the current culture or of a specific culture:</span></span>  
  
    1.  <span data-ttu-id="0d403-124">若要擷取目前文化特性的工作日名稱，請呼叫日期和時間值的 <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> 執行個體方法，並傳遞字串 "dddd" 做為 `format` 參數。</span><span class="sxs-lookup"><span data-stu-id="0d403-124">To extract the weekday name for the current culture, call the date and time value’s <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="0d403-125">下列範例說明如何呼叫 <xref:System.DateTime.ToString%28System.String%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d403-125">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2.  <span data-ttu-id="0d403-126">若要擷取特定文化特性的工作日名稱，請呼叫日期和時間值的 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="0d403-126">To extract the weekday name for a specific culture, call the date and time value’s <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="0d403-127">傳遞字串 "ddd" 做為 `format` 參數。</span><span class="sxs-lookup"><span data-stu-id="0d403-127">Pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="0d403-128">傳遞 <xref:System.Globalization.CultureInfo> 或 <xref:System.Globalization.DateTimeFormatInfo> 物件，其代表您想要將其工作日名稱當作 `provider` 參數來擷取的文化特性。</span><span class="sxs-lookup"><span data-stu-id="0d403-128">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="0d403-129">下列程式碼說明如何使用代表 es-ES 文化特性的 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> 物件，來呼叫 <xref:System.Globalization.CultureInfo> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d403-129">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the es-ES culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="0d403-130">範例</span><span class="sxs-lookup"><span data-stu-id="0d403-130">Example</span></span>  
 <span data-ttu-id="0d403-131">此範例說明如何呼叫 <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> 屬性以及 <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> 方法，以針對特定日期擷取代表星期幾的數字、縮寫的工作日名稱，以及完整的工作日名稱。</span><span class="sxs-lookup"><span data-stu-id="0d403-131">The example illustrates calls to the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> properties and the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> methods to retrieve the number that represents the day of the week, the abbreviated weekday name, and the full weekday name for a particular date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 <span data-ttu-id="0d403-132">個別語言可能會提供功能來複製或補充 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供的功能。</span><span class="sxs-lookup"><span data-stu-id="0d403-132">Individual languages may provide functionality that duplicates or supplements the functionality provided by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="0d403-133">例如，Visual Basic 就有包含兩個這類函式：</span><span class="sxs-lookup"><span data-stu-id="0d403-133">For example, Visual Basic includes two such functions:</span></span>  
  
-   <span data-ttu-id="0d403-134">`Weekday` 會傳回指出特定日期是星期幾的數字。</span><span class="sxs-lookup"><span data-stu-id="0d403-134">`Weekday`, which returns a number that indicates the day of the week of a particular date.</span></span> <span data-ttu-id="0d403-135">它會將一週第一天的序數值視為一，而 <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> 屬性會將其視為零。</span><span class="sxs-lookup"><span data-stu-id="0d403-135">It considers the ordinal value of the first day of the week to be one, whereas the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property considers it to be zero.</span></span>  
  
-   <span data-ttu-id="0d403-136">`WeekdayName` 會傳回目前文化特性中對應特定工作日編號的週間日名稱。</span><span class="sxs-lookup"><span data-stu-id="0d403-136">`WeekdayName`, which returns the name of the week in the current culture that corresponds to a particular weekday number.</span></span>  
  
 <span data-ttu-id="0d403-137">下列範例說明如何使用 Visual Basic `Weekday` 和 `WeekdayName` 函式。</span><span class="sxs-lookup"><span data-stu-id="0d403-137">The following example illustrates the use of the Visual Basic `Weekday` and `WeekdayName` functions.</span></span>  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 <span data-ttu-id="0d403-138">您也可以使用 <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> 屬性傳回的值來擷取特定日期的工作日名稱。</span><span class="sxs-lookup"><span data-stu-id="0d403-138">You can also use the value returned by the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve the weekday name of a particular date.</span></span> <span data-ttu-id="0d403-139">這只需要在該屬性傳回的 <xref:System.Enum.ToString%2A> 值上呼叫 <xref:System.DayOfWeek> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d403-139">This requires only a call to the <xref:System.Enum.ToString%2A> method on the <xref:System.DayOfWeek> value returned by the property.</span></span> <span data-ttu-id="0d403-140">不過，此技巧並不會產生目前文化特性的當地語系化工作日名稱，如下列範例所說明。</span><span class="sxs-lookup"><span data-stu-id="0d403-140">However, this technique does not produce a localized weekday name for the current culture, as the following example illustrates.</span></span>  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="0d403-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d403-141">See also</span></span>

- [<span data-ttu-id="0d403-142">執行格式化作業</span><span class="sxs-lookup"><span data-stu-id="0d403-142">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)
- [<span data-ttu-id="0d403-143">標準日期和時間格式字串</span><span class="sxs-lookup"><span data-stu-id="0d403-143">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="0d403-144">自訂日期和時間格式字串</span><span class="sxs-lookup"><span data-stu-id="0d403-144">Custom Date and Time Format Strings</span></span>](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
