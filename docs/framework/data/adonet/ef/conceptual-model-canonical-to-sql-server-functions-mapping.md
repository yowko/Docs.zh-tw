---
title: "概念模型標準與 SQL Server 函式對應 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 概念模型標準與 SQL Server 函式對應
本主題描述概念模型標準函式如何對應到相對應的 SQL Server 函式。  
  
## 日期及時間函式  
 下表描述日期與時間函式的對應：  
  
|標準函式|SQL Server 函式|  
|----------|-------------------|  
|[AddDays\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[AddMinutes\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[AddMonths\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[AddYears\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[CreateDateTime\(year, month, day, hour, minute, second\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|針對 SQL Server 2000 和 SQL Server 2005，伺服器上會建立 `datetime` 格式的值。  針對 SQL Server 2008 和以後版本，伺服器上會建立 `datetime2` 值。|  
|[CreateDateTimeOffset\(year, month, day, hour, minute, second, tzoffset\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|伺服器上會建立 `datetimeoffset` 格式的值。<br /><br /> 在 SQL Server 2000 或 SQL Server 2005 中不支援。|  
|[CreateTime\(hour, minute, second\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|伺服器上會建立 `time` 格式的值。<br /><br /> 在 SQL Server 2000 或 SQL Server 2005 中不支援。|  
|[CurrentDateTime\(\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|SQLServer 2008 中：`SysDateTime()`。<br /><br /> SQLServer 2000 和 SQLServer 2005 中：`GetDate()`。|  
|[CurrentDateTimeOffset\(\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|SQL Server 2008 中：`SysDateTimeOffset()`。<br /><br /> 在 SQL Server 2000 或 SQL Server 2005 中不支援。|  
|[CurrentUtcDateTime\(\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|SQLServer 2008 中：`SysUtcDateTime()`。  SQL Server 2000 和 SQL Server 2005 中：`GetUtcDate()`。|  
|[DayOfYear\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Day\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays\(startExpression, endExpression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours\(startExpression, endExpression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[DiffMicroseconds\(startExpression, endExpression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds\(startExpression, endExpression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[DiffMinutes\(startExpression, endExpression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[DiffNanoseconds\(startExpression, endExpression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[DiffSeconds\(startExpression, endExpression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[DiffYears\(startExpression, endExpression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes\(DateTimeOffset\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Hour\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Millisecond\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[Minute\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Month\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[Second\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Truncate\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|針對 SQL Server 2000 和 SQL Server 2005，伺服器上會建立截斷 `datetime` ``  格式的值。  針對 SQL Server 2008 和以後版本，伺服器上會建立截斷的  `` `datetime2` 或  `` `datetimeoffset` 值。|  
|[Year\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## 彙總函式  
 下表描述彙總函式的對應：  
  
|標準函式|SQL Server 函式|  
|----------|-------------------|  
|[Avg\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[Max\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP\(expression\)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## 數學函式  
 以下資料表描述數學函式的對應：  
  
|標準函式|SQL Server 函式|  
|----------|-------------------|  
|[Abs\(value\)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[Ceiling\(value\)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[Floor\(value\)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Power\(value\)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[Round\(value\)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[Truncate](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## 字串函式  
 下表描述字串函式的對應：  
  
|標準函式|SQL Server 函式|  
|----------|-------------------|  
|[Contains\(string, target\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat\(string1, string2\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|string1 \+ string2|  
|[EndsWith\(string, target\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **請注意**，如果 `string` 是儲存在固定長度的字串資料行，而且 `target` 是常數，`CHARINDEX` 函式會傳回 `false`。  在這個情況下，會搜尋到整個字串，包括任何填補的後端空格。  可能的解決方法是傳遞字串至 `EndsWith` 函式前，修剪固定長度字串中的資料，如以下範例所示：`EndsWith(TRIM(string), target)`|  
|[IndexOf\(target, string2\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Left \(string1, length\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[Length \(string\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim\(string\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[Right \(string1, length\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[Trim\(string\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Replace \(string1, string2, string3\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Reverse \(string\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim\(string\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith\(string, target\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Substring\(string, start, length\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower\(string\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper\(string\)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## 位元函式  
 下表描述位元函式的對應：  
  
|標準函式|SQL Server 函式|  
|----------|-------------------|  
|[BitWiseAnd \(value1, value2\)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|value1 & value2|  
|[BitWiseNot \(value\)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|~value|  
|[BitWiseOr \(value1, value2\)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|value1 &#124; value2|  
|[BitWiseXor \(value1, value2\)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|value1 ^ value2|