---
title: "標準日期和時間格式字串"
description: "標準日期和時間格式字串"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: be239871-10cc-4949-b548-200bb260630a
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 56da9671a0849b0f0a94d8881cdc28e70bcf8549

---

# <a name="standard-date-and-time-format-strings"></a>標準日期和時間格式字串

標準日期和時間格式字串使用單一格式規範，定義日期和時間值的文字表示。 凡包含多個字元 (包括空白字元) 的日期與時間格式字串，都會被解譯為自訂日期與時間格式字串。如需詳細資訊，請參閱[自訂日期與時間格式字串](custom-datetime.md)。 標準或自訂格式字串有兩種使用方式：

* 定義執行格式化作業後所產生的字串。

* 定義可藉由剖析作業轉換成 [DateTime](xref:System.DateTime) 或 [DateTimeOffset](xref:System.DateTimeOffset) 值的日期和時間值的文字表示。

標準日期和時間格式字串可以與 [DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 值搭配使用。 

下表描述標準日期和時間的格式規範。 除非特別註明，否則特定標準日期和時間格式規範會產生相同的字串表示，無論搭配使用 [DateTime](xref:System.DateTime) 或 [DateTimeOffset](xref:System.DateTimeOffset) 值皆然。 如需使用標準日期和時間格式字串的詳細資訊，請參閱[備註](#notes)一節。

格式規範 | 描述 | 範例
---------------- | ----------- | --------
"d" | 簡短日期模式。 | `2009-06-15T13:45:30 -> 6/15/2009 (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)`; `2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)`
"D" | 完整日期模式。 | `2009-06-15T13:45:30 -> Monday, June 15, 2009 (en-US)`; `2009-06-15T13:45:30 -> 15 июня 2009 г. (ru-RU)`; `2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)`
"f" | 完整日期/時間模式 (簡短時間)。 | `2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 13:45 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)`
"F" | 完整日期/時間模式 (完整時間)。 | `2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 13:45:30 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)`
"g" | 一般日期/時間模式 (簡短時間)。 | `2009-06-15T13:45:30 -> 6/15/2009 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)`; `2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)`
"G" | 一般日期/時間模式 (完整時間)。 | `2009-06-15T13:45:30 -> 6/15/2009 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)`; `2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)`
"M", "m' | 月/日模式。 | `2009-06-15T13:45:30 -> June 15 (en-US)`; `2009-06-15T13:45:30 -> 15. juni (da-DK)`; `2009-06-15T13:45:30 -> 15 Juni (id-ID)`
"O"、"o" | 來回日期/時間模式。 | [DateTime](xref:System.DateTime) 值：`2009-06-15T13:45:30 (DateTimeKind.Local) --> 2009-06-15T13:45:30.0000000-07:00`; `2009-06-15T13:45:30 (DateTimeKind.Utc) --> 2009-06-15T13:45:30.0000000Z`; `2009-06-15T13:45:30 (DateTimeKind.Unspecified) --> 2009-06-15T13:45:30.0000000`。 [DateTimeOffset](xref:System.DateTimeOffset) 值：`2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.0000000-07:00`
"R"、"r" | RFC1123 模式。 | `2009-06-15T13:45:30 -> Mon, 15 Jun 2009 20:45:30 GMT`
"s" | 可排序日期/時間模式。 | `2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30`; `2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30`
"t" | 簡短時間模式。 | `2009-06-15T13:45:30 -> 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> 13:45 (hr-HR)`; `2009-06-15T13:45:30 -> 01:45 م (ar-EG)` 
"T" | 完整時間模式。 | `2009-06-15T13:45:30 -> 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> 13:45:30 (hr-HR)`; `2009-06-15T13:45:30 -> 01:45:30 م (ar-EG)`
"u" | 國際可排序日期/時間模式。 | 具有 [DateTime](xref:System.DateTime) 值：`2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z`。 具有 [DateTime](xref:System.DateTimeOffset) 值：`2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z`
"U" | 國際完整日期/時間模式。 | `2009-06-15T13:45:30 -> Monday, June 15, 2009 8:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 20:45:30 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)`
"Y", "y" | 年月模式。 | `2009-06-15T13:45:30 -> June, 2009 (en-US)`; `2009-06-15T13:45:30 -> juni 2009 (da-DK)`; `2009-06-15T13:45:30 -> Juni 2009 (id-ID)`
任何其他單一字元 | 未知的規範。 | 會擲回 [FormatException](xref:System.FormatException) 執行階段。

## <a name="how-standard-format-strings-work"></a>標準格式字串的運作方式

在格式化作業中，標準格式字串只是自訂格式字串的別名。 使用別名來表示自訂格式字串的好處是，儘管別名保持不變，自訂格式字串本身則可有變化。 這點非常重要，因為日期和時間值的字串表示通常會因文化特性而不同。 例如，"d" 標準格式字串表示日期和時間值將使用簡短日期模式顯示。 在不因文化特性而異 (Invariant Culture) 的情況下，此模式為 "MM/dd/yyyy"。 若為 fr-FR 文化特性，則是 "dd/MM/yyyy"。 若為 ja-JP 文化特性，則是 "yyyy/MM/dd"。

如果格式化作業中的標準格式字串對應至特定文化特性的自訂格式字串，您的應用程式可以定義特定文化特性，以下列其中一種方式使用自訂格式字串：

* 您可以使用預設 (或目前的) 文化特性。 下列範例顯示的日期使用了目前文化特性的簡短日期格式。 在此例中，目前的文化特性是 en-US。 

  ```csharp
  // Display using current (en-us) culture's short date format
  DateTime thisDate = new DateTime(2008, 3, 15);
  Console.WriteLine(thisDate.ToString("d"));           // Displays 3/15/2008
  ```

  ```vb
  ' Display using current (en-us) culture's short date format
  Dim thisDate As Date = #03/15/2008#
  Console.WriteLine(thisDate.ToString("d"))     ' Displays 3/15/2008
  ```
  
* 您可以將 [CultureInfo](xref:System.Globalization.CultureInfo) 物件 (表示要使用其格式設定的文化特性) 傳遞至具有 [IFormatProvider](xref:System.IFormatProvider) 參數的方法。 下列範例顯示的日期使用了 pt-BR 文化特性的簡短日期格式。
  
  ```csharp
  // Display using pt-BR culture's short date format
  DateTime thisDate = new DateTime(2008, 3, 15);
  CultureInfo culture = new CultureInfo("pt-BR");      
  Console.WriteLine(thisDate.ToString("d", culture));  // Displays 15/3/2008
  ```

  ```vb
  ' Display using pt-BR culture's short date format
  Dim thisDate As Date = #03/15/2008#
  Dim culture As New CultureInfo("pt-BR")      
  Console.WriteLine(thisDate.ToString("d", culture))   ' Displays 15/3/2008
  ```
  
* 您可以將提供格式設定資訊的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件傳遞至具有 [IFormatProvider](xref:System.IFormatProvider) 參數的方法。 下列範例顯示的日期，是使用取自於 hr-HR 文化特性之 DateTimeFormatInfo 物件的簡短日期格式。  

  ```csharp
  // Display using date format information from hr-HR culture
  DateTime thisDate = new DateTime(2008, 3, 15);
  DateTimeFormatInfo fmt = (new CultureInfo("hr-HR")).DateTimeFormat;
  Console.WriteLine(thisDate.ToString("d", fmt));      // Displays 15.3.2008
  ```

  ```vb
  ' Display using date format information from hr-HR culture
  Dim thisDate As Date = #03/15/2008#
  Dim fmt As DateTimeFormatInfo = (New CultureInfo("hr-HR")).DateTimeFormat
  Console.WriteLine(thisDate.ToString("d", fmt))   ' Displays 15.3.2008
  ```
  
在某些情況下，標準格式字串可做為不變之長自訂格式字串的簡便縮寫。 有四個標準格式字串屬於此分類："O" (或 "o")、"R" (或 "r")、"s" 和 "u"。 這些字串相當於不因文化特性而異所定義的自訂格式字串。 它們針對日期和時間值所產生的字串表示在各文化特性中都相同。 下表提供這四種標準日期和時間格式字串的相關資訊。

標準格式字串 | 由 DateTimeFormatInfo.InvariantInfo 屬性定義 | 自訂格式字串
---------------------- | ---------------------------------------------------- | --------------------
"O" 或 "o" | 無 | yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz
"R" 或 "r" | [RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) | ddd、dd MMM yyyy HH':'mm':'ss 'GMT'
"s" | [SortableDateTime](xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern) | yyyy'-'MM'-'dd'T'HH':'mm':'ss
"u" | [UniversalSortableDateTime](xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern) | yyyy'-'MM'-'dd HH':'mm':'ss'Z'

下列各節描述 [DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 值的標準格式規範。

## <a name="the-short-date-d-format-specifier"></a>簡短日期 ("d")

"d" 標準格式規範表示由特定文化特性之 [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的 [ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) 屬性傳回的自訂格式字串為 "MM/dd/yyyy"。 

下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。
下列範例使用 "d" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008,4, 10);
Console.WriteLine(date1.ToString("d", DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays 4/10/2008                       
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("en-NZ")));
// Displays 10/04/2008                       
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("de-DE")));
// Displays 10.04.2008 
```

```vb
Dim date1 As Date = #4/10/2008#
Console.WriteLine(date1.ToString("d", DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays 4/10/2008                       
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("en-NZ")))
' Displays 10/04/2008                       
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("de-DE")))
' Displays 10.04.2008 
```

## <a name="the-long-date-d-format-specifier"></a>完整日期 ("D") 格式規範

"D" 標準格式規範表示由目前 [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "dddd, dd MMMM yyyy"。

下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。

屬性 | 說明
-------- | -----------
[LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) | 定義結果字串的整體格式。
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | 定義可顯示在結果字串中的當地語系化日期名稱。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 定義可顯示在結果字串中的當地語系化月份名稱。

下列範例使用 "D" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008, 4, 10);
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008                        
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("pt-BR")));
// Displays quinta-feira, 10 de abril de 2008                        
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("es-MX")));
// Displays jueves, 10 de abril de 2008
```

```vb
Dim date1 As Date = #4/10/2008#
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008                        
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("pt-BR")))
' Displays quinta-feira, 10 de abril de 2008                        
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("es-MX")))
' Displays jueves, 10 de abril de 2008
```

## <a name="the-full-date-short-time-f-format-specifier"></a>完整日期簡短時間 ("f") 格式規範

"f" 標準格式規範表示完整日期 ("D") 和簡短時間 ("t") 模式的組合，以空格分隔。

結果字串會受到特定 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。 由某些文化特性的 [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) 和 [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) 屬性所傳回的自訂格式規範，可能不會使用所有屬性。

屬性 | 說明
-------- | -----------
[LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) | 定義結果字串之日期元件的格式。
[ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | 定義結果字串之時間元件的格式。
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | 定義可顯示在結果字串中的當地語系化日期名稱。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 定義可顯示在結果字串中的當地語系化月份名稱。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 定義表示從午夜到中午之前時間 (12 小時制) 的字串。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 定義表示從中午到午夜之前時間 (12 小時制) 的字串。

下列範例使用 "f" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("f", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 6:30 AM                        
Console.WriteLine(date1.ToString("f", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays jeudi 10 avril 2008 06:30 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("f", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 6:30 AM                        
Console.WriteLine(date1.ToString("f", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays jeudi 10 avril 2008 06:30 
```

## <a name="the-full-date-long-time-f-format-specifier"></a>完整日期完整時間 ("F") 格式規範

"F" 標準格式規範表示由目前 [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "dddd, dd MMMM yyyy HH:mm:ss"。

下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。 由某些文化特性的 [FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) 屬性所傳回的自訂格式規範，可能不會使用所有屬性。

屬性 | 說明
-------- | -----------
[FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) | 定義結果字串的整體格式。
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | 定義可顯示在結果字串中的當地語系化日期名稱。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 定義可顯示在結果字串中的當地語系化月份名稱。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 定義表示從午夜到中午之前時間 (12 小時制) 的字串。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 定義表示從中午到午夜之前時間 (12 小時制) 的字串。

下列範例使用 "F" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("F", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("F", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays jeudi 10 avril 2008 06:30:00 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("F", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("F", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays jeudi 10 avril 2008 06:30:00 
```

## <a name="the-general-date-short-time-g-format-specifier"></a>一般日期簡短時間 ("g") 格式規範

"g" 標準格式規範表示簡短日期 ("d") 和簡短時間 ("t") 模式的組合，以空格分隔。

結果字串會受到特定 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。 由某些文化特性的 [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) 和 [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) 屬性所傳回的自訂格式規範，可能不會使用所有屬性。

屬性 | 說明
-------- | -----------
[ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) | 定義結果字串之日期元件的格式。
[ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | 定義結果字串之時間元件的格式。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 定義表示從午夜到中午之前時間 (12 小時制) 的字串。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 定義表示從中午到午夜之前時間 (12 小時制) 的字串。

下列範例使用 "g" 格式規範來顯示日期和時間值。 

``` csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("g", 
                  DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008 06:30                      
Console.WriteLine(date1.ToString("g", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 4/10/2008 6:30 AM                       
Console.WriteLine(date1.ToString("g", 
                  CultureInfo.CreateSpecificCulture("fr-BE")));
// Displays 10/04/2008 6:30 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("g", _
                  DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008 06:30                      
Console.WriteLine(date1.ToString("g", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 4/10/2008 6:30 AM                       
Console.WriteLine(date1.ToString("g", _
                  CultureInfo.CreateSpecificCulture("fr-BE")))
' Displays 10/04/2008 6:30  
```

## <a name="the-general-date-long-time-g-format-specifier"></a>一般日期完整時間 ("G") 格式規範

"G" 標準格式規範表示簡短日期 ("d") 和完整時間 ("T") 模式的組合，以空格分隔。

結果字串會受到特定 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。 由某些文化特性的 [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) 和 [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) 屬性所傳回的自訂格式規範，可能不會使用所有屬性。

屬性 | 說明
-------- | -----------
[ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) | 定義結果字串之日期元件的格式。
[LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) | 定義結果字串之時間元件的格式。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 定義表示從午夜到中午之前時間 (12 小時制) 的字串。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 定義表示從中午到午夜之前時間 (12 小時制) 的字串。

下列範例使用 "G" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("G", 
                  DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008 06:30:00
Console.WriteLine(date1.ToString("G", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 4/10/2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("G", 
                  CultureInfo.CreateSpecificCulture("nl-BE")));
// Displays 10/04/2008 6:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("G", _
                  DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008 06:30:00
Console.WriteLine(date1.ToString("G", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 4/10/2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("G", _
                  CultureInfo.CreateSpecificCulture("nl-BE")))
' Displays 10/04/2008 6:30:00                       
```

## <a name="the-month-m-m-format-specifier"></a>月 ("M"、"m") 格式規範

"M" 或 "m" 標準格式規範表示由目前 [DateTimeFormatInfo.MonthDayPattern](xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern) 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "MMMM dd"。

下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。

屬性 | 說明
-------- | -----------
[MonthDayPattern](xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern) | 定義結果字串的整體格式。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 定義可顯示在結果字串中的當地語系化月份名稱。

下列範例使用 "m" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("m", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays April 10                        
Console.WriteLine(date1.ToString("m", 
                  CultureInfo.CreateSpecificCulture("ms-MY")));
// Displays 10 April  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("m", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays April 10                        
Console.WriteLine(date1.ToString("m", _
                  CultureInfo.CreateSpecificCulture("ms-MY")))
' Displays 10 April
```

## <a name="the-round-trip-o-o-format-specifier"></a>來回行程 ("O"、"o") 格式規範

"O" 或 "o" 標準格式規範可表示使用保存時區資訊之模式的自訂日期和時間格式字串，並發出符合 ISO 8601 的結果字串。 若為 [DateTime](xref:System.DateTime) 值，此格式規範是設計來以純文字保存日期和時間值以及 [DateTime.Kind](xref:System.DateTime.Kind) 屬性。 如果將 [DateTime.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTime.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) 或 [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) 方法的 styles 參數設定為 [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind)，則可以使用這兩個方法來剖析還原格式化字串。 

"O" 或 "o" 標準格式規範對應至 DateTime 值的 "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" 自訂格式字串，也對應至 [DateTimeOffset](xref:System.DateTimeOffset) 值的 "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzzz" 自訂格式字串。 在此字串中，分隔個別字元 (例如連字號、冒號和字母 "T") 的各組單引號表示個別字元為不可變更的常值。 所有格符號不會出現在輸出字串中。 

"O" 或 "o" 標準格式規範 (以及 "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" 自訂格式字串) 利用 ISO 8601 表示時區資訊的三種方式，來保留 [DateTime](xref:System.DateTime) 值的 [Kind](xref:System.DateTime.Kind) 屬性： 

* [DateTimeKind.Local](xref:System.DateTimeKind.Local) 日期和時間值的時區元件是與 UTC 的時差 (例如，+01:00、-07:00)。 所有 DateTimeOffset 值也都是以此格式表示。 

* [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) 日期和時間值的時區元件使用 "Z" (代表零時差) 來表示 UTC。 

* [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 日期和時間值沒有時區資訊。 

因為 "O" 或 "o" 標準格式規範符合國際標準，所以使用該規範的或剖析作業一律使用不因國別而異的文化特性和西曆。 

傳遞至 [DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 的 `Parse`、`TryParse`、`ParseExact` 和 `TryParseExact` 方法的字串如果是這些格式，就可以使用 "O" 或 "o" 格式規範來剖析。 在 [DateTime](xref:System.DateTime) 物件的案例中，您呼叫的剖析多載應該也要包含 styles 參數，且值為 [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind)。 請注意，如果您呼叫剖析方法時，使用對應於 "O" 或 "o" 格式規範的自訂格式字串，將不會取得與 "O" 或 "o" 相同的結果。 這是因為使用自訂格式字串的剖析方法，無法剖析缺少時區元件或使用 "Z" 來指示 UTC 之日期和時間值的字串表示法。 

下列範例使用 "o" 格式規範，在美國太平洋時區系統上顯示一連串的 [DateTime](xref:System.DateTime) 值以及 [DateTimeOffset](xref:System.DateTimeOffset) 值。。 

```csharp
using System;

public class Example
{
   public static void Main()
   {
       DateTime dat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                   DateTimeKind.Unspecified);
       Console.WriteLine("{0} ({1}) --> {0:O}", dat, dat.Kind); 

       DateTime uDat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                    DateTimeKind.Utc);
       Console.WriteLine("{0} ({1}) --> {0:O}", uDat, uDat.Kind);

       DateTime lDat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                    DateTimeKind.Local);
       Console.WriteLine("{0} ({1}) --> {0:O}\n", lDat, lDat.Kind);

       DateTimeOffset dto = new DateTimeOffset(lDat);
       Console.WriteLine("{0} --> {0:O}", dto);
   }
}
// The example displays the following output:
//    6/15/2009 1:45:30 PM (Unspecified) --> 2009-06-15T13:45:30.0000000
//    6/15/2009 1:45:30 PM (Utc) --> 2009-06-15T13:45:30.0000000Z
//    6/15/2009 1:45:30 PM (Local) --> 2009-06-15T13:45:30.0000000-07:00
//    
//    6/15/2009 1:45:30 PM -07:00 --> 2009-06-15T13:45:30.0000000-07:00
```

```vb
Module Example
   Public Sub Main()
       Dim dat As New Date(2009, 6, 15, 13, 45, 30, 
                           DateTimeKind.Unspecified)
       Console.WriteLine("{0} ({1}) --> {0:O}", dat, dat.Kind) 

       Dim uDat As New Date(2009, 6, 15, 13, 45, 30, DateTimeKind.Utc)
       Console.WriteLine("{0} ({1}) --> {0:O}", uDat, uDat.Kind)

       Dim lDat As New Date(2009, 6, 15, 13, 45, 30, DateTimeKind.Local)
       Console.WriteLine("{0} ({1}) --> {0:O}", lDat, lDat.Kind)
       Console.WriteLine()

       Dim dto As New DateTimeOffset(lDat)
       Console.WriteLine("{0} --> {0:O}", dto)
   End Sub
End Module
' The example displays the following output:
'    6/15/2009 1:45:30 PM (Unspecified) --> 2009-06-15T13:45:30.0000000
'    6/15/2009 1:45:30 PM (Utc) --> 2009-06-15T13:45:30.0000000Z
'    6/15/2009 1:45:30 PM (Local) --> 2009-06-15T13:45:30.0000000-07:00
'    
'    6/15/2009 1:45:30 PM -07:00 --> 2009-06-15T13:45:30.0000000-07:00
```

下列範例使用 "o" 格式規範建立格式化字串，然後呼叫日期和時間 `Parse` 方法來還原原始日期和時間值。

```csharp
// Round-trip DateTime values.
DateTime originalDate, newDate;
string dateString;
// Round-trip a local time.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 10, 6, 30, 0), DateTimeKind.Local);
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);
// Round-trip a UTC time.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 12, 9, 30, 0), DateTimeKind.Utc);                  
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);
// Round-trip time in an unspecified time zone.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 13, 12, 30, 0), DateTimeKind.Unspecified);                  
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);

// Round-trip a DateTimeOffset value.
DateTimeOffset originalDTO = new DateTimeOffset(2008, 4, 12, 9, 30, 0, new TimeSpan(-8, 0, 0));
dateString = originalDTO.ToString("o");
DateTimeOffset newDTO = DateTimeOffset.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} to {1}.", originalDTO, newDTO);
// The example displays the following output:
//    Round-tripped 4/10/2008 6:30:00 AM Local to 4/10/2008 6:30:00 AM Local.
//    Round-tripped 4/12/2008 9:30:00 AM Utc to 4/12/2008 9:30:00 AM Utc.
//    Round-tripped 4/13/2008 12:30:00 PM Unspecified to 4/13/2008 12:30:00 PM Unspecified.
//    Round-tripped 4/12/2008 9:30:00 AM -08:00 to 4/12/2008 9:30:00 AM -08:00.
```

```vb
' Round-trip DateTime values.
Dim originalDate, newDate As Date
Dim dateString As String
' Round-trip a local time.
originalDate = Date.SpecifyKind(#4/10/2008 6:30AM#, DateTimeKind.Local)
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)
' Round-trip a UTC time.
originalDate = Date.SpecifyKind(#4/12/2008 9:30AM#, DateTimeKind.Utc)                  
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)
' Round-trip time in an unspecified time zone.
originalDate = Date.SpecifyKind(#4/13/2008 12:30PM#, DateTimeKind.Unspecified)                  
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)

' Round-trip a DateTimeOffset value.
Dim originalDTO As New DateTimeOffset(#4/12/2008 9:30AM#, New TimeSpan(-8, 0, 0))
dateString = originalDTO.ToString("o")
Dim newDTO As DateTimeOffset = DateTimeOffset.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} to {1}.", originalDTO, newDTO)
' The example displays the following output:
'    Round-tripped 4/10/2008 6:30:00 AM Local to 4/10/2008 6:30:00 AM Local.
'    Round-tripped 4/12/2008 9:30:00 AM Utc to 4/12/2008 9:30:00 AM Utc.
'    Round-tripped 4/13/2008 12:30:00 PM Unspecified to 4/13/2008 12:30:00 PM Unspecified.
'    Round-tripped 4/12/2008 9:30:00 AM -08:00 to 4/12/2008 9:30:00 AM -08:00.
```

## <a name="the-rfc1123-r-r-format-specifier"></a>RFC1123 ("R"、"r") 格式規範

"R" 或 "r" 標準格式規範表示由 [DateTimeFormatInfo.RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) 屬性所定義的自訂日期和時間格式字串。 此模式反映已定義的標準，且屬性為唯讀。 因此，不論所使用的文化特性或提供的格式提供者為何，它一定會是相同的。 自訂格式字串為 "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'"。 使用這個標準格式規範時，格式或剖析作業一律使用不因文化特性而異。

在表示不因文化特性而異之 [DateTimeFormatInfo.InvariantInfo](xref:System.Globalization.DateTimeFormatInfo.InvariantInfo) 屬性所傳回的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件中，有下列屬性會影響結果字串。

屬性 | 說明
-------- | -----------
[RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) | 定義結果字串的格式。
[AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) | 定義可顯示在結果字串中的縮寫日期名稱。
[AbbreviatedMonthNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames) | 定義可顯示在結果字串中的縮寫月份名稱。

雖然 RFC 1123 標準以國際標準時間 (UTC) 來表示時間，但對於要進行格式設定的 [DateTime](xref:System.DateTime) 物件，格式設定操作並不會修改這些物件的值。 因此，您必須先呼叫 [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) 方法將 [DateTime](xref:System.DateTime) 值轉換成 UTC，才能執行格式設定操作。 相較之下，[DateTimeOffset](xref:System.DateTimeOffset) 值會自動執行這項轉換，因此在格式設定操作之前，不需要呼叫 [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) 方法。 

下列範例使用 "r" 格式規範，在美國太平洋時區系統上顯示 [DateTime](xref:System.DateTime) 以及 [DateTimeOffset](xref:System.DateTimeOffset) 值。。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
DateTimeOffset dateOffset = new DateTimeOffset(date1, 
                            TimeZoneInfo.Local.GetUtcOffset(date1));
Console.WriteLine(date1.ToUniversalTime().ToString("r"));
// Displays Thu, 10 Apr 2008 13:30:00 GMT                       
Console.WriteLine(dateOffset.ToUniversalTime().ToString("r"));
// Displays Thu, 10 Apr 2008 13:30:00 GMT  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Dim dateOffset As New DateTimeOffset(date1, TimeZoneInfo.Local.GetUtcOFfset(date1))
Console.WriteLine(date1.ToUniversalTime.ToString("r"))
' Displays Thu, 10 Apr 2008 13:30:00 GMT                       
Console.WriteLine(dateOffset.ToUniversalTime.ToString("r"))
' Displays Thu, 10 Apr 2008 13:30:00 GMT
```

## <a name="the-sortable-s-format-specifier"></a>可排序 ("s") 格式規範

"s" 標準格式規範表示由 [DateTimeFormatInfo.SortableDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern) 屬性所定義的自訂日期和時間格式字串。 此模式反映已定義的標準 (ISO 8601)，且屬性為唯讀。 因此，不論所使用的文化特性或提供的格式提供者為何，它一定會是相同的。 自訂格式字串為 "yyyy'-'MM'-'dd'T'HH':'mm':'ss"。

 "s" 格式規範的目的在於產生結果字串時，能夠根據日期和時間值，一致地以遞增或遞減順序排序。 如此一來，雖然 "s" 標準格式規範會以一致的格式來表示日期和時間值，但是格式設定操作不會修改日期和時間物件的值 (該值已進行可反映其 [DateTime.Kind](xref:System.DateTime.Kind) 屬性或其 [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) 值的格式設定)。 例如，格式化日期和時間值 2014-11-15T18:32:17+00:00 和 2014-11-15T18:32:17+08:00 所產生的結果字串相同。 

使用這個標準格式規範時，格式或剖析作業一律使用不因文化特性而異。 

下列範例使用 "s" 格式規範，在美國太平洋時區系統上顯示 [DateTime](xref:System.DateTime) 以及 [DateTimeOffset](xref:System.DateTimeOffset) 值。。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("s"));
// Displays 2008-04-10T06:30:00
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("s"))
' Displays 2008-04-10T06:30:00 
```

## <a name="the-short-time-t-format-specifier"></a>簡短時間 ("t") 格式規範

"t" 標準格式規範表示由目前 [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "HH:mm"。

結果字串會受到特定 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。 由某些文化特性的 [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) 屬性所傳回的自訂格式規範，可能不會使用所有屬性。

屬性 | 說明
-------- | -----------
[DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | 定義結果字串之時間元件的格式。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 定義表示從午夜到中午之前時間 (12 小時制) 的字串。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 定義表示從中午到午夜之前時間 (12 小時制) 的字串。

下列範例使用 "t" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("t", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 6:30 AM                        
Console.WriteLine(date1.ToString("t", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays 6:30  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("t", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 6:30 AM                        
Console.WriteLine(date1.ToString("t", _
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays 6:30
```

## <a name="the-long-time-t-format-specifier"></a>完整時間 ("T") 格式規範

"T" 標準格式規範表示由特定文化特性之 [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "HH:mm:ss"。

下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。 由某些文化特性的 [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) 屬性所傳回的自訂格式規範，可能不會使用所有屬性。

屬性 | 說明
-------- | -----------
[LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) | 定義結果字串之時間元件的格式。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 定義表示從午夜到中午之前時間 (12 小時制) 的字串。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 定義表示從中午到午夜之前時間 (12 小時制) 的字串。

下列範例使用 "T" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("T", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 6:30:00 AM                       
Console.WriteLine(date1.ToString("T", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays 6:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("T", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 6:30:00 AM                       
Console.WriteLine(date1.ToString("T", _
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays 6:30:00 
```

## <a name="the-universal-sortable-u-format-specifier"></a>國際可排序 ("u") 格式規範

"u" 標準格式規範表示由 [DateTimeFormatInfo.UniversalSortableDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern) 屬性所定義的自訂日期和時間格式字串。 此模式反映已定義的標準，且屬性為唯讀。 因此，不論所使用的文化特性或提供的格式提供者為何，它一定會是相同的。 自訂格式字串為 "yyyy'-'MM'-'dd HH':'mm':'ss'Z'"。 使用這個標準格式規範時，格式或剖析作業一律使用不因文化特性而異。 

雖然結果字串應該以國際標準時間 (UTC) 來表示時間，但在格式設定操作期間，原始 [DateTime](xref:System.DateTime) 值不會執行任何轉換。 因此，您必須先呼叫 [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) 方法將 [DateTime](xref:System.DateTime) 值轉換成 UTC，才能對其執行格式設定。 相較之下，[DateTimeOffset](xref:System.DateTimeOffset) 值會自動執行這項轉換，因此在格式設定操作之前，不需要呼叫 [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) 方法。   

下列範例使用 "u" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToUniversalTime().ToString("u"));
// Displays 2008-04-10 13:30:00Z
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToUniversalTime.ToString("u"))
' Displays 2008-04-10 13:30:00Z                       
```

## <a name="the-universal-full-u-format-specifier"></a>國際完整 ("U") 格式規範

"U" 標準格式規範表示由指定文化特性之 [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) 屬性所定義的自訂日期和時間格式字串。 此模式與 "F" 模式相同。 不過，[DateTime](xref:System.DateTime) 值在受到格式設定之前會自動轉換為 UTC。

下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。 由某些文化特性的 [FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) 屬性所傳回的自訂格式規範，可能不會使用所有屬性。

屬性 | 說明
-------- | -----------
[FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) | 定義結果字串的整體格式。
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | 定義可顯示在結果字串中的當地語系化日期名稱。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 定義可顯示在結果字串中的當地語系化月份名稱。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 定義表示從午夜到中午之前時間 (12 小時制) 的字串。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 定義表示從中午到午夜之前時間 (12 小時制) 的字串。

[DateTimeOffset](xref:System.DateTimeOffset) 類型不支援 "U" 格式規範，如果使用它來格式設定 [DateTimeOffset](xref:System.DateTimeOffset) 值，則會擲回 [FormatException](xref:System.FormatException)。

下列範例使用 "U" 格式規範來顯示日期和時間值。

``` csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("U", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 1:30:00 PM                       
Console.WriteLine(date1.ToString("U", 
                  CultureInfo.CreateSpecificCulture("sv-FI")));
// Displays den 10 april 2008 13:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("U", CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 1:30:00 PM                       
Console.WriteLine(date1.ToString("U", CultureInfo.CreateSpecificCulture("sv-FI")))
' Displays den 10 april 2008 13:30:00                       
```

## <a name="the-year-month-y-y-format-specifier"></a>年月 ("Y"、"y") 格式規範

"Y" 或 "y" 標準格式規範表示由指定文化特性之 [DateTimeFormatInfo.YearMonthPattern](xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern) 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "yyyy MMMM"。

下表列出可控制傳回字串之格式設定的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性。

屬性 | 說明
-------- | -----------
[YearMonthPattern](xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern) | 定義結果字串的整體格式。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 定義可顯示在結果字串中的當地語系化月份名稱。

下列範例使用 "y" 格式規範來顯示日期和時間值。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("Y", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays April, 2008                       
Console.WriteLine(date1.ToString("y", 
                  CultureInfo.CreateSpecificCulture("af-ZA")));
// Displays April 2008 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("Y", CultureInfo.CreateSpecificCulture("en-US")))
' Displays April, 2008                       
Console.WriteLine(date1.ToString("y", CultureInfo.CreateSpecificCulture("af-ZA")))
' Displays April 2008
```                       

## <a name="notes"></a>附註

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo 屬性

格式設定會受到目前 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性的影響，而此屬性是由目前執行緒文化特性隱含提供或由叫用格式設定之方法的 [IFormatProvider](xref:System.IFormatProvider) 參數明確提供。 針對 [IFormatProvider](xref:System.IFormatProvider) 參數，您的應用程式應指定代表文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件，或是指定代表特定文化特性之日期和時間格式設定慣例的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。 許多標準日期和時間格式規範都是格式設定模式的別名，這些模式是由目前 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件的屬性所定義。 您的應用程式可以變更對應 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 屬性的對應日期和時間格式模式，藉此改變某些標準日期和時間格式規範所產生的結果。

## <a name="see-also"></a>請參閱

[格式化類型](formatting-types.md)

[自訂日期與時間格式字串](custom-datetime.md)




<!--HONumber=Nov16_HO3-->


