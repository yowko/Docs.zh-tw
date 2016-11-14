---
title: "如何：反覆存取日期和時間值"
description: "如何：反覆存取日期和時間值"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 15690f18-1bb9-4bb8-bc11-0b737e2f0859
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 00a09c8a60138a1828d4e8c62dd72b88abbf4bbe

---

# <a name="how-to-roundtrip-date-and-time-values"></a>如何：反覆存取日期和時間值

在許多應用程式中，日期和時間值的用途都是要明確地識別單一時間點。 本主題說明如何儲存並還原 [DateTime](xref:System.DateTime) 值與 [DateTimeOffset](xref:System.DateTimeOffset) 值，以讓還原值識別出與儲存值相同的時間。

## <a name="to-roundtrip-a-datetime-value"></a>若要反覆存取 DateTime 值

1. 呼叫 [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) 方法與 "o" 格式規範，以將 [DateTime](xref:System.DateTime) 值轉換為其字串表示。

2. 將 [DateTime](xref:System.DateTime) 值的字串表示儲存至檔案，或跨處理序、應用程式定義域或電腦界限進行傳遞。

3. 擷取代表 [DateTime](xref:System.DateTime) 值的字串。

4. 呼叫 [DateTime.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTime.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) 方法，然後將 [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) 做為 *DateTimeStyles* 參數的值傳遞。

下列範例說明如何反覆存取 [DateTime](xref:System.DateTime) 值。

```csharp
const string fileName = @".\DateFile.txt";

StreamWriter outFile = new StreamWriter(fileName);

// Save DateTime value.
DateTime dateToSave = DateTime.SpecifyKind(new DateTime(2008, 6, 12, 18, 45, 15), 
                                           DateTimeKind.Local);
string dateString = dateToSave.ToString("o");      
Console.WriteLine("Converted {0} ({1}) to {2}.", 
                  dateToSave.ToString(), 
                  dateToSave.Kind.ToString(), 
                  dateString);      
outFile.WriteLine(dateString);
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName);
outFile.Close();

// Restore DateTime value.
DateTime restoredDate;

StreamReader inFile = new StreamReader(fileName);
dateString = inFile.ReadLine();
inFile.Close();
restoredDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Read {0} ({2}) from {1}.", restoredDate.ToString(), 
                                              fileName, 
                                              restoredDate.Kind.ToString());
// The example displays the following output:
//    Converted 6/12/2008 6:45:15 PM (Local) to 2008-06-12T18:45:15.0000000-05:00.
//    Wrote 2008-06-12T18:45:15.0000000-05:00 to .\DateFile.txt.
//    Read 6/12/2008 6:45:15 PM (Local) from .\DateFile.txt.
```

```vb
Const fileName As String = ".\DateFile.txt"

Dim outFile As New StreamWriter(fileName)

' Save DateTime value.
Dim dateToSave As Date = DateTime.SpecifyKind(#06/12/2008 6:45:15 PM#, _
                                              DateTimeKind.Local)
Dim dateString As String = dateToSave.ToString("o")      
Console.WriteLine("Converted {0} ({1}) to {2}.", dateToSave.ToString(), _
                  dateToSave.Kind.ToString(), dateString)      
outFile.WriteLine(dateString)
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName)
outFile.Close()   

' Restore DateTime value.
Dim restoredDate As Date

Dim inFile As New StreamReader(fileName)
dateString = inFile.ReadLine()
inFile.Close()
restoredDate = DateTime.Parse(dateString, Nothing, DateTimeStyles.RoundTripKind)
Console.WriteLine("Read {0} ({2}) from {1}.", restoredDate.ToString(), _
                  fileName, restoredDAte.Kind.ToString())
' The example displays the following output:
'    Converted 6/12/2008 6:45:15 PM (Local) to 2008-06-12T18:45:15.0000000-05:00.
'    Wrote 2008-06-12T18:45:15.0000000-05:00 to .\DateFile.txt.
'    Read 6/12/2008 6:45:15 PM (Local) from .\DateFile.txt.
```

反覆存取 [DateTime](xref:System.DateTime) 值時，這項技術可以成功保留所有當地和全球通用時間的時間。 例如，如果當地的 [DateTime](xref:System.DateTime) 值儲存在美國太平洋標準時區的系統上，但該值在美國中央標準時區的系統上還原，則還原的日期和時間會比原始時間晚兩個小時，以反映出兩個時區之間的時間差異。 不過，針對未指定的時間，這項技術並不一定準確。 只要 [DateTime](xref:System.DateTime) 值的 [Kind](xref:System.DateTime.Kind) 屬性是 [Unspecified](xref:System.DateTimeKind.Unspecified)，系統就會將其全部視為當地時間。 如果不是這種狀況，[DateTime](xref:System.DateTime) 就無法成功地識別出正確的時間點。 這項限制的因應措施，是將日期和時間值與其儲存和還原作業的時區緊密結合。

## <a name="to-roundtrip-a-datetimeoffset-value"></a>若要反覆存取 DateTimeOffset 值

呼叫 [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) 方法與 "o" 格式規範，以將 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為其字串表示。

2. 將 [DateTimeOffset](xref:System.DateTimeOffset) 值的字串表示儲存至檔案，或跨處理序、應用程式定義域或電腦界限進行傳遞。

3. 擷取代表 [DateTimeOffset](xref:System.DateTimeOffset) 值的字串。

4. 呼叫 [DateTimeOffset.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTimeOffset.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) 方法，然後將 [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) 做為 *styles* 參數的值傳遞。

下列範例說明如何反覆存取 [DateTimeOffset](xref:System.DateTimeOffset) 值。

```csharp
const string fileName = @".\DateOff.txt";

StreamWriter outFile = new StreamWriter(fileName);

// Save DateTime value.
DateTimeOffset dateToSave = new DateTimeOffset(2008, 6, 12, 18, 45, 15, 
                                               new TimeSpan(7, 0, 0));
string dateString = dateToSave.ToString("o");      
Console.WriteLine("Converted {0} to {1}.", dateToSave.ToString(), 
                  dateString);      
outFile.WriteLine(dateString);
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName);
outFile.Close();

// Restore DateTime value.
DateTimeOffset restoredDateOff;

StreamReader inFile = new StreamReader(fileName);
dateString = inFile.ReadLine();
inFile.Close();
restoredDateOff = DateTimeOffset.Parse(dateString, null, 
                                       DateTimeStyles.RoundtripKind);
Console.WriteLine("Read {0} from {1}.", restoredDateOff.ToString(), 
                  fileName);
// The example displays the following output:
//    Converted 6/12/2008 6:45:15 PM +07:00 to 2008-06-12T18:45:15.0000000+07:00.
//    Wrote 2008-06-12T18:45:15.0000000+07:00 to .\DateOff.txt.
//    Read 6/12/2008 6:45:15 PM +07:00 from .\DateOff.txt.
```

```vb
Const fileName As String = ".\DateOff.txt"

Dim outFile As New StreamWriter(fileName)

' Save DateTime value.
Dim dateToSave As New DateTimeOffset(2008, 6, 12, 18, 45, 15, _
                                     New TimeSpan(7, 0, 0))
Dim dateString As String = dateToSave.ToString("o")      
Console.WriteLine("Converted {0} to {1}.", dateToSave.ToString(), dateString)      
outFile.WriteLine(dateString)
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName)
outFile.Close()   

' Restore DateTime value.
Dim restoredDateOff As DateTimeOffset

Dim inFile As New StreamReader(fileName)
dateString = inFile.ReadLine()
inFile.Close()
restoredDateOff = DateTimeOffset.Parse(dateString, Nothing, DateTimeStyles.RoundTripKind)
Console.WriteLine("Read {0} from {1}.", restoredDateOff.ToString(), fileName)
' The example displays the following output:
'    Converted 6/12/2008 6:45:15 PM +07:00 to 2008-06-12T18:45:15.0000000+07:00.
'    Wrote 2008-06-12T18:45:15.0000000+07:00 to .\DateOff.txt.
'    Read 6/12/2008 6:45:15 PM +07:00 from .\DateOff.txt.
```

這項技術會一律明確地將 [DateTimeOffset](xref:System.DateTimeOffset) 值識別為單一時間點。 您可以呼叫 [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) 方法，將該值轉換成國際標準時間 (UTC)，或者呼叫 [DateTimeOffset.ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) 或 [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo) 方法，將它轉換為特定時區的時間。 這項技術有個主要限制：在表示特定時區之時間的 [DateTimeOffset](xref:System.DateTimeOffset) 值上執行日期和時間算術時，可能不會產生該時區的精確結果。 這是因為在具現化 [DateTimeOffset](xref:System.DateTimeOffset) 值時，它就會其時區解除關聯。 因此，當您執行日期和時間計算時，就無法再套用該時區的調整規則。 若要解決這個問題，您可以定義自訂類型，以包含日期與時間值及其隨附的時區。

## <a name="see-also"></a>另請參閱

[執行格式化作業](performing-formatting-operations.md)

[標準日期與時間格式字串](standard-datetime.md)




<!--HONumber=Nov16_HO1-->


