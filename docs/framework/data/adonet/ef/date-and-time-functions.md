---
title: 日期和時間函式
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: aa024ad748db26cb75111984abdb61fdbd538ef9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198449"
---
# <a name="date-and-time-functions"></a>日期和時間函式

.NET Framework Data Provider for SQL Server (SqlClient) 提供了日期和時間函式，這些函式會在 `System.DateTime` 輸入值上執行作業，並傳回 `string`、數值或 `System.DateTime` 值結果。 這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。 提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。 下表顯示 SqlClient 的日期和時間函數。  
  
|函式|描述|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|傳回根據將間隔加入指定日期的新 `DateTime` 值。<br /><br /> **引數**<br /><br /> `datepart`：代表要傳回新值之日期部分的 `String`。<br /><br /> `number`：用來遞增 `Int32` 的 `Int64`、`Decimal`、`Double` 或 `datepart` 值。<br /><br /> `date:` 傳回、或的運算式，或 `DateTime` `DateTimeOffset` 具有有效 `Time` 位數 = [0-7] 的運算式，或日期格式的字元字串。<br /><br /> **傳回值**<br /><br /> 新的 `DateTime`、`DateTimeOffset` 或 `Time` 值 (精確度 = [0-7])。<br /><br /> **範例**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|傳回跨越兩個指定日期的日期和時間界線數目。<br /><br /> **引數**<br /><br /> `datepart`：代表要計算差異之日期部分的 `String`。<br /><br /> `startdate`：計算的開始日期是傳回 `DateTime`、`DateTimeOffset`、`Time` 值 (精確度 = [0-7]) 或日期格式之字元字串的運算式。<br /><br /> `enddate:` 計算的結束日期是傳回 `DateTime` 、或 `DateTimeOffset` 或 `Time` 值（精確度 = [0-7]）或日期格式之字元字串的運算式。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|傳回一個字元字串，代表指定日期的指定日期部分。<br /><br /> **引數**<br /><br /> `datepart`：代表要傳回新值之日期部分的 `String`。<br /><br /> `date`：這是傳回 `DateTime,`、`DateTimeOffset`、`Time` 值 (精確度 = [0-7]) 或日期格式之字元字串的運算式。<br /><br /> **傳回值**<br /><br /> 代表指定日期之指定日期部分的字元字串。<br /><br /> **範例**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|傳回一個整數來代表指定之日期的指定日期部分。<br /><br /> **引數**<br /><br /> `datepart`：代表要傳回新值之日期部分的 `String`。<br /><br /> `date`：這是傳回 `DateTime,`、`DateTimeOffset,`、`Time` 值 (精確度 = [0-7]) 或日期格式之字元字串的運算式。<br /><br /> **傳回值**<br /><br /> 指定日期的指定日期部分，當做 `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|以整數形式傳回指定日期的日期。<br /><br /> **引數**<br /><br /> `date`： Type `DateTime` 或 `DateTimeOffset` precision = 0-7 的運算式。<br /><br /> **傳回值**<br /><br /> 指定之日期的日，當做 `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|採用 SQL Server 的內部格式，為日期時間值產生目前的日期和時間。<br /><br /> **傳回值**<br /><br /> 當成 `DateTime` 的目前系統日期和時間，精確度為 3。<br /><br /> **範例**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|以 UTC (國際標準時間或格林威治標準時間) 格式產生日期時間值。<br /><br /> **傳回值**<br /><br /> 採用 UTC 格式且精確度為 3 的 `DateTime` 值。<br /><br /> **範例**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|以整數形式傳回指定日期的月份。<br /><br /> **引數**<br /><br /> `date`： Type `DateTime` 或 `DateTimeOffset` precision = 0-7 的運算式。<br /><br /> **傳回值**<br /><br /> 指定之日期的月份，當做 `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|以整數形式傳回指定日期的年份。<br /><br /> **引數**<br /><br /> `date`： Type `DateTime` 或 `DateTimeOffset` precision = 0-7 的運算式。<br /><br /> **傳回值**<br /><br /> 指定之日期的年份，當做 `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|傳回精確度為 7 的 `DateTime` 值。<br /><br /> **傳回值**<br /><br /> 精確度為 7 的 `DateTime` 值。<br /><br /> **範例**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|以 UTC (國際標準時間或格林威治標準時間) 格式產生日期時間值。<br /><br /> **傳回值**<br /><br /> 採用 UTC 格式且精確度 = 7 的 `DateTime` 值。<br /><br /> **範例**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|傳回精確度為 7 的 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> 採用 UTC 格式且精確度為 7 的 `DateTimeOffset` 值。<br /><br /> **範例**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 如需 SqlClient 支援之日期和時間函數的詳細資訊，請參閱 [日期和時間資料類型和函數 (transact-sql) ](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)。
  
## <a name="see-also"></a>另請參閱

- [適用於 Entity Framework 的 SqlClient 函式](sqlclient-for-ef-functions.md)
