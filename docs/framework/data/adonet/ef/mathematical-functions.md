---
title: 數學函式
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 9dfd1faf9bdab995b19c38e32f64a88ed67cb280
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mathematical-functions"></a>數學函式
.NET Framework Data Provider for SQL Server (SqlClient) 提供了數學函式，這些函式會在當做引數提供的輸入值上執行計算，並傳回數值結果。 這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。 提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。下表將描述 SqlClient 數學函式。  
  
|函式|描述|  
|--------------|-----------------|  
|`ABS(` `expression` `)`|執行絕對值函式。<br /><br /> **引數**<br /><br /> `expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。<br /><br /> **傳回值**<br /><br /> 指定之運算式的絕對值。<br /><br /> **範例**<br /><br /> `SqlServer.ABS(-2)`|  
|`ACOS(` `expression` `)`|傳回指定之運算式的反餘弦函數 (Arccosine) 值。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.ACOS(.9)`|  
|`ASIN(` `expression` `)`|傳回指定之運算式的反正弦函數 (Arcsine) 值。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.ASIN(.9)`|  
|`ATAN(` `expression` `)`|傳回指定之數值運算式的反正切函數 (Arctangent) 值。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.ATAN(9)`|  
|`ATN2(` `expression`, `expression``)`|傳回其正切函數 (Tangent) 介於兩個指定數值運算式之間的角度 (以弧度為單位)。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.ATN2(9, 8)`|  
|`CEILING(` `expression` `)`|將指定的運算式轉換成大於或等於它的最小整數。<br /><br /> **引數**<br /><br /> `expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。<br /><br /> **傳回值**<br /><br /> `Int32`， `Int64`， `Double`，或`Decimal`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]|  
|`COS(` `expression` `)`|計算指定之角度的三角餘弦函數 (Cosine) (以弧度為單位)。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.COS(45)`|  
|`COT(` `expression` `)`|計算指定之角度的三角餘切函數 (Cotangent) (以弧度為單位)。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.COT(60)`|  
|`DEGREES(` `radians` `)`|傳回以度數表示的對應角度。<br /><br /> **引數**<br /><br /> `expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。<br /><br /> **傳回值**<br /><br /> `Int32`， `Int64`， `Double`，或`Decimal`。<br /><br /> **範例**<br /><br /> `SqlServer.DEGREES(3.1)`|  
|`EXP(` `expression` `)`|計算指定之數值運算式的指數值。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.EXP(1)`|  
|`FLOOR(` `expression` `)`|將指定的運算式轉換成小於或等於它的最大整數。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]|  
|`LOG(` `expression` `)`|計算指定之 `float` 運算式的自然對數。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.LOG(100)`|  
|`LOG10(` `expression` `)`|傳回指定 `Double` 運算式的以 10 為基底之對數。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.LOG10(100)`|  
|`PI()`|以 `Double` 形式傳回 pi 的常數值。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.PI()`|  
|`POWER(` `numeric_expression, power_expression` `)`|將指定之運算式的值計算至指定的乘冪。<br /><br /> **引數**<br /><br /> `numeric_expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。<br /><br /> `power_expression`：代表 `Double` 乘冪數的 `numeric_expression`。<br /><br /> **傳回值**<br /><br /> 指定之 `numeric_expression` 自乘至指定之 `power_expression` 的值。<br /><br /> **範例**<br /><br /> `SqlServer.POWER(2,7)`|  
|`RADIANS(` `expression` `)`|將度數轉換成弧度。<br /><br /> **引數**<br /><br /> `expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。<br /><br /> **傳回值**<br /><br /> `Int32`， `Int64`，<br /><br /> `Double` 或<br /><br /> `Decimal`.<br /><br /> **範例**<br /><br /> `SqlServer.RADIANS(360.0)`|  
|`RAND(`[seed]`)`|傳回 0 到 1 的隨機值。<br /><br /> **引數**<br /><br /> 將初始值當做 `Int32` 傳回。 如果沒有指定初始值，SQL Server Database Engine 就會隨機指派一個初始值。 只要指定初始值之後，傳回的結果一律相同。<br /><br /> **傳回值**<br /><br /> 0 到 1 的隨機 `Double` 值。<br /><br /> **範例**<br /><br /> `SqlServer.RAND()`|  
|`ROUND(` `numeric_expression, length` [ ,`function` ]`)`|傳回已經進位到指定長度或有效位數的數值運算式。<br /><br /> **引數**<br /><br /> `numeric_expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。<br /><br /> `length`：`Int32`，代表 `numeric_expression` 要四捨五入的精確度。 當 `length` 是正數時，`numeric_expression` 會四捨五入到 `length` 所指定的十進位數。 當 `length` 是負數時，`numeric_expression` 會依照 `length` 所指定，在小數點左側四捨五入。<br /><br /> `function`: (選擇性) `Int32` ，代表要執行的作業類型。 當省略 function，或具有值為 0 （預設）、`numeric_expression`會捨入。 指定 0 以外的值時，`numeric_expression`會被截斷。<br /><br /> **傳回值**<br /><br /> 指定之 `numeric_expression` 自乘至指定之 `power_expression` 的值。<br /><br /> **範例**<br /><br /> `SqlServer.ROUND(748.58, -3)`|  
|`SIGN(` `expression` `)`|傳回指定運算式的正 (+1)、零 (0) 或負 (-1) 號。<br /><br /> **引數**<br /><br /> `expression`：`Int32`、`Int64`、`Double` 或 `Decimal`<br /><br /> **傳回值**<br /><br /> `Int32`， `Int64`， `Double`，或`Decimal`。<br /><br /> **範例**<br /><br /> `SqlServer.SIGN(-10)`|  
|`SIN(` `expression` `)`|計算指定之角度的三角正弦函數 (Sine) (以弧度為單位)，並傳回 `Double` 運算式。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.SIN(20)`|  
|`SQRT(` `expression` `)`|傳回指定之運算式的平方根。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.SQRT(3600)`|  
|`SQUARE(` `expression` `)`|傳回指定之運算式的平方。<br /><br /> **引數**<br /><br /> `expression`：`Double`。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> `SqlServer.SQUARE(25)`|  
|`TAN(` `expression` `)`|計算指定之運算式的正切函數。<br /><br /> **引數**<br /><br /> `expression`: `Double`<br /><br /> **傳回值**<br /><br /> `Double`<br /><br /> **範例**<br /><br /> `SqlServer.TAN(45.0)`|  
  
 如需 SqlClient 支援之數學函式的詳細資訊，請參閱 SqlClient 提供者資訊清單中所指定之 SQL Server 版本的說明文件：  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[數學函數 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115913)|[數學函數 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115911)|[數學函數 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115912)|  
  
## <a name="see-also"></a>另請參閱  
 [適用於 Entity Framework 的 SqlClient 函式](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
