---
title: "標準 TimeSpan 格式字串"
description: "標準 TimeSpan 格式字串"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 4e0f02f1-4abd-47b5-8995-5c3ff45b0ce1
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 4e6b58cd8b29b4a9d46bd43a03c1e8c6c45dfcaa
ms.lasthandoff: 03/02/2017

---

# <a name="standard-timespan-format-strings"></a>標準 TimeSpan 格式字串

標準 [TimeSpan](xref:System.TimeSpan) 格式字串是使用單一格式規範來定義 [TimeSpan](xref:System.TimeSpan) 值的文字表示，而該值為格式設定作業產生的結果。 任何包含一個以上字元 (包含空格) 的格式字串，都會解譯為自訂 [TimeSpan](xref:System.TimeSpan) 格式字串。 如需詳細資訊，請參閱[自訂 TimeSpan 格式字串](custom-timespan.md)。

[TimeSpan](xref:System.TimeSpan) 值的字串表示有下列產生方式：藉由呼叫 [TimeSpan.ToString](xref:System.TimeSpan.ToString) 方法的多載產生，以及藉由支援複合格式化的方法所產生，例如 [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))。 如需詳細資訊，請參閱[格式化類型](formatting-types.md)和[複合格式設定](composite-format.md)。 下列範例說明格式設定作業中的標準格式字串用法。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan duration = new TimeSpan(1, 12, 23, 62);
      string output = "Time of Travel: " + duration.ToString("c");
      Console.WriteLine(output);

      Console.WriteLine("Time of Travel: {0:c}", duration); 
   }
}
// The example displays the following output:
//       Time of Travel: 1.12:24:02
//       Time of Travel: 1.12:24:02
```

```vb
Module Example
   Public Sub Main()
      Dim duration As New TimeSpan(1, 12, 23, 62)
      Dim output As String = "Time of Travel: " + duration.ToString("c")
      Console.WriteLine(output)

      Console.WriteLine("Time of Travel: {0:c}", duration) 
   End Sub
End Module
' The example displays the following output:
'       Time of Travel: 1.12:24:02
'       Time of Travel: 1.12:24:02
```

[TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) 和 [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)) 方法也會使用標準 [TimeSpan](xref:System.TimeSpan) 格式字串，來定義用於剖析作業之輸入字串的必要格式 (剖析會將值的字串表示轉換成該值)。下列範例說明剖析作業中標準格式字串的用法。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value = "1.03:14:56.1667";
      TimeSpan interval;
      try {
         interval = TimeSpan.ParseExact(value, "c", null);
         Console.WriteLine("Converted '{0}' to {1}", value, interval);
      }   
      catch (FormatException) {
         Console.WriteLine("{0}: Bad Format", value);
      }   
      catch (OverflowException) {
         Console.WriteLine("{0}: Out of Range", value);
      }

      if (TimeSpan.TryParseExact(value, "c", null, out interval))
         Console.WriteLine("Converted '{0}' to {1}", value, interval);
      else
         Console.WriteLine("Unable to convert {0} to a time interval.", 
                           value);
   }
}
// The example displays the following output:
//       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
//       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
```

```vb
Module Example
   Public Sub Main()
      Dim value As String = "1.03:14:56.1667"
      Dim interval As TimeSpan
      Try
         interval = TimeSpan.ParseExact(value, "c", Nothing)
         Console.WriteLine("Converted '{0}' to {1}", value, interval)
      Catch e As FormatException
         Console.WriteLine("{0}: Bad Format", value)
      Catch e As OverflowException
         Console.WriteLine("{0}: Out of Range", value)
      End Try

      If TimeSpan.TryParseExact(value, "c", Nothing, interval) Then
         Console.WriteLine("Converted '{0}' to {1}", value, interval)
      Else
         Console.WriteLine("Unable to convert {0} to a time interval.", 
                           value)
      End If                
   End Sub
End Module
' The example displays the following output:
'       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
'       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
```

下表列出標準時間間隔格式規範。

格式規範 | 名稱 | 描述 | 範例
---------------- | ---- | ----------- | --------
"c" | 常數 (非變異) 格式 | 這個規範不區分文化特性。 格式為 [-][d’.’]hh’:’mm’:’ss[‘.’fffffff] \ ("t" 與 "T" 格式字串會產生相同的結果)。 | `TimeSpan.Zero -> 00:00:00`; `New TimeSpan(0, 0, 30, 0) -> 00:30:00`; `New TimeSpan(3, 17, 25, 30, 500) -> 3.17:25:30.5000000`
"g" | 一般短格式 | 這個規範只會輸出需要的內容。 它會區分文化特性，並採用 [-][d’:’]h’:’mm’:’ss[.FFFFFFF] 格式。 | `New TimeSpan(1, 3, 16, 50, 500) -> 1:3:16:50.5 (en-US)`; `New TimeSpan(1, 3, 16, 50, 500) -> 1:3:16:50,5 (fr-FR)`; `New TimeSpan(1, 3, 16, 50, 599) -> 1:3:16:50.599 (en-US)`; `New TimeSpan(1, 3, 16, 50, 599) -> 1:3:16:50,599 (fr-FR)`
"G" | 一般長格式 | 這個規範一律會輸出天數和七個小數。 它會區分文化特性，並採用 [-]d’:’hh’:’mm’:’ss.fffffff 格式。 | `New TimeSpan(18, 30, 0) -> 0:18:30:00.0000000 (en-US)`; `New TimeSpan(18, 30, 0) -> 0:18:30:00,0000000 (fr-FR)` 

## <a name="the-constant-c-format-specifier"></a>常數 ("c") 格式規範

"c" 格式規範會以下列形式傳回 [TimeSpan](xref:System.TimeSpan) 值的字串表示：

[-][_d_.]_hh_:_mm_:_ss_[._fffffff_]

在方括號 ([ 和 ]) 中的項目是選擇性的項目。 句號 (.) 和冒號 (:) 是常值的符號。 下表說明其餘項目。 

項目 | 描述
------- | -----------
- | 選擇性的負號，表示負的時間間隔。
*d* | 選擇性的天數，沒有前置的零。
*hh* | 小時數，範圍從 "00" 到 "23"。
*mm* | 分鐘數，範圍從 "00" 到 "59"。
*ss* | 秒數，範圍從 "0" 到 "59"。
*fffffff* | 秒的選擇性小數部分。 其值的範圍可從 "0000001" (一個刻度或一秒的千萬分之一) 到 "9999999" (一秒的千萬分之&9;,999,999，也就是一秒減一個刻度)。 

與 "g" 和 "G" 格式規範不同，"c" 格式規範不區分文化特性。 它會產生 [TimeSpan](xref:System.TimeSpan) 值的字串表示，而該值是非變異值，且對於 .NET Framework 4 之前的所有舊版 .NET Framework 皆通用。 "c" 是預設的 [TimeSpan](xref:System.TimeSpan) 格式字串，而 [TimeSpan.ToString](xref:System.TimeSpan.ToString) 方法會使用 "c" 格式字串來格式化時間間隔值。

> [!NOTE]
> [TimeSpan](xref:System.TimeSpan)也支援 "t" 和 "T" 標準格式字串，它們的行為與 "c" 標準格式字串相同。

下列範例會具現化兩個 [TimeSpan](xref:System.TimeSpan) 物件，用以執行算術運算，並顯示結果。 在每個案例中，都使用複合格式化，以 "c" 格式規範顯示 [TimeSpan](xref:System.TimeSpan) 值。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:c} - {1:c} = {2:c}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2);

      interval1 = new TimeSpan(0, 0, 1, 14, 365);
      interval2 = TimeSpan.FromTicks(2143756);  
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       07:45:16 - 18:12:38 = -10:27:22
//       07:45:16 + 18:12:38 = 1.01:57:54
//       00:01:14.3650000 + 00:00:00.2143756 = 00:01:14.5793756
```

```vb
Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:c} - {1:c} = {2:c}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2)

      interval1 = New TimeSpan(0, 0, 1, 14, 365)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       07:45:16 - 18:12:38 = -10:27:22
'       07:45:16 + 18:12:38 = 1.01:57:54
'       00:01:14.3650000 + 00:00:00.2143756 = 00:01:14.5793756
```

## <a name="the-general-short-g-format-specifier"></a>一般短 ("g") 格式規範

"g" [TimeSpan](xref:System.TimeSpan) 格式規範會以壓縮模式傳回 [TimeSpan](xref:System.TimeSpan) 值的字串表示，而且只包括必要的項目。 其形式如下：

[-][_d_:]_h_:_mm_:_ss_[._FFFFFFF_]

在方括號 ([ 和 ]) 中的項目是選擇性的項目。 冒號 (:) 是常值符號。 下表說明其餘項目。

項目 | 描述
------- | -----------
- | 選擇性的負號，表示負的時間間隔。
*d* | 選擇性的天數，沒有前置的零。
*hh* | 小時數，範圍從 "0" 到 "23"，且沒有前置的零。 
*mm* | 分鐘數，範圍從 "00" 到 "59"。
*ss* | 秒數，範圍從 "0" 到 "59"。
. | 小數的秒數分隔符號。
*FFFFFFF* | 小數的秒數。 盡可能顯示最少的數字。

和 "G" 格式規範一樣，"g" 格式規範已經過當地語系化。 它的小數秒數分隔符號是根據目前文化特性而定。

下列範例會具現化兩個 [TimeSpan](xref:System.TimeSpan) 物件，用以執行算術運算，並顯示結果。 在每個案例中，都使用複合格式化，以 "g" 格式規範顯示 [TimeSpan](xref:System.TimeSpan) 值。 此外，它會使用目前的系統文化特性 (在此案例中是英文-美國或 en-US) 和法文-法國 (fr-FR) 文化特性的格式化慣例，來格式化 [TimeSpan](xref:System.TimeSpan) 值。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:g} - {1:g} = {2:g}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), 
                        "{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2));

      interval1 = new TimeSpan(0, 0, 1, 14, 36);
      interval2 = TimeSpan.FromTicks(2143756);      
      Console.WriteLine("{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       7:45:16 - 18:12:38 = -10:27:22
//       7:45:16 + 18:12:38 = 1:1:57:54
//       0:01:14.036 + 0:00:00.2143756 = 0:01:14.2503756
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:g} - {1:g} = {2:g}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), 
                        "{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2))

      interval1 = New TimeSpan(0, 0, 1, 14, 36)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       7:45:16 - 18:12:38 = -10:27:22
'       7:45:16 + 18:12:38 = 1:1:57:54
'       0:01:14.036 + 0:00:00.2143756 = 0:01:14.2503756
```

## <a name="the-general-long-g-format-specifier"></a>一般長 ("G") 格式規範

"G" [TimeSpan](xref:System.TimeSpan) 格式規範會以完整格式傳回 [TimeSpan](xref:System.TimeSpan) 值的字串表示，而此形式一律會同時包含日數和小數秒數。 從 "G" 標準格式規範產生的字串具有下列形式：

[-]*d*:*hh*:*mm*:*ss*.*fffffff*

在方括號 ([ 和 ]) 中的項目是選擇性的項目。 冒號 (:) 是常值符號。 下表說明其餘項目。

項目 | 描述
------- | -----------
- | 選擇性的負號，表示負的時間間隔。
*d* | 選擇性的天數，沒有前置的零。
*hh* | 小時數，範圍從 "0" 到 "23"。 
*mm* | 分鐘數，範圍從 "00" 到 "59"。
*ss* | 秒數，範圍從 "0" 到 "59"。
. | 小數的秒數分隔符號。
*fffffff* | 小數的秒數。

和 "G" 格式規範一樣，"g" 格式規範已經過當地語系化。 它的小數秒數分隔符號是根據目前文化特性而定。

下列範例會具現化兩個 [TimeSpan](xref:System.TimeSpan) 物件，用以執行算術運算，並顯示結果。 在每個案例中，都使用複合格式化，以 "G" 格式規範顯示 [TimeSpan](xref:System.TimeSpan) 值。 此外，它會使用目前的系統文化特性 (在此案例中是英文-美國或 en-US) 和法文-法國 (fr-FR) 文化特性的格式化慣例，來格式化 [TimeSpan](xref:System.TimeSpan) 值。 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:G} - {1:G} = {2:G}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), 
                        "{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2));

      interval1 = new TimeSpan(0, 0, 1, 14, 36);
      interval2 = TimeSpan.FromTicks(2143756);      
      Console.WriteLine("{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       0:07:45:16.0000000 - 0:18:12:38.0000000 = -0:10:27:22.0000000
//       0:07:45:16,0000000 + 0:18:12:38,0000000 = 1:01:57:54,0000000
//       0:00:01:14.0360000 + 0:00:00:00.2143756 = 0:00:01:14.2503756
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:G} - {1:G} = {2:G}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), 
                        "{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2))

      interval1 = New TimeSpan(0, 0, 1, 14, 36)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       0:07:45:16.0000000 - 0:18:12:38.0000000 = -0:10:27:22.0000000
'       0:07:45:16,0000000 + 0:18:12:38,0000000 = 1:01:57:54,0000000
'       0:00:01:14.0360000 + 0:00:00:00.2143756 = 0:00:01:14.2503756
```

## <a name="see-also"></a>另請參閱

[格式化類型](formatting-types.md)

[複合格式](composite-format.md)

[剖析字串](parsing-strings.md)


