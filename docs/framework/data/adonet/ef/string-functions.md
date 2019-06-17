---
title: 字串函式
ms.date: 03/30/2017
ms.assetid: 338f0c26-8aee-43eb-bd1a-ec0849a376b9
ms.openlocfilehash: 3eb70151628e32f6ad0a87be8ff0cd071ae89235
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041603"
---
# <a name="string-functions"></a>字串函式
.NET Framework Data Provider for SQL Server (SqlClient) 提供了 `String` 函式，這些函式會針對輸入 `String` 執行作業，並傳回 `String` 或數值結果。 這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。 提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。  
  
 下表顯示 SqlClient `String` 函式。  
  
|功能|描述|  
|--------------|-----------------|  
|`ASCII(expression)`|傳回字串運算式最左側字元的 ASCII 字碼值。<br /><br /> **引數**<br /><br /> `expression`：任何有效運算式的 ASCII`String`型別。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.ASCII('A')`|  
|`CHAR(expression)`|將 `Int32` 程式碼轉換成 ASCII 字串。<br /><br /> **引數**<br /><br /> `expression`：`Int32`。<br /><br /> **傳回值**<br /><br /> ASCII `String`。<br /><br /> **範例**<br /><br /> `SqlServer.char(97)`|  
|`CHARINDEX(expression1, expression2 [, start_location])`|傳回指定運算式在某個字元字串中的起始位置。<br /><br /> **引數**<br /><br /> `expression1`：含有要尋找之字元順序的運算式。 此運算式可以是 String (ASCII 或 Unicode) 型別或 Binary 型別。<br /><br /> `expression2`：通常是搜尋指定順序之資料行的運算式。 此運算式可以是 String (ASCII 或 Unicode) 型別或 Binary 型別。<br /><br /> `start_location`: （選擇性) Int64 （SQL Server 2000 中不會傳回） 或 Int32，代表要開始搜尋 expression2 中 expression1 的字元位置。 如果 start_location 沒有指定、為負數或者為零，則此搜尋就會從 expression2 的起點開始。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.CHARINDEX('h', 'habcdefgh', 2)`|  
|`DIFFERENCE(expression, expression)`|會比較兩個字串的 `SOUNDEX` 值，並評估兩者的相似度。<br /><br /> **引數**<br /><br /> ASCII 或 Unicode `String` 型別。 `expression` 可以是常數、變數或資料行。<br /><br /> **傳回值**<br /><br /> 傳回表示兩個字元運算式之 SOUNDEX 值之間差異的 `Int32`。 範圍是從 0 到 4。 0 表示相似度弱或沒有相似度，4 表示相似性強或值相同。<br /><br /> **範例**<br /><br /> `// The following example returns a DIFFERENCE value of 4,`<br /><br /> `//the least possible difference or the best match.`<br /><br /> `SqlServer.DIFFERENCE('Green','Greene');`|  
|`LEFT(expression, count)`|傳回指定字元數之字元字串的左側部分。<br /><br /> **引數**<br /><br /> `expression`：Unicode 或 ASCII String 型別。 使用 CAST 函式可明確轉換 character_expression。<br /><br /> `count`：`Int64` （SQL Server 2000 中不會傳回） 或`Int32`指定將傳回多少 character_expression 字元數的型別。<br /><br /> **傳回值**<br /><br /> Unicode 或 ASCII `String`。<br /><br /> **範例**<br /><br /> `SqlServer.LEFT('SQL Server', 4)`|  
|`LEN(expression)`|傳回指定 String 運算式中的字元數，但尾端空白不算。<br /><br /> **引數**<br /><br /> `expression`：運算式`String`（Unicode 或 ASCII） 型別或`Binary`類型<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.LEN('abcd')`|  
|`LOWER(expression)`|將大寫字元資料轉換成小寫之後，傳回 `String` 運算式。<br /><br /> **引數**<br /><br /> `expression`：`String` 型別的任何有效運算式。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `SqlServer.LOWER('AbB')`|  
|`LTRIM(expression)`|移除開頭空白之後，傳回 `String` 運算式。<br /><br /> **引數**<br /><br /> `expression`：`String` 型別的任何有效運算式。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `SqlServer.LTRIM('   d')`|  
|`NCHAR(expression)`|依照 Unicode 標準所定義，傳回含指定整數碼的 Unicode `String`。<br /><br /> **引數**<br /><br /> `expression`：`Int32`。<br /><br /> **傳回值**<br /><br /> Unicode `String`。<br /><br /> **範例**<br /><br /> `SqlServer.NCHAR(65)`|  
|`PATINDEX('%pattern%', expression)`|傳回某個模式在指定之 `String` 運算式中第一次出現的開始位置。<br /><br /> **引數**<br /><br /> `'%pattern%'`：ASCII 或 Unicode `String` 型別。 此處可以使用萬用字元，但是模式前後都必須加上 % 字元 (除非要搜尋第一個或最後一個字元)。<br /><br /> `expression`：要搜尋指定之模式的 ASCII 或 Unicode `String`。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.PATINDEX('abc', 'ab')`|  
|`QUOTENAME('char_string' [, 'quote_char'])`|傳回 Unicode `String`，且附加分隔符號，讓輸入字串成為有效的 SQL Server 2005 分隔識別碼。<br /><br /> **引數**<br /><br /> `char_string`：Unicode `String`。<br /><br /> `quote_char`：用來作為分隔符號的單字元字串。 它可以是單引號 ( ' )、左或右方括號 ( [ ] )，或雙引號 ( " )。 如果未指定 `quote_char`，就會使用方括號。<br /><br /> **傳回值**<br /><br /> Unicode `String`。<br /><br /> **範例**<br /><br /> `SqlServer.QUOTENAME('abc[]def')`|  
|`REPLACE(expression1, expression2, expression3)`|另一個的字元運算式中取代的字元運算式。<br /><br /> **引數**<br /><br /> `expression1`：要搜尋的字串運算式。 `expression1` 可以是 Unicode 或 ASCII String 型別。<br /><br /> `expression2`: 要尋找的子字串。 `expression2` 可以是 Unicode 或 ASCII String 型別。<br /><br /> `expression3`；取代字串。 `expression3` 可以是 Unicode 或 ASCII String 型別。<br /><br /> **範例**<br /><br /> `SqlServer.REPLACE('aabbcc', 'bc', 'zz')`|  
|`REPLICATE(char_expression, int_expression)`|以指定次數重複字元運算式。<br /><br /> **引數**<br /><br /> `char_expression`：Unicode 或 ASCII `String` 型別。<br /><br /> `int_expression`：`Int64` (在 SQL Server 2000 中不支援) 或 `Int32`。<br /><br /> **傳回值**<br /><br /> Unicode 或 ASCII `String` 型別。<br /><br /> **範例**<br /><br /> `SqlServer.REPLICATE('aa',2)`|  
|`REVERSE(expression)`|傳回字元位置與輸入字串相反的 Unicode 或 ASCII String。<br /><br /> **引數**<br /><br /> `expression`：Unicode 或 ASCII `String` 型別。<br /><br /> **傳回值**<br /><br /> Unicode 或 ASCII `String` 型別。<br /><br /> **範例**<br /><br /> `SqlServer.REVERSE('abcd')`|  
|`RIGHT(char_expression, count)`|傳回指定字元數之字元字串的右側部分。<br /><br /> **引數**<br /><br /> `char_expression`: Unicode 或 ASCII String 型別。 使用 CAST 函式可明確轉換 character_expression。<br /><br /> `count`：`Int64` （SQL Server 2000 中不會傳回） 或`Int32`指定將傳回多少 character_expression 字元數的型別。<br /><br /> **傳回值**<br /><br /> ASCII `String` 型別。<br /><br /> **範例**<br /><br /> `SqlServer.RIGHT('SQL Server', 6)`|  
|`RTRIM(expression)`|傳回移除尾端空格之後的 Unicode 或 ASCII String。<br /><br /> **引數**<br /><br /> `expression`：Unicode 或 ASCII `String` 型別。<br /><br /> **傳回值**<br /><br /> Unicode 或 ASCII `String` 型別。<br /><br /> **範例**<br /><br /> `SqlServer.RTRIM('   d   e      ')`|  
|`SOUNDEX(expression)`|傳回四個字元 (SOUNDEX) 代碼來評估兩個字串的相似度。**引數**<br /><br /> `expression`：Unicode 或 ASCII String 型別。<br /><br /> **傳回值**<br /><br /> ASCII `String`。 四個字元的 (SOUNDEX) 代碼是用來評估兩個字串之相似度的一個字串。<br /><br /> **範例**<br /><br /> `Select SqlServer.SOUNDEX('Smith'), SqlServer.SOUNDEX('Smythe') FROM {1}`<br /><br /> **傳回**<br /><br /> `----- -----  S530  S530`|  
|`SPACE(int_expression)`|傳回重複空格的 ASCII `String`。<br /><br /> **引數**<br /><br /> `int_expression`：`Int64` （SQL Server 2000 中不會傳回） 或`Int32`表示的空格數目。<br /><br /> **傳回值**<br /><br /> ASCII `String`。<br /><br /> **範例**<br /><br /> `SqlServer.SPACE(2)`|  
|`STR(float_expression [, length [, decimal]])`|傳回從數值資料轉換而來的 ASCII `String`。<br /><br /> **引數**<br /><br /> `float _expression`：含小數點之近似數值 (`Double`) 資料型別的運算式。<br /><br /> `length`：(選擇項) 代表總長度的 `Int32`。 其中包括小數點、正負號、位數和空格。 預設值為 10。<br /><br /> `decimal`: (選擇性)`Int32`表示小數點右邊的位數。 小數位數必須小於或等於 16。 如果小數位數超過 16，結果將會被截斷成小數點右邊的 16 位數。<br /><br /> **傳回值**<br /><br /> ASCII `String`。<br /><br /> **範例**<br /><br /> `SqlServer.STR(212.0)`|  
|`STUFF(str_expression, start, length, str_expression_to_insert)`|刪除指定長度的字元，並在字串運算式中指定的起點插入另一組字元。<br /><br /> **引數**<br /><br /> `str_expression`：Unicode 或 ASCII `String`。<br /><br /> `start:` `Int64` （SQL Server 2000 中不會傳回） 或`Int32`值，指定開始刪除和插入的位置。<br /><br /> `length`：`Int64` (SQL Server 2000 中不會傳回) 或指定要刪除之字元數的 `Int32` 值。<br /><br /> `str_expression_to_insert`：Unicode 或 ASCII `String`。<br /><br /> **傳回值**<br /><br /> Unicode 或 ASCII `String`。<br /><br /> **範例**<br /><br /> `SqlServer.STUFF('abcd', 2, 2, 'zz')`|  
|`SUBSTRING(str_expression, start, length)`|傳回 `String` 運算式的一部分。<br /><br /> **引數**<br /><br /> `str_expression`：具有 `String` (ASCII 或 Unicode) 型別或 `Binary` 型別的運算式。<br /><br /> `start`：`Int64` （SQL Server 2000 中不會傳回） 或`Int32`指定子字串開始的位置。 1 代表字串中的第一個字元。<br /><br /> `length`：`Int64` （SQL Server 2000 中不會傳回） 或`Int32`，指定將傳回運算式的字元數。<br /><br /> **傳回值**<br /><br /> `String` (ASCII 或 Unicode) 型別或 `Binary` 型別。<br /><br /> **範例**<br /><br /> `SqlServer.SUBSTRING('abcd', 2, 2)`|  
|`UNICODE(expression)`|依照 Unicode 標準所定義，傳回輸入運算式第一個字元的整數值。<br /><br /> **引數**<br /><br /> `expression`：Unicode `String`。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `SqlServer.UNICODE('a')`|  
|`UPPER(expression)`|將小寫字元資料轉換成大寫之後，傳回 `String` 運算式。<br /><br /> **引數**<br /><br /> `expression`：ASCII 或 Unicode String 型別的運算式。<br /><br /> **傳回值**<br /><br /> ASCII 或 Unicode `String` 型別。<br /><br /> **範例**<br /><br /> `SqlServer.UPPER('AbB')`|  
  
 如需 SqlClient 所支援 `String` 函式的詳細資訊，請參閱 SqlClient 提供者資訊清單中所指定 SQL Server 版本的說明文件：  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[字串函式 (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115915)|[字串函式 (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115916)|[字串函式 (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115914)|  
  
## <a name="see-also"></a>另請參閱

- [適用於 Entity Framework 的 SqlClient 函式](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
- [適用於 Entity Framework 的 SqlClient 已知問題](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)
