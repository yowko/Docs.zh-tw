---
title: 日期和時間資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 80b7df4922e1398c7290e769e53627a1d46ebc83
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344167"
---
# <a name="date-and-time-data"></a>日期和時間資料
SQL Server 2008 導入了處理日期和時間資訊的新資料型別。 這些新資料型別包括日期和時間的個別型別，以及具有較大範圍、精確度和時區感知的擴充資料型別。 從 .NET Framework 3.5 版 Service Pack (SP) 1 開始，.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 就會針對 SQL Server 2008 Database Engine 的所有新功能提供完整支援。 您必須安裝 .NET Framework 3.5 SP1 (或更新版本) 才能使用這些新功能搭配 SqlClient。  
  
 SQL Server 2008 之前的 SQL Server 版本只有兩種可使用日期及時間值的資料型別：`datetime` 和 `smalldatetime`。 這兩種資料型別都同時包含日期值和時間值，所以很難只使用日期或是時間值。 此外，這些資料型別只支援發生在 1753 年英國西曆引進之後的日期。 另一項限制是這些較舊的資料型別並不具有時區感知的功能，所以不能使用源自多個時區的資料。  
  
 您可以在《SQL Server 線上叢書》中取得 SQL Server 資料型別的完整文件。 下表將列出日期和時間資料的版本特有入門級主題。  
  
 **SQL Server 線上叢書**  
  
1. [使用日期和時間資料](https://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>SQL Server 2008 所導入的日期/時間資料型別  
 下表將描述新的日期和時間資料型別。  
  
|SQL Server 資料型別|描述|  
|--------------------------|-----------------|  
|`date`|`date` 資料型別的範圍從 01 年 1 月 1 日到 9999 年 12 月 31 日，精確度為 1 日。 預設值為 1900 年 1 月 1 日。 儲存大小是 3 個位元組。|  
|`time`|`time` 資料型別只會根據 24 小時制來儲存時間值。 `time` 資料型別的範圍從 00:00:00.0000000 到 23:59:59.9999999，精確度為 100 奈秒。 預設值是 00:00:00.0000000 (午夜)。 `time` 資料型別支援使用者定義的小數點後第二位的精確度，儲存大小則從 3 到 6 位元組不等，依指定的精確度而定。|  
|`datetime2`|`datetime2` 資料型別將 `date` 和 `time` 資料型別的範圍及精確度組合成單一的資料型別。<br /><br /> 預設值及字串常值格式與 `date` 和 `time` 資料型別中定義的相同。|  
|`datetimeoffset`|`datetimeoffset` 資料型別具有 `datetime2` 的所有功能，且具有額外的時區位移 (Offset)。 時區位移以 [+&#124;-] hh: mm。 HH 是代表時區位移中時數的 2 位數，範圍介於 00 至 14 之間。 MM 是代表時區位移中額外分鐘數的 2 位數，範圍介於 00 至 59 之間。 時間格式可支援到 100 奈秒。 強制的 + 或 - 號則代表在取得當地時間時，是在 UTC (世界標準時間或格林威治標準時間) 中加入或減去時區位移數。|  
  
> [!NOTE]
>  如需使用 `Type System Version` 關鍵字的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。  
  
## <a name="date-format-and-date-order"></a>日期格式和日期順序  
 SQL Server 剖析日期和時間值的方式不僅取決於型別系統版本和伺服器版本，而且也取決於伺服器的預設語言和格式設定。 如果透過連接執行查詢，而連接是使用不同的語言與日期格式設定，那麼原先在另一種語言中日期格式有效的日期字串可能會變成無法辨識。  
  
 Transact-SQL SET LANGUAGE 陳述式 (Statement) 會隱含地設定可決定日期部分順序的 DATEFORMAT。 您可以在連接時使用 SET DATEFORMAT Transact-SQL 陳述式，按照 MDY、DMY、YMD、YDM、MYD 或 DYM 順序排序日期部分，藉以讓日期值意義明確。  
  
 如果您沒有針對連接指定任何 DATEFORMAT，SQL Server 就會使用與連接相關聯的預設語言。 例如，日期字串 '01/02/03' 在語言設定為美式英文的伺服器上會解譯成 MDY (2003 年 1 月 2 日)，而在語言設定為英式英文的伺服器上則會解譯成 DMY (2003 年 2 月 1 日)。 年份是使用 SQL Server 的截止年份規則決定的，而且此規則會定義指派世紀值的截止日期。 如需詳細資訊，請參閱 < [two digit year cutoff 選項](https://go.microsoft.com/fwlink/?LinkId=120473)SQL Server 線上叢書 》 中。  
  
> [!NOTE]
>  從字串格式轉換成 `date`、`time`、`datetime2` 或 `datetimeoffset` 時，不支援 YDM 日期格式。  
  
 如需有關 SQL Server 如何解譯日期和時間資料的詳細資訊，請參閱 <<c0> [ 使用的日期和時間資料](https://go.microsoft.com/fwlink/?LinkID=98361)SQL Server 2008 線上叢書 》 中。  
  
## <a name="datetime-data-types-and-parameters"></a>日期/時間資料型別和參數  
 <xref:System.Data.SqlDbType> 中已加入下列的列舉型別以支援新的日期及時間資料型別。  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  

您可以指定的資料型別<xref:System.Data.SqlClient.SqlParameter>使用其中一種上述<xref:System.Data.SqlDbType>列舉型別。 

> [!NOTE]
> 您無法設定`DbType`的屬性`SqlParameter`至`SqlDbType.Date`。

 您也可以藉由將 <xref:System.Data.SqlClient.SqlParameter> 物件的 <xref:System.Data.SqlClient.SqlParameter.DbType%2A> 屬性設定為特定的 `SqlParameter` 列舉值，以一般的方式指定 <xref:System.Data.DbType> 的型別。 <xref:System.Data.DbType> 中已加入下列的列舉值以支援 `datetime2` 和 `datetimeoffset` 資料型別：  
  
-   DbType.DateTime2  
  
-   DbType.DateTimeOffset  
  
 這些新的列舉型別補充了存在舊版 .NET Framework 中的 `Date`、`Time` 和 `DateTime` 列舉型別。  
  
 您可以從參數物件之值的 .NET Framework 型別，或從參數物件的 `DbType` 推斷出參數物件的 .NET Framework 資料提供者型別。 尚未引進任何新增的 <xref:System.Data.SqlTypes> 來支援新的日期及時間資料型別。 下表說明 SQL Server 2008 日期和時間資料型別以及 CLR 資料型別之間的對應。  
  
|SQL Server 資料型別|.NET Framework 類型|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|System.DateTime|Date|Date|  
|時間|System.TimeSpan|時間|時間|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter 屬性  
 下表將說明與日期和時間資料型別相關的 `SqlParameter` 屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|取得或設定值是否可為 Null。 將 Null 參數值傳送至伺服器時，必須指定 <xref:System.DBNull>，而不是 `null` (在 Visual Basic 中為 `Nothing`)。 如需資料庫 null 值的詳細資訊，請參閱 [Handling Null Values](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)。|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|取得或設定用於表示此值的最大位數。 若為日期和時間資料型別，則會忽略這項設定。|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|取得或設定的值時間部分是解析的小數點位數`Time`， `DateTime2`，和`DateTimeOffset`。 預設值為 0，表示從此值推斷實際的小數點位數並傳送至伺服器。|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|若為日期和時間資料型別，則會忽略。|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|取得或設定參數值。|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|取得或設定參數值。|  
  
> [!NOTE]
>  小於零或是大於或等於 24 小時的時間值將會擲回 <xref:System.ArgumentException>。  
  
### <a name="creating-parameters"></a>建立參數  
 您可以建立<xref:System.Data.SqlClient.SqlParameter>物件使用其建構函式，或將它加入至<xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A>藉由呼叫集合`Add`方法<xref:System.Data.SqlClient.SqlParameterCollection>。 `Add` 方法會將建構函式引數或現有的參數物件當做輸入。  
  
 本主題的下列章節會提供如何指定 date 和 time 參數的範例。 如需使用參數的其他範例，請參閱[設定參數和參數資料類型](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)並[DataAdapter 的參數](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)。  
  
### <a name="date-example"></a>Date 範例  
 下列程式碼片段將示範如何指定 `date` 參數。  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a>Time 範例  
 下列程式碼片段將示範如何指定 `time` 參數。  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Datetime2 範例  
 下列程式碼片段將示範如何指定同時含有日期和時間部分的 `datetime2` 參數。  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>DateTimeOffSet 範例  
 下列程式碼片段將示範如何指定含有日期、時間和時區位移 0 的 `DateTimeOffSet` 參數。  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
 您也可以使用 `AddWithValue` 的 <xref:System.Data.SqlClient.SqlCommand> 方法來提供參數，如下列程式碼片段所示。 不過，`AddWithValue` 方法不允許您指定參數的 <xref:System.Data.SqlClient.SqlParameter.DbType%2A> 或 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A>。  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date`參數可對應至`date`， `datetime`，或`datetime2`伺服器上的資料類型。 使用新的 `datetime` 資料型別時，您必須明確將此參數的 <xref:System.Data.SqlDbType> 屬性設定為執行個體 (Instance) 的資料型別。 使用 <xref:System.Data.SqlDbType.Variant> 或隱含地提供參數值可能會導致與 `datetime` 和 `smalldatetime` 資料型別的回溯相容性 (Backward Compatibility) 問題。  
  
 下表將顯示從哪些 CLR 型別推斷哪些 `SqlDbTypes`：  
  
|CLR 類型|推斷的 SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>擷取日期和時間資料  
 下表說明用於擷取 SQL Server 2008 日期和時間值的方法。  
  
|SqlClient 方法|描述|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|擷取指定的資料行值做為 <xref:System.DateTime> 結構。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|擷取指定的資料行值做為 <xref:System.DateTimeOffset> 結構。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|傳回的型別是欄位基礎提供者特定的型別。 針對新的日期和時間型別，傳回與 `GetFieldType` 相同的型別。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|擷取指定資料行的值。 針對新的日期和時間型別，傳回與 `GetValue` 相同的型別。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|擷取指定陣列中的值。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|以 <xref:System.Data.SqlTypes.SqlString> 擷取資料行值。 如果資料無法以 <xref:System.InvalidCastException> 表示，就會發生 `SqlString`。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|擷取資料行的資料，做為其預設 `SqlDbType`。 針對新的日期和時間型別，傳回與 `GetValue` 相同的型別。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|擷取指定陣列中的值。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|如果 Type System Version 是設為 SQL Server 2005，則擷取資料行的值做為字串。 如果資料無法以字串表示，就會發生 <xref:System.InvalidCastException>。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|擷取指定的資料行值做為 <xref:System.TimeSpan> 結構。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|擷取指定資料行的值做為其基礎的 CLR 型別。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|擷取陣列中的資料行值。|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|傳回說明結果集中繼資料的 <xref:System.Data.DataTable>。|  
  
> [!NOTE]
>  新的日期和時間 `SqlDbTypes` 不支援 SQL Server 中同處理序 (In-Process) 執行的程式碼。 如果其中一個型別傳遞至伺服器，就會引發例外狀況 (Exception)。  
  
## <a name="specifying-date-and-time-values-as-literals"></a>將日期和時間值指定為常值  
 您可以使用各種不同的常值字串格式來指定日期和時間資料型別，然後 SQL Server 就會在執行階段評估這些格式，並將它們轉換成內部日期/時間結構。 SQL Server 可辨識以單引號 (') 括住的日期和時間資料。 下列範例將示範一些格式：  
  
-   字母日期格式，例如 `'October 15, 2006'`。  
  
-   數字日期格式，例如 `'10/15/2006'`。  
  
-   未分隔的字串格式，例如 `'20061015'`。如果您正在使用 ISO 標準日期格式，它就會解譯成 2006 年 10 月 15 日。  
  
> [!NOTE]
>  您可以在《SQL Server 線上叢書》中找到所有常值字串格式以及日期和時間資料型別之其他功能的完整文件。  
  
 小於零或是大於或等於 24 小時的時間值將會擲回 <xref:System.ArgumentException>。  
  
## <a name="resources-in-sql-server-2008-books-online"></a>SQL Server 2008 線上叢書中的資源  
 如需在 SQL Server 2008 中使用日期和時間值的詳細資訊，請參閱《SQL Server 2008 線上叢書》中的下列資源。  
  
|主題|描述|  
|-----------|-----------------|  
|[日期和時間資料類型與函數 (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|提供所有 Transact-SQL 日期及時間資料型別與函式的概觀。|  
|[使用日期和時間資料](https://go.microsoft.com/fwlink/?LinkId=98361)|提供有關日期和時間資料型別與函式的詳細資訊，以及使用這些項目的範例。|  
|[資料類型 (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|說明 SQL Server 2008 中的系統資料型別。|  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型對應](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [設定參數和參數資料類型](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [SQL Server 資料類型和 ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
