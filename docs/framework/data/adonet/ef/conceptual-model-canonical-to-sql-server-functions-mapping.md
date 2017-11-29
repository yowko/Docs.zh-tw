---
title: "概念模型標準與 SQL Server 函式的對應"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a186c37506441dde814ca52970c60f0f816ba53e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>概念模型標準與 SQL Server 函式的對應
本主題描述概念模型標準函式如何對應到相對應的 SQL Server 函式。  
  
## <a name="date-and-time-functions"></a>日期及時間函式  
 下表描述日期與時間函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[AddDays(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[AddMinutes(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[AddMonths(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[AddYears(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[CreateDateTime （年、 月、 日、 時、 分、 秒）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|針對 SQL Server 2000 和 SQL Server 2005，伺服器上會建立 `datetime` 格式的值。 針對 SQL Server 2008 和以後版本，伺服器上會建立 `datetime2` 值。|  
|[CreateDateTimeOffset （年、 月、 日、 小時、 分鐘、 秒、 tzoffset）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|伺服器上會建立 `datetimeoffset` 格式的值。<br /><br /> 在 SQL Server 2000 或 SQL Server 2005 中不支援。|  
|[Createtimefilterend （時、 分、 秒）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|伺服器上會建立 `time` 格式的值。<br /><br /> 在 SQL Server 2000 或 SQL Server 2005 中不支援。|  
|[CurrentDateTime()](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|SQLServer 2008 中：`SysDateTime()`。<br /><br /> SQLServer 2000 和 SQLServer 2005 中：`GetDate()`。|  
|[CurrentDateTimeOffset()](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|SQL Server 2008 中：`SysDateTimeOffset()`。<br /><br /> 在 SQL Server 2000 或 SQL Server 2005 中不支援。|  
|[CurrentUtcDateTime()](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|SQLServer 2008 中：`SysUtcDateTime()`。 SQL Server 2000 和 SQL Server 2005 中：`GetUtcDate()`。|  
|[DayOfYear(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Day(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays （startExpression、 endExpression）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours （startExpression、 endExpression）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[DiffMicroseconds （startExpression、 endExpression）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds （startExpression、 endExpression）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[DiffMinutes （startExpression、 endExpression）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[DiffNanoseconds （startExpression、 endExpression）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[DiffSeconds （startExpression、 endExpression）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[DiffYears （startExpression、 endExpression）](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes(DateTimeOffset)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Hour(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Millisecond(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[Minute(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Month(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[Second(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Truncate(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|SQL Server 2000 和 SQL Server 2005，截斷的`datetime`格式化的值在伺服器上建立。 SQL Server 2008 和更新版本中，截斷`datetime2`或`datetimeoffset`值建立在伺服器上。|  
|[Year(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>彙總函式  
 下表描述彙總函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[Avg(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[Max(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>數學函式  
 以下資料表描述數學函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[Abs(value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[Ceiling(value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[Floor(value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Power(value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[Round(value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[截斷](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>字串函式  
 下表描述字串函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[Contains(string, target)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat （string1，string2）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|string1 + string2|  
|[EndsWith （string，目標）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **請注意**`CHARINDEX`函式會傳回`false`如果`string`固定的長度字串資料行中儲存和`target`是常數。 在這個情況下，會搜尋到整個字串，包括任何填補的後端空格。 可能的解決方法是傳遞字串至 `EndsWith` 函式前，修剪固定長度字串中的資料，如以下範例所示：`EndsWith(TRIM(string), target)`|  
|[IndexOf （目標、 string2）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Left （string1，長度）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[長度 （字串）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[權限 （string1，長度）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[Trim(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[取代 （string1，string2，string3）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[反向 （字串）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith （string，目標）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[子字串 （字串、 開始、 長度）](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>位元函式  
 下表描述位元函式的對應：  
  
|標準函式|SQL Server 函式|  
|-------------------------|--------------------------|  
|[BitWiseAnd （value1，value2）](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|value1 & value2|  
|[BitWiseNot （值）](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|~value|  
|[BitWiseOr （value1，value2）](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|value1 &#124;value2|  
|[BitWiseXor （value1，value2）](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|value1 ^ value2|
