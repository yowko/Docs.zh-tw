---
title: "在 .NET 中剖析日期和時間字串"
description: "在 .NET 中剖析日期和時間字串"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e61514cd-5329-4eb8-b122-482fffb54ab7
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f0131baa0874880b6697458426da5ae9ce1705b7
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-date-and-time-strings-in-net"></a><span data-ttu-id="f8569-104">在 .NET 中剖析日期和時間字串</span><span class="sxs-lookup"><span data-stu-id="f8569-104">Parsing date and time strings in .NET</span></span>

<span data-ttu-id="f8569-105">剖析方法會將表示日期和時間的字串，轉換為同等的 [DateTime](xref:System.DateTime) 物件。</span><span class="sxs-lookup"><span data-stu-id="f8569-105">Parsing methods convert the string representation of a date and time to an equivalent [DateTime](xref:System.DateTime) object.</span></span> <span data-ttu-id="f8569-106">[Parse](xref:System.DateTime.Parse(System.String)) 和 [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) 方法會轉換數種常見的日期和時間表示。</span><span class="sxs-lookup"><span data-stu-id="f8569-106">The [Parse](xref:System.DateTime.Parse(System.String)) and [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) methods convert any of several common representations of a date and time.</span></span> <span data-ttu-id="f8569-107">[ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) 和 [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) 方法會將符合的字串表示轉換成日期和時間格式字串指定的模式。</span><span class="sxs-lookup"><span data-stu-id="f8569-107">The [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) and [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) methods convert a string representation that conforms to the pattern specified by a date and time format string.</span></span> <span data-ttu-id="f8569-108">(請參閱[標準日期和時間格式字串](standard-datetime.md)以及[自訂日期和時間格式字串](custom-datetime.md)主題。)</span><span class="sxs-lookup"><span data-stu-id="f8569-108">(See the topics on [standard date and time format strings](standard-datetime.md) and [custom date and time format strings](custom-datetime.md).)</span></span> 

<span data-ttu-id="f8569-109">剖析受到格式提供者的屬性影響，格式提供者提供的資訊為日期和時間分隔符號使用的字串，以及月份、日和紀元名稱等等。</span><span class="sxs-lookup"><span data-stu-id="f8569-109">Parsing is influenced by the properties of a format provider that supplies information such as the strings used for date and time separators, and the names of months, days, and eras.</span></span> <span data-ttu-id="f8569-110">格式提供者是目前的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件，由目前執行緒文化特性隱含提供或由剖析方法的 [IFormatProvider](xref:System.IFormatProvider) 參數明確提供。</span><span class="sxs-lookup"><span data-stu-id="f8569-110">The format provider is the current [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object, which is provided implicitly by the current thread culture or explicitly by the [IFormatProvider](xref:System.IFormatProvider) parameter of a parsing method.</span></span> <span data-ttu-id="f8569-111">在 [IFormatProvider](xref:System.IFormatProvider) 參數中指定表示文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件，或指定 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="f8569-111">For the [IFormatProvider](xref:System.IFormatProvider) parameter, specify a [CultureInfo](xref:System.Globalization.CultureInfo) object, which represents a culture, or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object.</span></span> 

<span data-ttu-id="f8569-112">要剖析的日期表示字串，必須包含月份以及至少天或年。</span><span class="sxs-lookup"><span data-stu-id="f8569-112">The string representation of a date to be parsed must include the month and at least a day or year.</span></span> <span data-ttu-id="f8569-113">時間的字串表示必須包含小時，以及至少分鐘或 AM/PM 指示項。</span><span class="sxs-lookup"><span data-stu-id="f8569-113">The string representation of a time must include the hour and at least minutes or the AM/PM designator.</span></span> <span data-ttu-id="f8569-114">但若有可能，剖析會為省略的元件提供預設值。</span><span class="sxs-lookup"><span data-stu-id="f8569-114">However, parsing supplies default values for omitted components if possible.</span></span> <span data-ttu-id="f8569-115">遺漏日期預設為目前的日期，遺漏的年份預設為目前的年份，遺漏的某月某日預設為該月第一天，而遺漏的時間預設為午夜。</span><span class="sxs-lookup"><span data-stu-id="f8569-115">A missing date defaults to the current date, a missing year defaults to the current year, a missing day of the month defaults to the first day of the month, and a missing time defaults to midnight.</span></span> 

<span data-ttu-id="f8569-116">如果字串表示只指定時間，剖析會傳回 [DateTime](xref:System.DateTime) 物件及設定為 [Today](xref:System.DateTime.Today) 屬性對應值的其 [Year](xref:System.DateTime.Year)、[Month](xref:System.DateTime.Month) 及 [Day](xref:System.DateTime.Day) 屬性。</span><span class="sxs-lookup"><span data-stu-id="f8569-116">If the string representation specifies only a time, parsing returns a [DateTime](xref:System.DateTime) object with its [Year](xref:System.DateTime.Year), [Month](xref:System.DateTime.Month), and [Day](xref:System.DateTime.Day) properties set to the corresponding values of the [Today](xref:System.DateTime.Today) property.</span></span> <span data-ttu-id="f8569-117">不過，如果剖析方法中指定了 [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) 常數，則產生的 year、month 及 day 屬性都會設成值 1。</span><span class="sxs-lookup"><span data-stu-id="f8569-117">However, if the [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) constant is specified in the parsing method, the resulting year, month, and day properties are set to the value 1.</span></span>

<span data-ttu-id="f8569-118">除了日期和時間元件外，日期和時間的字串表示可以包含表示時間與國際標準時間 (UTC) 差的位移。</span><span class="sxs-lookup"><span data-stu-id="f8569-118">In addition to a date and a time component, the string representation of a date and time can include an offset that indicates how much the time differs from Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="f8569-119">例如，字串 "2/14/2007 5:32:00 -7:00" 定義的時間比 UTC 早 7 個小時。</span><span class="sxs-lookup"><span data-stu-id="f8569-119">For example, the string "2/14/2007 5:32:00 -7:00" defines a time that is seven hours earlier than UTC.</span></span> <span data-ttu-id="f8569-120">如果時間的字串表示中省略了位移，剖析會傳回 [DateTime](xref:System.DateTime) 物件及其設為 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 的 [Kind](xref:System.DateTime.Kind) 屬性。</span><span class="sxs-lookup"><span data-stu-id="f8569-120">If an offset is omitted from the string representation of a time, parsing returns a [DateTime](xref:System.DateTime) object with its [Kind](xref:System.DateTime.Kind) property set to [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span></span> <span data-ttu-id="f8569-121">如果指定了位移，剖析會傳回 [DateTime](xref:System.DateTime) 物件及其設為 [Local](xref:System.DateTimeKind.Local) 的 [Kind](xref:System.DateTime.Kind) 屬性，且其值會調整成您電腦的當地時區。</span><span class="sxs-lookup"><span data-stu-id="f8569-121">If an offset is specified, parsing returns a [DateTime](xref:System.DateTime) object with its [Kind](xref:System.DateTime.Kind) property set to [Local](xref:System.DateTimeKind.Local) and its value adjusted to the local time zone of your machine.</span></span> <span data-ttu-id="f8569-122">您可以使用 [DateTimeStyles](xref:System.Globalization.DateTimeStyles) 常數及剖析方法修改此行為。</span><span class="sxs-lookup"><span data-stu-id="f8569-122">You can modify this behavior by using a [DateTimeStyles](xref:System.Globalization.DateTimeStyles) constant with the parsing method.</span></span>

<span data-ttu-id="f8569-123">格式提供者也可以用來解譯不明確的數值日期。</span><span class="sxs-lookup"><span data-stu-id="f8569-123">The format provider is also used to interpret an ambiguous numeric date.</span></span> <span data-ttu-id="f8569-124">例如，在字串 "02/03/04" 中，不清楚那個日期元件表示月、日和年。</span><span class="sxs-lookup"><span data-stu-id="f8569-124">For example, it is not clear which components of the date represented by the string "02/03/04" are the month, day, and year.</span></span> <span data-ttu-id="f8569-125">這種情況下，就會根據格式提供者中的相似日期格式順序來解譯元件。</span><span class="sxs-lookup"><span data-stu-id="f8569-125">In this case, the components are interpreted according to the order of similar date formats in the format provider.</span></span> 

## <a name="parse"></a><span data-ttu-id="f8569-126">剖析</span><span class="sxs-lookup"><span data-stu-id="f8569-126">Parse</span></span>

<span data-ttu-id="f8569-127">下面的程式碼範例會示範如何使用 `Parse` 方法將字串轉換成 `DateTime`。</span><span class="sxs-lookup"><span data-stu-id="f8569-127">The following code example illustrates the use of the `Parse` method to convert a string into a `DateTime`.</span></span> <span data-ttu-id="f8569-128">本例會使用與目前執行緒相關聯的文化特性執行剖析。</span><span class="sxs-lookup"><span data-stu-id="f8569-128">This example uses the culture associated with the current thread to perform the parse.</span></span> <span data-ttu-id="f8569-129">如果與目前文化特性相關聯的 [CultureInfo](xref:System.Globalization.CultureInfo) 無法剖析輸入的字串，則會擲回 [FormatException](xref:System.FormatException)。</span><span class="sxs-lookup"><span data-stu-id="f8569-129">If the [CultureInfo](xref:System.Globalization.CultureInfo) associated with the current culture cannot parse the input string, a [FormatException](xref:System.FormatException) is thrown.</span></span>

```csharp
string MyString = "Jan 1, 2009";
DateTime MyDateTime = DateTime.Parse(MyString);
Console.WriteLine(MyDateTime);
// Displays the following output on a system whose culture is en-US:
//       1/1/2009 12:00:00 AM
```

```vb
Dim MyString As String = "Jan 1, 2009"
Dim MyDateTime As DateTime = DateTime.Parse(MyString)
Console.WriteLine(MyDateTime)
' Displays the following output on a system whose culture is en-US:
'       1/1/2009 12:00:00 AM
```

<span data-ttu-id="f8569-130">您也可以指定一個設為該物件定義的文化特性之一的 `CultureInfo`，或者指定 [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) 屬性傳回的標準 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件之一。</span><span class="sxs-lookup"><span data-stu-id="f8569-130">You can also specify a `CultureInfo` set to one of the cultures defined by that object, or you can specify one of the standard [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) objects returned by the [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) property.</span></span> <span data-ttu-id="f8569-131">下列程式碼範例使用格式提供者將德文字串剖析成 `DateTime`。</span><span class="sxs-lookup"><span data-stu-id="f8569-131">The following code example uses a format provider to parse a German string into a `DateTime`.</span></span> <span data-ttu-id="f8569-132">代表 de-DE 文化特性的 `CultureInfo` 是由剖析中的字串定義及傳遞，以確保成功剖析這個特定的字串。</span><span class="sxs-lookup"><span data-stu-id="f8569-132">A `CultureInfo` representing the de-DE culture is defined and passed with the string being parsed to ensure successful parsing of this particular string.</span></span> <span data-ttu-id="f8569-133">這可排除 `CurrentThread` 的 `CurrentCulture` 有任何設定。</span><span class="sxs-lookup"><span data-stu-id="f8569-133">This precludes whatever setting is in the `CurrentCulture` of the `CurrentThread`.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output:
//       6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

<span data-ttu-id="f8569-134">不過，雖然您可以使用 [Parse](xref:System.DateTime.Parse(System.String)) 方法的多載指定自訂的格式提供者，此方法卻不支援使用非標準的格式提供者。</span><span class="sxs-lookup"><span data-stu-id="f8569-134">However, although you can use overloads of the [Parse](xref:System.DateTime.Parse(System.String)) method to specify custom format providers, the method does not support the use of non-standard format providers.</span></span> <span data-ttu-id="f8569-135">若要剖析以非標準格式表示的日期和時間，請改用 [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) 方法。</span><span class="sxs-lookup"><span data-stu-id="f8569-135">To parse a date and time expressed in a non-standard format, use the [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method instead.</span></span>

<span data-ttu-id="f8569-136">下列程式碼範例使用 [DateTimeStyles](xref:System.Globalization.DateTimeStyles) 列舉，指定目前的日期和時間資訊不應加入字串不定義的欄位 `DateTime` 中。</span><span class="sxs-lookup"><span data-stu-id="f8569-136">The following code example uses the [DateTimeStyles](xref:System.Globalization.DateTimeStyles) enumeration to specify that the current date and time information should not be added to the `DateTime` for fields that the string does not define.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo, 
                                           DateTimeStyles.NoCurrentDateDefault);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output if the current culture is en-US:
//      6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

## <a name="parseexact"></a><span data-ttu-id="f8569-137">ParseExact</span><span class="sxs-lookup"><span data-stu-id="f8569-137">ParseExact</span></span>

<span data-ttu-id="f8569-138">[DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) 方法會將符合指定字串模式的字串轉換成 `DateTime` 物件。</span><span class="sxs-lookup"><span data-stu-id="f8569-138">The [DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method converts a string that conforms to a specified string pattern to a `DateTime` object.</span></span> <span data-ttu-id="f8569-139">當不是指定格式的字串傳遞至這個方法時，就會擲回 [FormatException](xref:System.FormatException)。</span><span class="sxs-lookup"><span data-stu-id="f8569-139">When a string that is not of the form specified is passed to this method, a [FormatException](xref:System.FormatException) is thrown.</span></span> <span data-ttu-id="f8569-140">您可以指定標準日期和時間格式指定名稱的其中之一，或自訂日期和時間格式指定名稱的有限組合。</span><span class="sxs-lookup"><span data-stu-id="f8569-140">You can specify one of the standard date and time format specifiers or a limited combination of the custom date and time format specifiers.</span></span> <span data-ttu-id="f8569-141">使用自訂格式指定名稱，您有機會建構自訂的辨識字串。</span><span class="sxs-lookup"><span data-stu-id="f8569-141">Using the custom format specifiers, it is possible for you to construct a custom recognition string.</span></span> <span data-ttu-id="f8569-142">如需指定名稱的說明，請參閱[標準日期和時間格式字串](standard-datetime.md)以及[自訂日期和時間格式字串](custom-datetime.md)主題。</span><span class="sxs-lookup"><span data-stu-id="f8569-142">For an explanation of the specifiers, see the topics on [standard date and time format strings](standard-datetime.md) and [custom date and time format strings](custom-datetime.md).</span></span> 

<span data-ttu-id="f8569-143">每個 [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) 方法的多載也都有 [IFormatProvider](xref:System.IFormatProvider) 參數，通常提供有關格式字串的特定文化特性資訊。</span><span class="sxs-lookup"><span data-stu-id="f8569-143">Each overload of the [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method also has an [IFormatProvider](xref:System.IFormatProvider) parameter that typically provides culture-specific information about the formatting of the string.</span></span> <span data-ttu-id="f8569-144">此 [IFormatProvider](xref:System.IFormatProvider) 物件通常是代表標準文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件，或 [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) 屬性所傳回的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="f8569-144">Typically, this [IFormatProvider](xref:System.IFormatProvider) object is a [CultureInfo](xref:System.Globalization.CultureInfo) object that represents a standard culture or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that is returned by the [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) property.</span></span> <span data-ttu-id="f8569-145">不過，不同於其他日期和時間剖析函式，此方法也支援定義非標準日期和時間格式的 [IFormatProvider](xref:System.IFormatProvider)。</span><span class="sxs-lookup"><span data-stu-id="f8569-145">However, unlike the other date and time parsing functions, this method also supports an [IFormatProvider](xref:System.IFormatProvider) that defines a non-standard date and time format.</span></span> 

<span data-ttu-id="f8569-146">在下列程式碼範例中，`ParseExact` 方法接到了要剖析的字串物件，後面跟著格式指定名稱和 `CultureInfo` 物件。</span><span class="sxs-lookup"><span data-stu-id="f8569-146">In the following code example, the `ParseExact` method is passed a string object to parse, followed by a format specifier, followed by a `CultureInfo` object.</span></span> <span data-ttu-id="f8569-147">此 `ParseExact` 方法只能剖析以 en-US 文化特性展現完整日期模式的字串。</span><span class="sxs-lookup"><span data-stu-id="f8569-147">This `ParseExact` method can only parse strings that exhibit the long date pattern in the en-US culture.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("en-US");
      string[] MyString = {" Friday, April 10, 2009", "Friday, April 10, 2009"};
      foreach (string dateString in MyString)
      {
         try {
            DateTime MyDateTime = DateTime.ParseExact(dateString, "D", MyCultureInfo);
            Console.WriteLine(MyDateTime);
         }
         catch (FormatException) {
            Console.WriteLine("Unable to parse '{0}'", dateString);
         }
      }
   }
}
// The example displays the following output:
//       Unable to parse ' Friday, April 10, 2009'
//       4/10/2009 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("en-US")
      Dim MyString() As String = {" Friday, April 10, 2009", "Friday, April 10, 2009"}
      For Each dateString As String In MyString
         Try
            Dim MyDateTime As DateTime = DateTime.ParseExact(dateString, "D", _
                                                             MyCultureInfo)
            Console.WriteLine(MyDateTime)
         Catch e As FormatException
            Console.WriteLine("Unable to parse '{0}'", dateString)
         End Try
      Next
   End Sub
End Module
' The example displays the following output:
'       Unable to parse ' Friday, April 10, 2009'
'       4/10/2009 12:00:00 AM
```

## <a name="see-also"></a><span data-ttu-id="f8569-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8569-148">See Also</span></span>

[<span data-ttu-id="f8569-149">在 .NET 中剖析字串</span><span class="sxs-lookup"><span data-stu-id="f8569-149">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="f8569-150">在 .NET 中格式化類型</span><span class="sxs-lookup"><span data-stu-id="f8569-150">Formatting types in .NET</span></span>](formatting-types.md)

[<span data-ttu-id="f8569-151">在 .NET 中轉換類型</span><span class="sxs-lookup"><span data-stu-id="f8569-151">Type conversion in .NET</span></span>](type-conversion.md)


