---
title: 概念模型標準與 SQL Server 函式的對應
ms.date: 03/30/2017
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
ms.openlocfilehash: f997fbf39f3dee07cc0d58a39fca779f55236606
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251684"
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>概念模型標準與 SQL Server 函式的對應
本主題描述概念模型標準函式如何對應到相對應的 SQL Server 函式。  
  
## <a name="date-and-time-functions"></a>日期及時間函式  
 下表描述日期與時間函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[AddDays(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[AddMinutes(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[AddMonths(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[AddYears(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[CreateDateTime （年、月、日、小時、分鐘、秒）](./language-reference/date-and-time-canonical-functions.md)|針對 SQL Server 2000 和 SQL Server 2005，伺服器上會建立 `datetime` 格式的值。 針對 SQL Server 2008 和以後版本，伺服器上會建立 `datetime2` 值。|  
|[CreateDateTimeOffset （年、月、日、小時、分鐘、秒、tzoffset）](./language-reference/date-and-time-canonical-functions.md)|伺服器上會建立 `datetimeoffset` 格式的值。<br /><br /> 在 SQL Server 2000 或 SQL Server 2005 中不支援。|  
|[Createtimefilterend （小時、分鐘、秒）](./language-reference/date-and-time-canonical-functions.md)|伺服器上會建立 `time` 格式的值。<br /><br /> 在 SQL Server 2000 或 SQL Server 2005 中不支援。|  
|[CurrentDateTime()](./language-reference/date-and-time-canonical-functions.md)|SQLServer 2008 中：`SysDateTime()`。<br /><br /> SQLServer 2000 和 SQLServer 2005 中：`GetDate()`。|  
|[CurrentDateTimeOffset()](./language-reference/date-and-time-canonical-functions.md)|SQL Server 2008 中：`SysDateTimeOffset()`。<br /><br /> 在 SQL Server 2000 或 SQL Server 2005 中不支援。|  
|[CurrentUtcDateTime()](./language-reference/date-and-time-canonical-functions.md)|SQLServer 2008 中：`SysUtcDateTime()`。 SQL Server 2000 和 SQL Server 2005 中：`GetUtcDate()`。|  
|[DayOfYear(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Day(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[DiffMicroseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[DiffMinutes(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[DiffNanoseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[DiffSeconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[DiffYears(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes(DateTimeOffset)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Hour(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Millisecond(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[Minute(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Month(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[Second(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Truncate(expression)](./language-reference/date-and-time-canonical-functions.md)|針對 SQL Server 2000 和 SQL Server 2005，會在`datetime`伺服器上建立截斷的格式化值。 針對 SQL Server 2008 和更新版本，會在`datetime2`伺服器`datetimeoffset`上建立截斷的或值。|  
|[Year(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>彙總函式  
 下表描述彙總函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[Avg(expression)](./language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](./language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count(expression)](./language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min(expression)](./language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[Max(expression)](./language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev(expression)](./language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP(expression)](./language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum(expression)](./language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var(expression)](./language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP(expression)](./language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>數學函式  
 以下資料表描述數學函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[Abs(value)](./language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[Ceiling(value)](./language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[Floor(value)](./language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Power(value)](./language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[Round(value)](./language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[各](./language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>字串函式  
 下表描述字串函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[Contains （字串，目標）](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat(string1, string2)](./language-reference/string-canonical-functions.md)|string1 + string2|  
|[EndsWith （string，target）](./language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **注意**`false`如果`target` `CHARINDEX` 是儲存在固定長度的字串資料行中，而且是常數，此函數會傳回。`string` 在這個情況下，會搜尋到整個字串，包括任何填補的後端空格。 可能的解決方法是傳遞字串至 `EndsWith` 函式前，修剪固定長度字串中的資料，如以下範例所示：`EndsWith(TRIM(string), target)`|  
|[IndexOf(target, string2)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Left （string1，length）](./language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[長度（字串）](./language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim(string)](./language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[Right （string1，length）](./language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[Trim(string)](./language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Replace （string1，string2，string3 ...）](./language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Reverse （字串）](./language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim(string)](./language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith （string，target）](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Substring （字串、開始、長度）](./language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower(string)](./language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper(string)](./language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>位元函式  
 下表描述位元函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[BitWiseAnd (value1, value2)](./language-reference/bitwise-canonical-functions.md)|value1 & value2|  
|[BitWiseNot (value)](./language-reference/bitwise-canonical-functions.md)|~value|  
|[BitWiseOr (value1, value2)](./language-reference/bitwise-canonical-functions.md)|value1 &#124; value2|  
|[BitWiseXor （value1，value2）](./language-reference/bitwise-canonical-functions.md)|value1 ^ value2|
