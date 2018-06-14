---
title: 日期及時間函式
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: dbde1a2d19e9cf1559129adf8fe3dcc4fadddf0a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761112"
---
# <a name="date-and-time-functions"></a>日期及時間函式
.NET Framework Data Provider for SQL Server (SqlClient) 提供了日期和時間函式，這些函式會在 `System.DateTime` 輸入值上執行作業，並傳回 `string`、數值或 `System.DateTime` 值結果。 這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。 提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。下表將顯示 SqlClient 日期和時間函式。  
  
|函式|描述|  
|--------------|-----------------|  
|`DATEADD(` `datepart`, `number`, `date``)`|傳回新的 `DateTime` 值，這個值是以加入間隔至指定的日期為根據。<br /><br /> **引數**<br /><br /> `datepart`：代表要傳回新值之日期部分的 `String`。<br /><br /> `number`：用來遞增 `Int32` 的 `Int64`、`Decimal`、`Double` 或 `datepart` 值。<br /><br /> `date:` 傳回的運算式`DateTime`，或`DateTimeOffset`，或`Time`精確度 = [0-7]，或日期格式之字元字串。<br /><br /> **傳回值**<br /><br /> 新的 `DateTime`、`DateTimeOffset` 或 `Time` 值 (精確度 = [0-7])。<br /><br /> **範例**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(` `datepart`, `startdate`, `enddate``)`|傳回跨越兩個指定之日期的日期和時間界線數目。<br /><br /> **引數**<br /><br /> `datepart`：代表要計算差異之日期部分的 `String`。<br /><br /> `startdate`：計算的開始日期是傳回 `DateTime`、`DateTimeOffset`、`Time` 值 (精確度 = [0-7]) 或日期格式之字元字串的運算式。<br /><br /> `enddate:` 計算結束日期是傳回的運算式`DateTime`，或`DateTimeOffset`，或`Time`值與精確度 = [0-7]，或日期格式之字元字串。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(` `datepart`, `date``)`|傳回一個字元字串，代表指定日期的指定日期部分。<br /><br /> **引數**<br /><br /> `datepart`：代表要傳回新值之日期部分的 `String`。<br /><br /> `date`：這是傳回 `DateTime,`、`DateTimeOffset`、`Time` 值 (精確度 = [0-7]) 或日期格式之字元字串的運算式。<br /><br /> **傳回值**<br /><br /> 代表指定日期之指定日期部分的字元字串。<br /><br /> **範例**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(` `datepart`, `date``)`|傳回一個整數來代表指定之日期的指定日期部分。<br /><br /> **引數**<br /><br /> `datepart`：代表要傳回新值之日期部分的 `String`。<br /><br /> `date`：這是傳回 `DateTime,`、`DateTimeOffset,`、`Time` 值 (精確度 = [0-7]) 或日期格式之字元字串的運算式。<br /><br /> **傳回值**<br /><br /> 指定日期的指定日期部分，當做 `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(` `date` `)`|以整數形式傳回指定之日期的日。<br /><br /> **引數**<br /><br /> `date`： 類型的運算式`DateTime`或`DateTimeOffset`精確度 = 0-7。<br /><br /> **傳回值**<br /><br /> 指定之日期的日，當做 `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|採用 SQL Server 的內部格式，為日期時間值產生目前的日期和時間。<br /><br /> **傳回值**<br /><br /> 當成 `DateTime` 的目前系統日期和時間，精確度為 3。<br /><br /> **範例**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|以 UTC (國際標準時間或格林威治標準時間) 格式產生日期時間值。<br /><br /> **傳回值**<br /><br /> 採用 UTC 格式且精確度為 3 的 `DateTime` 值。<br /><br /> **範例**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(` `date` `)`|以整數形式傳回指定日期的月份。<br /><br /> **引數**<br /><br /> `date`： 類型的運算式`DateTime`或`DateTimeOffset`精確度 = 0-7。<br /><br /> **傳回值**<br /><br /> 指定之日期的月份，當做 `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(` `date` `)`|以整數形式傳回指定日期的年份。<br /><br /> **引數**<br /><br /> `date`： 類型的運算式`DateTime`或`DateTimeOffset`精確度 = 0-7。<br /><br /> **傳回值**<br /><br /> 指定之日期的年份，當做 `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|傳回精確度為 7 的 `DateTime` 值。<br /><br /> **傳回值**<br /><br /> 精確度為 7 的 `DateTime` 值。<br /><br /> **範例**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|以 UTC (國際標準時間或格林威治標準時間) 格式產生日期時間值。<br /><br /> **傳回值**<br /><br /> 採用 UTC 格式且精確度 = 7 的 `DateTime` 值。<br /><br /> **範例**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|傳回精確度為 7 的 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> 採用 UTC 格式且精確度為 7 的 `DateTimeOffset` 值。<br /><br /> **範例**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 如需 SqlClient 所支援日期和時間函式的詳細資訊，請參閱 SqlClient 提供者資訊清單中所指定 SQL Server 版本的說明文件：  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[日期和時間函數 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115908)|[日期和時間函數 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115909)|[日期和時間函數 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>另請參閱  
 [適用於 Entity Framework 的 SqlClient 函式](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
