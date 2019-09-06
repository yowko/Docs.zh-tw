---
title: 標準函式的對應 CLR 方法
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 6f14ad8d9e8f919fe820447cc991b102319b38d5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251218"
---
# <a name="clr-method-to-canonical-function-mapping"></a>標準函式的對應 CLR 方法

Entity Framework 提供一組標準函式，可實作在許多資料庫系統常見的功能，例如字串操作和數學函式。 這樣就可以讓開發人員以廣泛的資料庫系統為相標。 從某種查詢技術 (例如 LINQ to Entities) 呼叫時，這些標準函式會轉譯成所使用之提供者的正確對應存放函式。 這樣就可以利用跨資料來源的通用形式來表示函式引動過程，在不同的資料來源提供一致的查詢體驗。 如果運算元為數值型別，位元運算 AND、OR,、NOT 和 XOR 運算子也是對應到這些標準函式。 若為布林運算元，位元運算 AND、OR、NOT 和 XOR 運算子會計算這些運算元的邏輯 AND、OR、NOT 和 XOR 運算。 如需詳細資訊，請參閱[標準](canonical-functions.md)函式。

就 LINQ 案例而言，針對 Entity Framework 的查詢會透過標準函式將某些 CLR 方法對應到基礎資料來源。 在 LINQ to Entities 查詢中，不是明確對應到標準函式的任何方法呼叫，將會導致擲回執行階段 <xref:System.NotSupportedException> 例外狀況 (Exception)。

## <a name="systemstring-method-static-mapping"></a>System.String 方法 (靜態) 對應

|System.String 方法 (靜態)|標準函式|
|-------------------------------------|------------------------|
|System.String Concat(String `str0`, String `str1`)|Concat(`str0`, `str1`)|
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat(Concat(`str0`, `str1`), `str2`)|
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat(Concat(Concat(`str0`, `str1`), `str2`), `str3`)|
|Boolean Equals(String `a`, String `b`)|= 運算子|
|Boolean IsNullOrEmpty(String `value`)|(IsNull(`value`)) OR Length(`value`) = 0|
|Boolean op_Equality(String `a`, String `b`)|= 運算子|
|Boolean op_Inequality(String `a` , String `b`)|!= 運算子|
|Microsoft.VisualBasic.Strings.Trim(String `str`)|Trim(`str`)|
|Microsoft.VisualBasic.Strings.LTrim(String `str`)|Ltrim(`str`)|
|Microsoft.VisualBasic.Strings.RTrim(String `str`)|Rtrim(`str`)|
|Microsoft.VisualBasic.Strings.Len(String `expression`)|Length(`expression`)|
|Microsoft.VisualBasic.Strings.Left(String `str`, Int32 `Length`)|Left(`str`, `Length`)|
|Microsoft.VisualBasic.Strings.Mid(String `str`, Int32 `Start`, Int32 `Length`)|Substring(`str`, `Start`, `Length`)|
|Microsoft.VisualBasic.Strings.Right(String `str`, Int32 `Length`)|Right(`str`, `Length`)|
|Microsoft.VisualBasic.Strings.UCase(String `Value`)|ToUpper(`Value`)|
|Microsoft.VisualBasic.Strings.LCase(String Value)|ToLower(`Value`)|

## <a name="systemstring-method-instance-mapping"></a>System.String 方法 (執行個體) 對應

|System.String 方法 (執行個體)|標準函式|注意|
|---------------------------------------|------------------------|-----------|
|Boolean Contains(String `value`)|`this` LIKE '%`value`%'|如果`value`不是常數，則這會對應至 IndexOf （`this`， `value`） > 0|
|Boolean EndsWith(String `value`)|`this`LIKE `'` '% `value`|如果 `value` 不是一個常數，則這會對應至 Right(`this`, length(`value`)) = `value`。|
|Boolean StartsWith(String `value`)|`this` LIKE '`value`%'|如果 `value` 不是一個常數，則這會對應至 IndexOf(`this`, `value`) = 1。|
|Length|Length(`this`)||
|Int32 IndexOf(String `value`)|IndexOf(`this`, `value`) - 1||
|System.String Insert(Int32 `startIndex`, String `value`)|Concat(Concat(Substring(`this`, 1, `startIndex`), `value`), Substring(`this`, `startIndex`+1, Length(`this`) - `startIndex`))||
|System.String Remove(Int32 `startIndex`)|Substring(`this`, 1, `startIndex`)||
|System.String Remove(Int32 `startIndex`, Int32 `count`)|Concat （substring （`this`，1， `startIndex`），substring （`this`， `startIndex` `count` `this` `count`  + + 1，Length （）-（`startIndex`）））  + |只有當 `startIndex` 是大於或等於 0 的整數時，才支援 Remove(`count`, `count`)。|
|System.String Replace(String `oldValue`, String `newValue`)|Replace(`this`, `oldValue`, `newValue`)||
|System.String Substring(Int32 `startIndex`)|Substring(`this`, `startIndex` +1, Length(`this`) - `startIndex`)||
|System.String Substring(Int32 `startIndex`, Int32 `length`)|Substring （`this`， `startIndex` + 1， `length`）||
|System.String ToLower()|ToLower(`this`)||
|System.String ToUpper()|ToUpper(`this`)||
|System.String Trim()|Trim(`this`)||
|System.String TrimEnd(Char[] `trimChars`)|RTrim(`this`)||
|System.String TrimStart(Char[]`trimChars`)|LTrim(`this`)||
|Boolean Equals(String `value`)|= 運算子||

## <a name="systemdatetime-method-static-mapping"></a>System.DateTime 方法 (靜態) 對應

|System.DateTime 方法 (靜態)|標準函式|注意|
|---------------------------------------|------------------------|-----------|
|Boolean Equals(DateTime `t1`, DateTime `t2`)|= 運算子||
|System.DateTime.Now|CurrentDateTime()||
|System.DateTime.UtcNow|CurrentUtcDateTime()||
|Boolean op_Equality(DateTime `d1`, DateTime `d2`)|= 運算子||
|Boolean op_GreaterThan(DateTime `t1`, DateTime `t2`)|> 運算子||
|Boolean op_GreaterThanOrEqual(DateTime `t1`, DateTime `t2`)|> = 運算子||
|Boolean op_Inequality(DateTime `t1`, DateTime `t2`)|!= 運算子||
|布林值 op_LessThan （ `t1`datetime， `t2`datetime）|< 運算子||
|Boolean op_LessThanOrEqual(DateTime `t1`, DateTime `t2`)|< = 運算子||
|Microsoft.VisualBasic.DateAndTime.DatePart( _<br /><br /> ByVal `Interval`為 DateInterval，\_<br /><br /> ByVal `DateValue`做為 DateTime，\_<br /><br /> 選擇性的`FirstDayOfWeekValue` ByVal As FirstDayOfWeek = VbSunday，\_<br /><br /> 選擇性的`FirstWeekOfYearValue` ByVal As FirstWeekOfYear = VbFirstJan1\_<br /><br /> ) As Integer||如需詳細資訊，請參閱「DatePart 函式」一節。|
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||
|Microsoft.VisualBasic.DateAndTime.Year(DateTime `TimeValue`)|Year()||
|Microsoft.VisualBasic.DateAndTime.Month(DateTime `TimeValue`)|Month()||
|Microsoft.VisualBasic.DateAndTime.Day(DateTime `TimeValue`)|Day()||
|Microsoft.VisualBasic.DateAndTime.Hour(DateTime `TimeValue`)|Hour()||
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|Minute()||
|Microsoft.VisualBasic.DateAndTime.Second(DateTime `TimeValue`)|Second()||

## <a name="systemdatetime-method-instance-mapping"></a>System.DateTime 方法 (執行個體) 對應

|System.DateTime 方法 (執行個體)|標準函式|
|-----------------------------------------|------------------------|
|Boolean Equals(DateTime `value`)|= 運算子|
|Day|Day(`this`)|
|Hour|Hour(`this`)|
|Millisecond|Millisecond(`this`)|
|Minute|Minute(`this`)|
|Month|Month(`this`)|
|第二個|Second(`this`)|
|Year|Year(`this`)|

## <a name="systemdatetimeoffset-method-instance-mapping"></a>System.DateTimeOffset 方法 (執行個體) 對應

為列出之屬性上的 `get` 方法顯示的對應。

|System.DateTimeOffset 方法 (執行個體)|標準函式|注意|
|-----------------------------------------------|------------------------|-----------|
|Day|Day(`this`)|對 SQL Server 2005 不支援。|
|Hour|Hour(`this`)|對 SQL Server 2005 不支援。|
|Millisecond|Millisecond(`this`)|對 SQL Server 2005 不支援。|
|Minute|Minute(`this`)|對 SQL Server 2005 不支援。|
|Month|Month(`this`)|對 SQL Server 2005 不支援。|
|第二個|Second(`this`)|對 SQL Server 2005 不支援。|
|Year|Year(`this`)|對 SQL Server 2005 不支援。|

> [!NOTE]
> 如果比較的 <xref:System.DateTimeOffset.Equals%2A> 物件相等，`true` 方法會傳回 <xref:System.DateTimeOffset>；否則會傳回 `false`。 <xref:System.DateTimeOffset.CompareTo%2A> 方法會傳回 0、1 或 -1，需視比較的 <xref:System.DateTimeOffset> 物件是否分別為相等、大於或小於而定。

## <a name="systemdatetimeoffset-method-static-mapping"></a>System.DateTimeOffset 方法 (靜態) 對應

為列出之屬性上的 `get` 方法顯示的對應。

|System.DateTimeOffset 方法 (靜態)|標準函式|注意|
|---------------------------------------------|------------------------|-----------|
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|對 SQL Server 2005 不支援。|

## <a name="systemtimespan-method-instance-mapping"></a>System.TimeSpan 方法 (執行個體) 對應

為列出之屬性上的 `get` 方法顯示的對應。

|System.TimeSpan 方法 (執行個體)|標準函式|注意|
|-----------------------------------------|------------------------|-----------|
|小時|Hour(`this`)|對 SQL Server 2005 不支援。|
|Milliseconds|Millisecond(`this`)|對 SQL Server 2005 不支援。|
|分鐘|Minute(`this`)|對 SQL Server 2005 不支援。|
|Seconds|Second(`this`)|對 SQL Server 2005 不支援。|

> [!NOTE]
> 如果比較的 <xref:System.TimeSpan.Equals%2A> 物件相等，`true` 方法會傳回 <xref:System.TimeSpan>；否則會傳回 `false`。 <xref:System.TimeSpan.CompareTo%2A> 方法會傳回 0、1 或 -1，需視比較的 <xref:System.TimeSpan> 物件是否分別為相等、大於或小於而定。

### <a name="datepart-function"></a>DatePart 函式

`DatePart` 函式會對應到幾個不同標準函式的其中一個，根據 `Interval` 的值而定。 下表顯示支援之 `Interval` 值的標準函式對應：

|間隔值|標準函式|
|--------------------|------------------------|
|DateInterval.Year|Year()|
|DateInterval.Month|Month()|
|DateInterval.Day|Day()|
|DateInterval.Hour|Hour()|
|DateInterval.Minute|Minute()|
|DateInterval.Second|Second()|

## <a name="mathematical-function-mapping"></a>數學函式對應

|CLR 方法|標準函式|
|----------------|------------------------|
|System.Decimal.Ceiling(Decimal `d`)|Ceiling(`d`)|
|System.Decimal.Floor(Decimal `d`)|Floor(`d`)|
|System.Decimal.Round(Decimal `d`)|Round(`d`)|
|System.Math.Ceiling(Decimal `d`)|Ceiling(`d`)|
|System.Math.Floor(Decimal `d`)|Floor(`d`)|
|System.Math.Round(Decimal `d`)|Round(`d`)|
|System.Math.Ceiling(Double `a`)|Ceiling(`a`)|
|System.Math.Floor(Double `a`)|Floor(`a`)|
|System.Math.Round(Double `a`)|Round(`a`)|
|System.Math.Round(雙精度浮點數值、Int16 數字)|Round(值、數字)|
|System.Math.Round(雙精度浮點數值、Int32 數字)|Round(值、數字)|
|System.Math.Round(十進位值、Int16 數字)|Round(值、數字)|
|System.Math.Round(十進位值、Int32 數字)|Round(值、數字)|
|System.Math.Abs(Int16 值)|Abs(value)|
|System.Math.Abs(Int32 值)|Abs(value)|
|System.Math.Abs(Int64 值)|Abs(value)|
|System.Math.Abs(位元組值)|Abs(value)|
|System.Math.Abs(單一值)|Abs(value)|
|System.Math.Abs(雙精度浮點數值)|Abs(value)|
|System.Math.Abs(十進位值)|Abs(value)|
|System.Math.Truncate(雙精度浮點數值、Int16 數字)|Truncate(值、數字)|
|System.Math.Truncate(雙精度浮點數值、Int32 數字)|Truncate(值、數字)|
|System.Math.Truncate(十進位值、Int16 數字)|Truncate(值、數字)|
|System.Math.Truncate(十進位值、Int32 數字)|Truncate(值、數字)|
|System.Math.Power(Int32 值、Int64 指數)|Power(值、指數)|
|System.Math.Power(Int32 值、雙精度浮點指數)|Power(值、指數)|
|System.Math.Power(Int32 值、十進位指數)|Power(值、指數)|
|System.Math.Power(Int64 值、Int64 指數)|Power(值、指數)|
|System.Math.Power(Int64 值、雙精度浮點指數)|Power(值、指數)|
|System.Math.Power(Int64 值、十進位指數)|Power(值、指數)|
|System.Math.Power(雙精度浮點數值、Int64 指數)|Power(值、指數)|
|System.Math.Power(雙精度浮點數值、雙精度浮點指數)|Power(值、指數)|
|System.Math.Power(雙精度浮點數值、十進位指數)|Power(值、指數)|
|System.Math.Power(十進位值、Int64 指數)|Power(值、指數)|
|System.Math.Power(十進位值、雙精度浮點指數)|Power(值、指數)|
|System.Math.Power(十進位值、十進位指數)|Power(值、指數)|

## <a name="bitwise-operator-mapping"></a>位元運算子對應

|位元運算子|非布林運算元的標準函式|布林運算元的標準函式|
|----------------------|--------------------------------------------------|---------------------------------------------|
|位元 AND 運算子|BitWiseAnd|op1 AND op2|
|位元 OR 運算子|BitWiseOr|op1 OR op2|
|位元 NOT 運算子|BitWiseNot|NOT(op)|
|位元 XOR 運算子|BitWiseXor|((op1 AND NOT(op2)) OR (NOT(op1) AND op2))|

## <a name="other-mapping"></a>其他對應

|方法|標準函式|
|------------|------------------------|
|Guid.NewGuid()|NewGuid()|

## <a name="see-also"></a>另請參閱

- [LINQ to Entities](linq-to-entities.md)
