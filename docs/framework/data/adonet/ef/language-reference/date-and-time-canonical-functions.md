---
title: 日期及時間標準函式
ms.date: 03/30/2017
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
ms.openlocfilehash: b79d11909c22208e0ea15b4083c230e920f1ad42
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925418"
---
# <a name="date-and-time-canonical-functions"></a>日期及時間標準函式
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 包括日期和時間的標準函式。  
  
## <a name="remarks"></a>備註  
 下表顯示的日期和時間[!INCLUDE[esql](../../../../../../includes/esql-md.md)]標準函式。 `datetime` 是<xref:System.DateTime>值。  
  
|功能|描述|  
|--------------|-----------------|  
|`AddNanoseconds(expression,number)`|將奈秒數的指定 `number` 加入至 `expression`。<br /><br /> **引數**<br /><br /> `expression`：`DateTime`、`DateTimeOffset` 或 `Time`。<br /><br /> `number`: `Int32`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`AddMicroseconds(expression,number)`|將毫秒數的指定 `number` 加入至 `expression`。<br /><br /> **引數**<br /><br /> `expression`：`DateTime`、`DateTimeOffset` 或 `Time`。<br /><br /> `number`: `Int32`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`AddMilliseconds(expression,number)`|將毫秒數的指定 `number` 加入至 `expression`。<br /><br /> **引數**<br /><br /> `expression`：`DateTime`、`DateTimeOffset` 或 `Time`。<br /><br /> `number`: `Int32`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`AddSeconds(expression,number)`|將秒數的指定 `number` 加入至 `expression`。<br /><br /> **引數**<br /><br /> `expression`：`DateTime`、`DateTimeOffset` 或 `Time`。<br /><br /> `number`: `Int32`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`AddMinutes(expression,number)`|將分鐘數的指定 `number` 加入至 `expression`。<br /><br /> **引數**<br /><br /> `expression`：`DateTime`、`DateTimeOffset` 或 `Time`。<br /><br /> `number`: `Int32`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`AddHours(expression,number)`|將時數的指定 `number` 加入至 `expression`。<br /><br /> **引數**<br /><br /> `expression`：`DateTime`、`DateTimeOffset` 或 `Time`。<br /><br /> `number`: `Int32`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`AddDays(expression,number)`|將天數的指定 `number` 加入至 `expression`。<br /><br /> **引數**<br /><br /> `expression`：`DateTime` 或 `DateTimeOffset`。<br /><br /> `number`: `Int32`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`AddMonths(expression,number)`|將月份數的指定 `number` 加入至 `expression`。<br /><br /> **引數**<br /><br /> `expression`：`DateTime` 或 `DateTimeOffset`。<br /><br /> `number`: `Int32`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`AddYears(expression,number)`|將年數的指定 `number` 加入至 `expression`。<br /><br /> **引數**<br /><br /> `expression`：`DateTime` 或 `DateTimeOffset`。<br /><br /> `number`: `Int32`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`CreateDateTime(year,month,day,hour,minute,second)`|傳回新 `DateTime` 值作為此伺服器時區內之伺服器目前的日期和時間。<br /><br /> **引數**<br /><br /> `year`、`month`、`day`、`hour`、`minute`：`Int16` 和 `Int32`。<br /><br /> `second`: `Double`.<br /><br /> **傳回值**<br /><br /> `DateTime`。|  
|`CreateDateTimeOffset(year,month,day,hour,minute,second,tzoffset)`|傳回新 `DateTimeOffset` 值作為與國際標準時間 (UTC) 相關之伺服器目前的日期和時間。<br /><br /> **引數**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **傳回值**<br /><br /> `DateTimeOffset`。|  
|`CreateTime(hour,minute,second)`|傳回新 `Time` 值做為目前時間。<br /><br /> **引數**<br /><br /> `hour` 和 `minute`：`Int32`<br /><br /> `second`: `Double`.<br /><br /> **傳回值**<br /><br /> `Time`。|  
|`CurrentDateTime()`|傳回 `DateTime` 值作為此伺服器時區內之伺服器目前的日期和時間。<br /><br /> **傳回值**<br /><br /> `DateTime`。|  
|`CurrentDateTimeOffset()`|以 `DateTimeOffset` 格式傳回目前的日期、時間和時差。<br /><br /> **傳回值**<br /><br /> `DateTimeOffset`。|  
|`CurrentUtcDateTime()`|傳回 <xref:System.DateTime> 值作為 UTS 時區內之伺服器目前的日期和時間。<br /><br /> **傳回值**<br /><br /> `DateTime`。|  
|`Day(expression)`|以介於 1 到 31 之間的 `expression` 格式傳回 `Int32` 的日數部分。<br /><br /> **引數**<br /><br /> `DateTime` 和 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(expression)`|以介於 1 到 366 之間的 `expression` 格式傳回的 `Int32` 天數部分，其中傳回的 366 代表閏年的最後一天。<br /><br /> **引數**<br /><br /> `DateTime` 或 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`DiffNanoseconds(startExpression,endExpression)`|傳回 `startExpression` 與 `endExpression` 之間的奈秒差。<br /><br /> **引數**<br /><br /> `startExpression`、`endExpression`：`DateTime`、`DateTimeOffset` 或 `Time`。 **注意︰** `startExpression`和`endExpression`必須屬於相同的型別。   <br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`DiffMilliseconds(startExpression,endExpression)`|傳回 `startExpression` 與 `endExpression` 之間的毫秒差。<br /><br /> **引數**<br /><br /> `startExpression`、`endExpression`：`DateTime`、`DateTimeOffset` 或 `Time`。 **注意︰** `startExpression`和`endExpression`必須屬於相同的型別。   <br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`DiffMicroseconds(startExpression,endExpression)`|傳回 `startExpression` 與 `endExpression` 之間的微秒差。<br /><br /> **引數**<br /><br /> `startExpression`、`endExpression`：`DateTime`、`DateTimeOffset` 或 `Time`。 **注意︰** `startExpression`和`endExpression`必須屬於相同的型別。   <br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`DiffSeconds(startExpression,endExpression)`|傳回 `startExpression` 與 `endExpression` 之間的秒差。<br /><br /> **引數**<br /><br /> `startExpression`、`endExpression`：`DateTime`、`DateTimeOffset` 或 `Time`。 **注意︰** `startExpression`和`endExpression`必須屬於相同的型別。   <br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`DiffMinutes(startExpression,endExpression)`|傳回 `startExpression` 與 `endExpression` 之間的分鐘差。<br /><br /> **引數**<br /><br /> `startExpression`、`endExpression`：`DateTime`、`DateTimeOffset` 或 `Time`。 **注意︰** `startExpression`和`endExpression`必須屬於相同的型別。   <br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`DiffHours(startExpression,endExpression)`|傳回 `startExpression` 與 `endExpression` 之間的小時差。<br /><br /> **引數**<br /><br /> `startExpression`、`endExpression`：`DateTime`、`DateTimeOffset` 或 `Time`。 **注意︰** `startExpression`和`endExpression`必須屬於相同的型別。   <br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`DiffDays(startExpression,endExpression)`|傳回 `startExpression` 與 `endExpression` 之間的天數差。<br /><br /> **引數**<br /><br /> `startExpression`、`endExpression`：`DateTime` 或 `DateTimeOffset`。 **注意︰** `startExpression`和`endExpression`必須屬於相同的型別。   <br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`DiffMonths(startExpression,endExpression)`|傳回 `startExpression` 與 `endExpression` 之間的月數差。<br /><br /> **引數**<br /><br /> `startExpression`、`endExpression`：`DateTime` 或 `DateTimeOffset`。 **注意︰** `startExpression`和`endExpression`必須屬於相同的型別。   <br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`DiffYears(startExpression,endExpression)`|傳回 `startExpression` 與 `endExpression` 之間的年數差。<br /><br /> **引數**<br /><br /> `startExpression`、`endExpression`：`DateTime` 或 `DateTimeOffset`。 **注意︰** `startExpression`和`endExpression`必須屬於相同的型別。   <br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`GetTotalOffsetMinutes(datetimeoffset)`|傳回 `datetimeoffset` 與格林威治標準時間 (GMT) 間的時差分鐘數。 這項值通常介於 +780 到 -780 之間 (+ 或 - 13 小時)。 **注意：** 僅支援 SQL Server 2008 中此函式。 <br /><br /> **引數**<br /><br /> `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`Hour(expression)`|以介於 0 到 23 之間的 `expression` 格式傳回 `Int32` 的小時部分。<br /><br /> **引數**<br /><br /> `DateTime, Time` 和 `DateTimeOffset`。<br /><br /> **範例**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(expression)`|以介於 0 到 999 之間的 `expression` 格式傳回 `Int32` 的毫秒部分。<br /><br /> **引數**<br /><br /> `DateTime, Time` 和 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> `Int32`。|  
|`Minute(expression)`|以介於 0 到 59 之間的 `expression` 格式傳回 `Int32` 的分鐘部分。<br /><br /> **引數**<br /><br /> `DateTime, Time` 或 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month(expression)`|以介於 1 到 12 之間的 `expression` 格式傳回 `Int32` 的月份部分。<br /><br /> **引數**<br /><br /> `DateTime` 或 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(expression)`|以介於 0 到 59 之間的 `expression` 格式傳回 `Int32` 的秒鐘部分。<br /><br /> **引數**<br /><br /> `DateTime, Time` 和 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(expression)`|傳回 `expression`，含已截斷的時間值。<br /><br /> **引數**<br /><br /> `DateTime` 或 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> `expression` 的類型。|  
|`Year(expression)`|以 `expression` `Int32` 格式傳回 `YYYY` 的年份部分。<br /><br /> **引數**<br /><br /> `DateTime` 和 `DateTimeOffset`。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 如果提供 `null` 輸入，這些函式會傳回 `null`。  
  
 Microsoft SQL Client Managed Provider 中提供了對等的功能。 如需詳細資訊，請參閱 <<c0> [ 適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
