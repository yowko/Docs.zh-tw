---
title: 在 ADO.NET 中修改大量數值 (max) 資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 285803d92474efd3268816d1af06eb3ff4abbc79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365588"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>在 ADO.NET 中修改大量數值 (max) 資料
大型物件 (LOB) 資料型別是指資料列大小上限超過 8 KB 的資料型別。 SQL Server 可提供 `max`、`varchar` 和 `nvarchar` 資料型別的 `varbinary` 規範，允許儲存最大達 2^32 位元組的值。 資料表資料行及 Transact-SQL 變數可指定 `varchar(max)`、`nvarchar(max)` 或 `varbinary(max)` 資料型別。 在 ADO.NET 中，`max` 資料型別可透過 `DataReader` 來擷取，也可指定為輸入及輸出參數值，並且不需要任何特殊處理。 對於大型 `varchar` 資料型別，可透過遞增方式擷取及更新資料。  
  
 `max` 資料型別可用於比較 (做為 Transact-SQL 變數) 及串連。 它們也可用於 SELECT 陳述式的 DISTINCT、ORDER BY、GROUP BY 子句，以及彙總、聯結 (Join) 及子查詢中。  
  
 下表將提供《SQL Server 線上叢書》中相關文件的連結。  
  
 **SQL Server 線上叢書**  
  
1.  [使用大數值資料類型](http://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>大數值型別限制  
 下列限制適用於 `max` 資料型別，而小型資料型別則沒有這些限制：  
  
-   `sql_variant` 不可包含大型 `varchar` 資料型別。  
  
-   大型 `varchar` 資料行不可指定為索引中的索引鍵資料行。 而在非叢集索引的內含資料行中，則允許有大型資料行。  
  
-   大型 `varchar` 資料行不可用做分割索引鍵資料行。  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>在 Transact-SQL 中使用大數值型別  
 Transact-SQL `OPENROWSET` 函式是連接及存取遠端資料的一次性方法。 其包括從 OLE DB 資料來源存取遠端資料時所需的所有連接資訊。 您可以在查詢的 FROM 子句中，將 `OPENROWSET` 當做資料表名稱般地加以參考。 此外，它也可參考為 INSERT、UPDATE 或 DELETE 陳述式的目標資料表，但會受到 OLE DB 提供者的功能影響。  
  
 `OPENROWSET` 函式包含 `BULK` 資料列集提供者，可讓您直接從檔案讀取資料，不需將資料載入目標資料表中。 這可讓您在簡單的 INSERT SELECT 陳述式中使用 `OPENROWSET`。  
  
 `OPENROWSET``BULK`選項引數可有效地控制何處開始及結束讀取資料、 如何處理錯誤，以及如何解譯資料。 例如，您可以指定將資料檔案讀取為具有型別 `varbinary`、`varchar` 或 `nvarchar` 的單一資料列及單一資料行資料列集。 如需完整的語法及選項，請參閱《SQL Server 線上叢書》。  
  
 下列範例會將相片插入 AdventureWorks 範例資料庫中的 ProductPhoto 資料表。 當使用`BULK``OPENROWSET`提供者，您必須提供偶數的資料行的具名的清單，如果您未將值插入每個資料行。 在此情況下，將主索引鍵定義為識別欄位，也可從資料行清單省略。 請注意，您還必須提供關聯名稱，將其置於 `OPENROWSET` 陳述式的結尾處 (此情況中為 ThumbnailPhoto)。 這會與要載入檔案之 `ProductPhoto` 資料表中的資料行關聯。  
  
```  
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
  
 { *\<物件 >* }  
  
 SET  
  
 { *column_name* = {。寫入 (*運算式*， @Offset ， @Length )}  
  
 WRITE 方法指定值的區段*column_name*將予修改。 運算式是將複製到的值*column_name*、`@Offset`是起始點速率將寫入運算式，而`@Length`引數是資料行中區段的長度。  
  
|如果|然後|  
|--------|----------|  
|運算式設為 NULL|`@Length` 會忽略中的值和*column_name*會截斷在指定`@Offset`。|  
|`@Offset` 為 NULL|更新作業處附加運算式結尾現有*column_name*值和`@Length`會被忽略。|  
|`@Offset` 大於 column_name 值的長度|SQL Server 會傳回錯誤。|  
|`@Length` 為 NULL|更新作業會移除從 `@Offset` 到 `column_name` 值結尾的所有資料。|  
  
> [!NOTE]
>  `@Offset` 及 `@Length` 都不可為負數。  
  
## <a name="example"></a>範例  
 此 Transact-SQL 範例會更新 DocumentSummary 中的部分值，其為 AdventureWorks 資料庫中 Document 資料表內的 `nvarchar(max)` 資料行。 藉由指定取代單字、現有資料中要取代之單字的開始位置 (位移)，以及要取代的字元數 (長度)，將 components 這個字取代為 features 這個字。 該範例會將 SELECT 陳述式併入到 UPDATE 陳述式之前與之後來比較結果。  
  
```  
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
 您可以使用大數值類型在 ADO.NET 中藉由指定做為大數值類型<xref:System.Data.SqlClient.SqlParameter>中的物件<xref:System.Data.SqlClient.SqlDataReader>傳回結果集，或使用<xref:System.Data.SqlClient.SqlDataAdapter>填滿`DataSet` / `DataTable`。 大型值型別與其相關的小型值資料型別在使用方式上並無差異。  
  
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
 下列程式碼會從 `LargePhoto` 資料庫中的 `ProductPhoto` 資料表擷取名稱及 `AdventureWorks` 物件，並將其儲存至檔案。 組件 (Assembly) 需要參考 <xref:System.Drawing> 命名空間 (Namespace) 才能進行編譯。  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> 的 <xref:System.Data.SqlClient.SqlDataReader> 方法會傳回 <xref:System.Data.SqlTypes.SqlBytes> 物件，其會公開 `Stream` 屬性。 程式碼會使用此建立新`Bitmap`物件，然後再將它儲存在 Gif `ImageFormat`。  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>使用大型值型別參數  
 大型值型別可用於 <xref:System.Data.SqlClient.SqlParameter> 物件，其使用方式與在 <xref:System.Data.SqlClient.SqlParameter> 物件中使用小型值型別相同。 您可以擷取大數值類型為<xref:System.Data.SqlClient.SqlParameter>值，如下列範例所示。 該程式碼假設下列 GetDocumentSummary 預存程序存在於 AdventureWorks 範例資料庫中。 預存程序會採用名為輸入的參數@DocumentID並傳回 DocumentSummary 資料行中的內容@DocumentSummary輸出參數。  
  
```  
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
 ADO.NET 程式碼會建立 <xref:System.Data.SqlClient.SqlConnection> 及 <xref:System.Data.SqlClient.SqlCommand> 物件來執行 GetDocumentSummary 預存程序並擷取文件摘要 (以大型值型別儲存)。 程式碼會將值傳遞@DocumentID輸入參數，並顯示結果傳遞回@DocumentSummary輸出在主控台視窗中的參數。  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 二進位和大量數值資料](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [SQL Server 資料類型對應](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [ADO.NET 中的 SQL Server 資料作業](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
