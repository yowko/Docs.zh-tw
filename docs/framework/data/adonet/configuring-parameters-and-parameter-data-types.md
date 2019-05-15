---
title: 設定參數和參數資料類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: 5d35e2775c6c6912d2a36c550202b309ebdeaa32
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583835"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>設定參數和參數資料類型

命令物件會使用參數將值傳遞至 SQL 陳述式或預存程序 (Stored Procedure)，以提供型別檢查及驗證。 與命令文字不同的是，參數輸入會被視為常值 (Literal)，而非可執行程式碼。 這有助於防衛「SQL 插入式」攻擊，在此類攻擊中，攻擊者會將危害伺服器安全的命令插入 SQL 陳述式中。

參數型命令 (Parameterized Command) 也可以改善查詢執行效能，因為它們可以協助資料庫伺服器正確地比對內送命令與正確快取的查詢計畫。 如需詳細資訊，請參閱 <<c0> [ 執行計畫快取和重複使用](/sql/relational-databases/query-processing-architecture-guide#execution-plan-caching-and-reuse)並[參數和執行計畫的重複使用](/sql/relational-databases/query-processing-architecture-guide#PlanReuse)。 除了安全性和效能的優點以外，參數型命令也提供方便的方法，可讓您安排傳遞至資料來源的值。

<xref:System.Data.Common.DbParameter> 物件可透過其建構函式建立，或者透過呼叫 <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> 集合的 `Add` 方法，將其加入 <xref:System.Data.Common.DbParameterCollection> 來建立。 `Add` 方法會將建構函式引數或現有的參數物件當做輸出，依資料提供者而定。

## <a name="supplying-the-parameterdirection-property"></a>提供 ParameterDirection 屬性

在加入參數時，您必須為不是輸入參數的參數提供 <xref:System.Data.ParameterDirection> 屬性。 下表所顯示的 `ParameterDirection` 值是可以與 <xref:System.Data.ParameterDirection> 列舉一起使用的。

|成員名稱|描述|
|-----------------|-----------------|
|<xref:System.Data.ParameterDirection.Input>|這是輸入參數， 這是預設值。|
|<xref:System.Data.ParameterDirection.InputOutput>|這個參數可執行輸入和輸出。|
|<xref:System.Data.ParameterDirection.Output>|這是輸出參數。|
|<xref:System.Data.ParameterDirection.ReturnValue>|此參數代表預存程序 (Stored Procedure)、內建函式或使用者定義函式等作業的傳回值。|

## <a name="working-with-parameter-placeholders"></a>使用參數預留位置

參數預留位置的語法會隨資料來源而有所不同。 .NET Framework 資料提供者會以不同方式來處理參數和參數預留位置的命名及指定。 這個語法是特定資料來源專用的，如以下資料表所述：

|資料提供者|參數命名語法|
|-------------------|-----------------------------|
|<xref:System.Data.SqlClient>|以格式 `@`*parametername*使用具名參數。|
|<xref:System.Data.OleDb>|使用由問號 (`?`) 表示的位置參數標記。|
|<xref:System.Data.Odbc>|使用由問號 (`?`) 表示的位置參數標記。|
|<xref:System.Data.OracleClient>|以格式 `:`*parmname* (或 *parmname*) 使用具名參數。|

## <a name="specifying-parameter-data-types"></a>指定的參數資料類型

參數的資料型別是.NET Framework 資料提供者特有的。 指定類型的值轉換`Parameter`為.NET Framework 資料提供者型別，再將值傳遞至資料來源。 您也可以使用一般方式指定 `Parameter` 的型別，方法是將 `DbType` 物件的 `Parameter` 屬性設為特定的 <xref:System.Data.DbType>。

.NET Framework 資料提供者型別`Parameter`物件從.NET Framework 型別推斷`Value`的`Parameter`物件，或從`DbType`的`Parameter`物件。 下列表格說明根據以 `Parameter` 值或指定之 `Parameter` 來傳遞的物件而推斷出的 `DbType`型別。

|.NET Framework 類型|DbType|SqlDbType|OleDbType|OdbcType|OracleType|
|-------------------------|------------|---------------|---------------|--------------|----------------|
|<xref:System.Boolean>|Boolean|位元|Boolean|位元|Byte|
|<xref:System.Byte>|Byte|TinyInt|UnsignedTinyInt|TinyInt|Byte|
|byte[]|二元|VarBinary。 如果位元組陣列超過 VarBinary 的最大大小即 8000 個位元組，這項隱含轉換將會失敗。大於 8000 個位元組的位元組陣列，請明確設定<xref:System.Data.SqlDbType>。|VarBinary|二元|Raw|
|<xref:System.Char>| |不支援從 char 推斷 <xref:System.Data.SqlDbType> 。|Char|Char|Byte|
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|
|<xref:System.DateTimeOffset>|DateTimeOffset|SQL Server 2008 中的 DateTimeOffset。 SQL Server 2008 之前的 SQL Server 版本不支援從 DateTimeOffset 推斷 <xref:System.Data.SqlDbType> 。|||DateTime|
|<xref:System.Decimal>|Decimal|Decimal|Decimal|數值|number|
|<xref:System.Double>|Double|浮動|Double|Double|Double|
|<xref:System.Single>|Single|Real|Single|Real|浮動|
|<xref:System.Guid>|Guid|UniqueIdentifier|Guid|UniqueIdentifier|Raw|
|<xref:System.Int16>|Int16|SmallInt|SmallInt|SmallInt|Int16|
|<xref:System.Int32>|Int32|Int|Int|Int|Int32|
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|數字|
|<xref:System.Object>|Object|變異|變異|不支援從 Object 推斷 OdbcType。|Blob|
|<xref:System.String>|String|NVarChar。 如果字串超過 NVarChar 的最大大小 (4000 個字元)，則這項隱含轉換將會失敗。 若要使用超過 4000 個字元的字串，請明確設定 <xref:System.Data.SqlDbType>。|VarWChar|NVarChar|NVarChar|
|<xref:System.TimeSpan>|時間|SQL Server 2008 中的 Time。 SQL Server 2008 之前的 SQL Server 版本不支援從 TimeSpan 推斷 <xref:System.Data.SqlDbType> 。|DBTime|時間|DateTime|
|<xref:System.UInt16>|UInt16|不支援從 UInt16 推斷 <xref:System.Data.SqlDbType> 。|UnsignedSmallInt|Int|UInt16|
|<xref:System.UInt32>|UInt32|不支援從 UInt32 推斷 <xref:System.Data.SqlDbType> 。|UnsignedInt|BigInt|UInt32|
|<xref:System.UInt64>|UInt64|不支援從 UInt64 推斷 <xref:System.Data.SqlDbType> 。|UnsignedBigInt|數值|number|
||AnsiString|VarChar|VarChar|VarChar|VarChar|
||AnsiStringFixedLength|Char|Char|Char|Char|
||貨幣|Money|貨幣|不支援從 `OdbcType` 推斷 `Currency` 。|number|
||日期|SQL Server 2008 中的 Date。 SQL Server 2008 之前的 SQL Server 版本不支援從 Date 推斷 <xref:System.Data.SqlDbType> 。|DBDate|Date|DateTime|
||SByte|不支援從 SByte 推斷 <xref:System.Data.SqlDbType> 。|TinyInt|不支援從 SByte 推斷 `OdbcType` 。|SByte|
||StringFixedLength|NChar|WChar|NChar|NChar|
||時間|SQL Server 2008 中的 Time。 SQL Server 2008 之前的 SQL Server 版本不支援從 Time 推斷 <xref:System.Data.SqlDbType> 。|DBTime|時間|DateTime|
||VarNumeric|不支援從 VarNumeric 推斷 <xref:System.Data.SqlDbType> 。|VarNumeric|不支援從 VarNumeric 推斷 `OdbcType` 。|number|
|使用者定義型別 (包含 <xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>的物件)|Object 或 String 是取決於提供者而定 (SqlClient 一律會傳回 Object，Odbc 一律會傳回 String，而 OleDb Managed 資料提供者可查看這兩者)|若 <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> 存在即為 SqlDbType.Udt，否則為 Variant|OleDbType.VarWChar (如果值為 null)，否則為 OleDbType.Variant。|OdbcType.NVarChar|不支援|

> [!NOTE]
> 將十進位值轉換為其他型別的過程稱為窄化轉換，此類轉換會將十進位值向零的方向取整數。 如果目的型別無法代表此項轉換的結果，則會擲回 <xref:System.OverflowException> 。

> [!NOTE]
> 當您將 null 參數值傳送至伺服器時，您必須指定<xref:System.DBNull>，而非`null`(`Nothing` Visual Basic 中)。 系統中的 Null 值是沒有值的空物件。 <xref:System.DBNull> 用於表示 null 值。 如需資料庫 null 值的詳細資訊，請參閱 [Handling Null Values](./sql/handling-null-values.md)。

## <a name="deriving-parameter-information"></a>衍生參數資訊

您也可以使用 `DbCommandBuilder` 類別 (Class) 從預存程序衍生參數。 `SqlCommandBuilder` 和 `OleDbCommandBuilder` 類別都能提供靜態方法 ( `DeriveParameters`)，該方法會在使用預存程序之參數資訊的命令物件，自動填入參數集合。 請注意， `DeriveParameters` 將會覆寫命令所有的現有參數資訊。

> [!NOTE]
> 衍生參數資訊會造成效能降低，因為這項作業需要對資料來源進行額外的來回行程才能擷取資訊。 若在設計階段已知參數資訊，您便可以明確設定參數，改善應用程式的效能。

如需詳細資訊，請參閱 < [Commandbuilder 產生命令](generating-commands-with-commandbuilders.md)。

## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>使用參數配合 SqlCommand 和預存程序

預存程序對資料驅動應用程式有許多好處。 藉由使用預存程序，資料庫作業可以封裝在單一命令中、最佳化為最佳效能，並且可進一步提升安全性。 雖然可以呼叫預存程序，預存程序名稱後, 接參數引數當成 SQL 陳述式，藉由傳遞<xref:System.Data.Common.DbCommand.Parameters%2A>的集合[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]<xref:System.Data.Common.DbCommand>物件可讓您更明確地定義預存程序參數，來存取輸出參數和傳回值。

> [!NOTE]
> 參數化陳述式能在伺服器上執行，都是透過允許查詢計畫重複使用的 `sp_executesql,` 。 呼叫 `sp_executesql` 的批次無法見到 `sp_executesql`批次中的本機資料指標或變數。 資料庫內容中的變更只會持續到 `sp_executesql` 陳述式結束。 如需詳細資訊，請參閱 [sp_executesql (transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql)。

將參數與 <xref:System.Data.SqlClient.SqlCommand> 搭配使用以執行 SQL Server 預存程序時，加入 <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> 集合的參數名稱必須與預存程序中的參數標記名稱相符。 .NET Framework Data Provider for SQL Server 不支援問號 （？） 預留位置將參數傳遞至 SQL 陳述式或預存程序。 它會將預存程式中的參數視為具名參數，並搜尋相符的參數標記。 例如， `CustOrderHist` 預存程序是使用名為 `@CustomerID`的參數所定義的。 則當您的程式碼執行預存程序時，也必須使用名為 `@CustomerID`的參數。

```sql
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)
```

### <a name="example"></a>範例

此範例會示範如何在 `Northwind` 範例資料庫中呼叫 SQL Server 預存程序。 預存程序的名稱為 `dbo.SalesByCategory` ，而且具有名為 `@CategoryName` 的輸入參數 (資料型別為 `nvarchar(15)`)。 此程式碼會在 Using 區塊中建立新的 <xref:System.Data.SqlClient.SqlConnection> ，這樣當程序結束時就會清除連接。 <xref:System.Data.SqlClient.SqlCommand> 和 <xref:System.Data.SqlClient.SqlParameter> 物件會建立，其屬性也會設定。 <xref:System.Data.SqlClient.SqlDataReader> 會執行 `SqlCommand` 並從預存程序傳回結果集，在主控台視窗中顯示輸出。

> [!NOTE]
> 與其建立 `SqlCommand` 和 `SqlParameter` 物件，然後再以個別的陳述式設定屬性，您可以選擇使用其中一個多載建構函式 (Constructor)，以單一的陳述式設定多個屬性。

[!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]

## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>使用參數配合 OleDbCommand 或 OdbcCommand

將參數與 <xref:System.Data.OleDb.OleDbCommand> 或 <xref:System.Data.Odbc.OdbcCommand>搭配使用時，加入至 `Parameters` 集合的參數順序必須與預存程序中所定義的參數順序相符。 .NET Framework Data Provider for OLE DB 和 ODBC 的.NET Framework 資料提供者在預存程序的參數視為預留位置，並套用順序的參數值。 此外，傳回值參數必須是第一個加入至 `Parameters` 集合的參數。

.NET Framework Data Provider for OLE DB 和 ODBC 的.NET Framework 資料提供者不支援具名的參數來傳遞參數至 SQL 陳述式或預存程序。 這種情況下，您必須使用問號 (?) 預留位置，如下列範例所示。

```sql
SELECT * FROM Customers WHERE CustomerID = ?
```

所以， `Parameter` 物件加入至 `Parameters` 集合的順序，必須直接對應至參數的 ? 預留位置。

### <a name="oledb-example"></a>OleDb 範例

```vb
Dim command As OleDbCommand = New OleDbCommand( _
  "SampleProc", connection)
command.CommandType = CommandType.StoredProcedure

Dim parameter As OleDbParameter = command.Parameters.Add( _
  "RETURN_VALUE", OleDbType.Integer)
parameter.Direction = ParameterDirection.ReturnValue

parameter = command.Parameters.Add( _
  "@InputParm", OleDbType.VarChar, 12)
parameter.Value = "Sample Value"

parameter = command.Parameters.Add( _
  "@OutputParm", OleDbType.VarChar, 28)
parameter.Direction = ParameterDirection.Output
```

```csharp
OleDbCommand command = new OleDbCommand("SampleProc", connection);
command.CommandType = CommandType.StoredProcedure;

OleDbParameter parameter = command.Parameters.Add(
  "RETURN_VALUE", OleDbType.Integer);
parameter.Direction = ParameterDirection.ReturnValue;

parameter = command.Parameters.Add(
  "@InputParm", OleDbType.VarChar, 12);
parameter.Value = "Sample Value";

parameter = command.Parameters.Add(
  "@OutputParm", OleDbType.VarChar, 28);
parameter.Direction = ParameterDirection.Output;
```

## <a name="odbc-example"></a>Odbc 範例

```vb
Dim command As OdbcCommand = New OdbcCommand( _
  "{ ? = CALL SampleProc(?, ?) }", connection)
command.CommandType = CommandType.StoredProcedure

Dim parameter As OdbcParameter = command.Parameters.Add("RETURN_VALUE", OdbcType.Int)
parameter.Direction = ParameterDirection.ReturnValue

parameter = command.Parameters.Add( _
  "@InputParm", OdbcType.VarChar, 12)
parameter.Value = "Sample Value"

parameter = command.Parameters.Add( _
  "@OutputParm", OdbcType.VarChar, 28)
parameter.Direction = ParameterDirection.Output
```

```csharp
OdbcCommand command = new OdbcCommand( _
  "{ ? = CALL SampleProc(?, ?) }", connection);
command.CommandType = CommandType.StoredProcedure;

OdbcParameter parameter = command.Parameters.Add( _
  "RETURN_VALUE", OdbcType.Int);
parameter.Direction = ParameterDirection.ReturnValue;

parameter = command.Parameters.Add( _
  "@InputParm", OdbcType.VarChar, 12);
parameter.Value = "Sample Value";

parameter = command.Parameters.Add( _
  "@OutputParm", OdbcType.VarChar, 28);
parameter.Direction = ParameterDirection.Output;
```

## <a name="see-also"></a>另請參閱

- [命令和參數](commands-and-parameters.md)
- [DataAdapter 參數](dataadapter-parameters.md)
- [ADO.NET 中的資料類型對應](data-type-mappings-in-ado-net.md)
- [ADO.NET 概觀](ado-net-overview.md)
