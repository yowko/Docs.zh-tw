---
title: 大型 UDT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: f55f6eccf3566a2391204e1ca4349ae5dff01954
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148552"
---
# <a name="large-udts"></a>大型 UDT
使用者定義類型 (UDT) 可讓開發人員將 Common Language Runtime (CLR) 物件儲存在 SQL Server 資料庫中來擴充伺服器的純量類型系統。 UDT 可包含多個項目並可具有不同的行為，與只含單一 SQL Server 系統資料類型的傳統別名資料類型有所不同。  
  
> [!NOTE]
> 您必須安裝 .NET Framework 3.5 SP1 (或更新版本) 才能運用大型 UDT 的強化 SqlClient 支援。  
  
 在過去，UDT 的大小上限為 8 KB。 在 SQL Server 2008 中，目前使用 <xref:Microsoft.SqlServer.Server.Format.UserDefined> 格式的 UDT 已不再具有這項限制。  
  
 如需使用者定義型別的完整文件，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 文件集**  
  
1. [CLR 使用者定義類型](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>使用 GetSchema 來擷取 UDT 結構描述  
 <xref:System.Data.SqlClient.SqlConnection> 的 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> 方法會傳回 <xref:System.Data.DataTable> 中的資料庫結構描述資訊。 有關詳細資訊，請參閱[SQL Server 架構集合](../sql-server-schema-collections.md)。  
  
### <a name="getschematable-column-values-for-udts"></a>UDT 的 GetSchemaTable 資料行值  
 <xref:System.Data.SqlClient.SqlDataReader> 的 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> 方法會傳回描述資料行中繼資料的 <xref:System.Data.DataTable>。 下表描述 SQL Server 2005 與 SQL Server 2008 之間大型 UDT 之資料行中繼資料中的差異。  
  
|SqlDataReader 資料行|SQL Server 2005|SQL Server 2008 及更新版本|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|不定|不定|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|UDT 執行個體|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|UDT 執行個體|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|指定為 *Database.SchemaName.TypeName* 的三部分名稱。|  
|`IsLong`|不定|不定|  
  
## <a name="sqldatareader-considerations"></a>SqlDataReader 考量  
 從 SQL Server 2008 開始，<xref:System.Data.SqlClient.SqlDataReader> 已擴充，可支援大型 UDT 值的擷取。 <xref:System.Data.SqlClient.SqlDataReader> 處理大型 UDT 值的方式，取決於您所使用的 SQL Server 版本，以及連接字串中指定的 `Type System Version`。 如需詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。  
  
 當 `Type System Version` 設定為 SQL Server 2005 時，下列 <xref:System.Data.SqlClient.SqlDataReader> 的方法將會傳回 <xref:System.Data.SqlTypes.SqlBinary>，而不是 UDT：  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 當 `Type System Version` 設定為 SQL Server 2005 時，下列方法將會傳回 `Byte[]` (而非 UDT) 的陣列：  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 請注意，不會針對目前的 ADO.NET 版本進行任何轉換。  
  
## <a name="specifying-sqlparameters"></a>指定 SqlParameters  
 下列 <xref:System.Data.SqlClient.SqlParameter> 屬性已經擴充，以便與大型 UDT 搭配運作。  
  
|SqlParameter 屬性|描述|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|取得或設定代表參數值的物件。 預設值是 null。 屬性可以是 `SqlBinary`、`Byte[]` 或受控物件。|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|取得或設定代表參數值的物件。 預設值是 null。 屬性可以是 `SqlBinary`、`Byte[]` 或受控物件。|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|取得或設定要解析的參數值大小。 預設值為 0。 屬性可以是代表參數值大小的整數。 對於大型 UDT 而言，這可能是 UDT 的實際大小，-1 則代表未知。|  
  
## <a name="retrieving-data-example"></a>擷取資料範例  
 下列程式碼片段示範如何擷取大型 UDT 資料。 `connectionString` 變數會假設已與 SQL Server 資料庫建立有效連線，而 `commandString` 變數會假設先列出具備主索引鍵資料行的有效 SELECT 陳述式。  
  
```csharp  
using (SqlConnection connection = new SqlConnection(
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a>另請參閱

- [設定參數和參數資料類型](../configuring-parameters-and-parameter-data-types.md)
- [擷取資料庫結構描述資訊](../retrieving-database-schema-information.md)
- [SQL Server 資料類型對應](../sql-server-data-type-mappings.md)
- [SQL 伺服器二進位和大值資料](sql-server-binary-and-large-value-data.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
