---
title: 數學函式
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268965"
---
# <a name="mathematical-functions"></a>數學函式

.NET Framework Data Provider for SQL Server (SqlClient) 提供了數學函式，這些函式會在當做引數提供的輸入值上執行計算，並傳回數值結果。 這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。 提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。下表將描述 SqlClient 數學函式。  
  
## <a name="absexpression"></a>ABS(expression)

執行絕對值函式。

**引數**

`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。

**傳回值**

指定之運算式的絕對值。

**範例**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS(expression)

傳回指定之運算式的反餘弦函數 (Arccosine) 值。

**引數**

`expression`：`Double`。

**傳回值**

`Double`。

**範例**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN(expression)

傳回指定之運算式的反正弦函數 (Arcsine) 值。

**引數**

`expression`：`Double`。

**傳回值**

`Double`。

**範例**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN(expression)

傳回指定之數值運算式的反正切函數 (Arctangent) 值。

**引數**

`expression`：`Double`。

**傳回值**

`Double`。

**範例**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2(expression, expression)

傳回其正切函數 (Tangent) 介於兩個指定數值運算式之間的角度 (以弧度為單位)。

**引數**

`expression`：`Double`。

**傳回值**

`Double`。

**範例**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>CEILING(expression)

將指定的運算式轉換成大於或等於它的最小整數。

**引數**

`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。

**傳回值**

`Int32`， `Int64`， `Double`，或`Decimal`。

**範例** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS(expression)

計算指定之角度的三角餘弦函數 (Cosine) (以弧度為單位)。 

**引數** 

`expression`：`Double`。 

**傳回值** 

`Double`。 

**範例** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT(expression)

計算指定之角度的三角餘切函數 (Cotangent) (以弧度為單位)。 

**引數** 

`expression`：`Double`。 

**傳回值** 

`Double`。 

**範例** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DEGREES(radians)

傳回以度數表示的對應角度。 

**引數** 

`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。 

**傳回值** 

`Int32`， `Int64`， `Double`，或`Decimal`。 

**範例** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP(expression)

計算指定之數值運算式的指數值。 

**引數** 

`expression`：`Double`。 

**傳回值** 

`Double`。 

**範例** `SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR(expression)

將指定的運算式轉換成小於或等於它的最大整數。 

**引數** 

`expression`：`Double`。 

**傳回值** 

`Double`。 

**範例** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG(expression)

計算指定之 `float` 運算式的自然對數。 

**引數** 

`expression`：`Double`。 

**傳回值** 

`Double`。 

**範例** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10(expression)

傳回指定 `Double` 運算式的以 10 為基底之對數。 

**引數** 

`expression`：`Double`。 

**傳回值** 

`Double`。 

**範例** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI （)

以 `Double` 形式傳回 pi 的常數值。 

**傳回值** 

`Double`。 

**範例** 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a>POWER （numeric_expression，power_expression）

將指定之運算式的值計算至指定的乘冪。

**引數** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`， `Int64`， `Double`，或`Decimal`。|
|`power_expression`| A`Double`表示要引發 power `numeric_expression`。| 

**傳回值** 

指定之 `numeric_expression` 自乘至指定之 `power_expression` 的值。 

**範例** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANS(expression)

將度數轉換成弧度。 

**引數** 

`expression`：`Int32`、`Int64`、`Double` 或 `Decimal`。 

**傳回值** 

`Int32`， `Int64`， `Double`，或`Decimal`。 

**範例** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND([seed])

傳回 0 到 1 的隨機值。 

**引數** 

初始值為`Int32`。 如果沒有指定初始值，SQL Server Database Engine 就會隨機指派一個初始值。 只要指定初始值之後，傳回的結果一律相同。

**傳回值** 

0 到 1 的隨機 `Double` 值。 

**範例** 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a>ROUND(numeric_expression, length[,function])

傳回已經進位到指定長度或有效位數的數值運算式。 

**引數** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`， `Int64`， `Double`，或`Decimal`。 
|`length`| `Int32`，代表 `numeric_expression` 要四捨五入的精確度。 當 `length` 是正數時，`numeric_expression` 會四捨五入到 `length` 所指定的十進位數。 當 `length` 是負數時，`numeric_expression` 會依照 `length` 所指定，在小數點左側四捨五入。|
|`function` | 選擇性。 `Int32` ，表示要執行的作業類型。 當函式遭到省略或者值為 0 （預設）、`numeric_expression`會捨入。 指定 0 以外的值時，`numeric_expression`會被截斷。 |

**傳回值** 

指定之 `numeric_expression` 自乘至指定之 `power_expression` 的值。

**範例** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN(expression) 

傳回指定運算式的正 (+1)、零 (0) 或負 (-1) 號。 

**引數** 

`expression`：`Int32`、`Int64`、`Double` 或 `Decimal` 

**傳回值** 

`Int32`， `Int64`， `Double`，或`Decimal`。 

**範例** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN(expression)

計算指定之角度的三角正弦函數 (Sine) (以弧度為單位)，並傳回 `Double` 運算式。 

**引數** 

`expression`：`Double`。 

**傳回值** 

`Double`。 

**範例** `SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT(expression)

傳回指定之運算式的平方根。 

**引數** 

`expression`：`Double`。 

**傳回值** 

`Double`。 

**範例** `SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>SQUARE(expression)

傳回指定之運算式的平方。 

**引數** 

`expression`：`Double`。 

**傳回值** 

`Double`。 

**範例** 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN(expression)

計算指定之運算式的正切函數。

**引數** 

`expression`: `Double` 

**傳回值** 

`Double` 

**範例** 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>另請參閱

如需 SqlClient 支援之數學函式的詳細資訊，請參閱 SqlClient 提供者資訊清單中所指定之 SQL Server 版本的說明文件：  
  
**SQL Server 2005:** [數學函數 & Amp;#40;transact-SQL&AMP;#41;](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))  
**SQL Server 2008:** [數學函數 & Amp;#40;transact-SQL&AMP;#41;](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))  
**SQL Server 2012 及更新版本：** [數學函數 & Amp;#40;transact-SQL&AMP;#41;](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)   

 [適用於 Entity Framework 的 SqlClient 函式](sqlclient-for-ef-functions.md)
