---
title: 修改大數值（max）資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 7ed036f5ad3a1c042ee277ecd2145f72746ef420
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451833"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>在 ADO.NET 中修改大量數值 (max) 資料
大型物件 (LOB) 資料類型是指資料列大小上限超過 8 KB 的資料類型。 SQL Server 提供 `max`、`varchar` 和 `nvarchar` 資料類型的 `varbinary` 規範，允許儲存最大達 2^32 位元組的值。 資料表資料行及 Transact-SQL 變數可指定 `varchar(max)`、`nvarchar(max)` 或 `varbinary(max)` 資料型別。 在 ADO.NET 中，`max` 資料型別可透過 `DataReader` 來擷取，也可指定為輸入及輸出參數值，並且不需要任何特殊處理。 對於大型 `varchar` 資料型別，可透過遞增方式擷取及更新資料。  
  
 `max` 資料類型可用於比較 (作為 Transact-SQL 變數) 及串連。 它們也可用於 SELECT 陳述式的 DISTINCT、ORDER BY、GROUP BY 子句，以及彙總、聯結 (Join) 及子查詢中。  
  
 下表將提供《SQL Server 線上叢書》中相關文件的連結。  
  
 **SQL Server 文件**  
  
1. [使用大數值資料類型](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))  
  
## <a name="large-value-type-restrictions"></a>大數值型別限制  
 下列限制適用於 `max` 資料型別，而小型資料型別則沒有這些限制：  
  
- `sql_variant` 不可包含大型 `varchar` 資料型別。  
  
- 大型 `varchar` 資料行不可指定為索引中的索引鍵資料行。 而在非叢集索引的內含資料行中，則允許有大型資料行。  
  
- 大型 `varchar` 資料行不可用做分割索引鍵資料行。  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>在 Transact-SQL 中使用大數值型別  
 Transact-SQL `OPENROWSET` 函式是連接及存取遠端資料的一次性方法。 其包括從 OLE DB 資料來源存取遠端資料時所需的所有連接資訊。 您可以依照資料表名稱的相同方式，在查詢的 FROM 子句中參考 `OPENROWSET`。 此外，它也可參考為 INSERT、UPDATE 或 DELETE 陳述式的目標資料表，但會受到 OLE DB 提供者的功能影響。  
  
 `OPENROWSET` 函式包含 `BULK` 資料列集提供者，可讓您直接從檔案讀取資料，不需將資料載入目標資料表中。 這可讓您在簡單的 INSERT SELECT 陳述式中使用 `OPENROWSET`。  
  
 `OPENROWSET BULK` 選項引數可有效地控制何處開始及結束讀取資料、如何處理錯誤，以及如何解譯資料。 例如，您可以指定讓資料檔案當作 `varbinary`、`varchar` 或 `nvarchar` 類型的單一資料列、單一資料行資料列集加以讀取。 如需完整的語法及選項，請參閱《SQL Server 線上叢書》。  
  
 下列範例會將相片插入 AdventureWorks 範例資料庫中的 ProductPhoto 資料表。 使用 `BULK OPENROWSET` 提供者時，即使未將值插入每個資料行，也必須提供資料行的具名清單。 在此情況下，將主索引鍵定義為識別欄位，也可從資料行清單省略。 請注意，您還必須提供關聯名稱，將其置於 `OPENROWSET` 陳述式的結尾處 (此情況中為 ThumbnailPhoto)。 這會與要載入檔案之 `ProductPhoto` 資料表中的資料行關聯。  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>使用 UPDATE .WRITE 更新資料  
 Transact-SQL UPDATE 陳述式具有新的 WRITE 語法，它可用來修改 `varchar(max)`、`nvarchar(max)` 或 `varbinary(max)` 資料行的內容。 這允許您對資料進行部分更新。 下面所示為簡略形式的 UPDATE .WRITE 語法：  
  
 UPDATE  
  
 { *\<object>* }  
  
 SET  
  
 { *column_name* = {。WRITE （ *expression* ，@Offset，@Length）}  
  
 WRITE 方法指定將對 *column_name* 值的某個區段進行修改。 其中，expression 是要複製到 *column_name* 的值；`@Offset` 是要寫入運算式的起點；`@Length` 引數是資料行中區段的長度。  
  
|If|結果為|  
|--------|----------|  
|運算式設為 NULL|系統會忽略 `@Length`，並會將 *column_name* 中的值在指定的 `@Offset` 處截斷。|  
|`@Offset` 是 NULL|更新作業會在現有 *column_name* 值的結尾處附加運算式，並且會忽略 `@Length`。|  
|`@Offset` 大於 column_name 值的長度|SQL Server 會傳回錯誤。|  
|`@Length` 是 NULL|更新作業會移除從 `@Offset` 到 `column_name` 值結尾的所有資料。|  
  
> [!NOTE]
> `@Offset` 及 `@Length` 都不可為負數。  
  
## <a name="example"></a>範例  
 此 Transact-SQL 範例會更新 DocumentSummary 中的部分值，其為 AdventureWorks 資料庫中 Document 資料表內的 `nvarchar(max)` 資料行。 'components' 一字藉由指定取代文字、現有資料中要取代之文字的起始位置 (位移)，以及要取代的字元數 (長度) 來取代為 'features' 一字。 該範例會將 SELECT 陳述式併入到 UPDATE 陳述式之前與之後來比較結果。  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>在 ADO.NET 中使用大數值型別  
 您可以在 ADO.NET 中使用大數值類型，方法是將大數值類型指定為 <xref:System.Data.SqlClient.SqlParameter> 中的 <xref:System.Data.SqlClient.SqlDataReader> 物件以傳回結果集，或使用 <xref:System.Data.SqlClient.SqlDataAdapter> 來填滿 `DataSet`/`DataTable`。 大型值型別與其相關的小型值資料型別在使用方式上並無差異。  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>使用 GetSqlBytes 擷取資料  
 `GetSqlBytes` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可用於擷取 `varbinary(max)` 資料行的內容。 下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlCommand> 的 `cmd` 物件會從資料表選取 `varbinary(max)` 資料；名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會以 <xref:System.Data.SqlTypes.SqlBytes> 形式擷取資料。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>使用 GetSqlChars 擷取資料  
 `GetSqlChars` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可用於擷取 `varchar(max)` 或 `nvarchar(max)` 資料行的內容。 下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlCommand> 的 `cmd` 物件會從資料表選取 `nvarchar(max)` 資料；名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會擷取資料。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>使用 GetSqlBinary 擷取資料  
 `GetSqlBinary` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可用於擷取 `varbinary(max)` 資料行的內容。 下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlCommand> 的 `cmd` 物件會從資料表選取 `varbinary(max)` 資料；名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會以 <xref:System.Data.SqlTypes.SqlBinary> 資料流形式擷取資料。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>使用 GetBytes 擷取資料  
 `GetBytes` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可將位元組資料流，從指定的資料行位移讀取到在指定陣列位移處開始的位元組陣列。 下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會將位元組擷取到位元組陣列。 請注意，`GetSqlBytes` 與 `GetBytes` 不同，其需要一定大小的陣列緩衝區。  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>使用 GetValue 擷取資料  
 `GetValue` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可將值從指定的資料行位移讀取到陣列中。 下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會從第一個資料行位移擷取二進位資料，然後從第二個資料行位移擷取字串資料。  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>從大型值型別轉換為 CLR 型別  
 您可以使用任何字串轉換方法 (如 `varchar(max)`)，來轉換 `nvarchar(max)` 或 `ToString` 資料行的內容。 下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會擷取資料。  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>範例  
 下列程式碼會從 `LargePhoto` 資料庫中的 `ProductPhoto` 資料表擷取名稱及 `AdventureWorks` 物件，並將其儲存至檔案。 組件 (Assembly) 需要參考 <xref:System.Drawing> 命名空間 (Namespace) 才能進行編譯。  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> 的 <xref:System.Data.SqlClient.SqlDataReader> 方法會傳回 <xref:System.Data.SqlTypes.SqlBytes> 物件，其會公開 `Stream` 屬性。 該程式碼會使用此物件來建立新的 `Bitmap` 物件，然後將其儲存為 Gif `ImageFormat`。  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>使用大型值型別參數  
 大型值型別可用於 <xref:System.Data.SqlClient.SqlParameter> 物件，其使用方式與在 <xref:System.Data.SqlClient.SqlParameter> 物件中使用小型值型別相同。 您可以將大數值類型擷取為 <xref:System.Data.SqlClient.SqlParameter> 值，如下列範例所示。 該程式碼假設下列 GetDocumentSummary 預存程序存在於 AdventureWorks 範例資料庫中。 預存程序會接受名為 @DocumentID 的輸入參數，並在 @DocumentSummary 輸出參數中傳回 DocumentSummary 資料行的內容。  
  
```sql
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>範例  
 ADO.NET 程式碼會建立 <xref:System.Data.SqlClient.SqlConnection> 及 <xref:System.Data.SqlClient.SqlCommand> 物件來執行 GetDocumentSummary 預存程序並擷取文件摘要 (以大型值型別儲存)。 該程式碼會傳遞 @DocumentID 輸入參數的值，並會在 [主控台] 視窗中顯示 @DocumentSummary 輸出參數中傳回的結果。  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 二進位和大量數值資料](sql-server-binary-and-large-value-data.md)
- [SQL Server 資料類型對應](../sql-server-data-type-mappings.md)
- [ADO.NET 中的 SQL Server 資料作業](sql-server-data-operations.md)
- [ADO.NET 概觀](../ado-net-overview.md)
