---
title: 大型 UDT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 3c74bed67069740354b36891db73ed80b952f0c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362720"
---
# <a name="large-udts"></a><span data-ttu-id="06883-102">大型 UDT</span><span class="sxs-lookup"><span data-stu-id="06883-102">Large UDTs</span></span>
<span data-ttu-id="06883-103">使用者定義型別 (UDT) 可透過在 SQL Server 資料庫中儲存 Common Language Runtime (CLR) 物件，讓開發人員擴充伺服器的純量型別 (Scalar Type) 系統。</span><span class="sxs-lookup"><span data-stu-id="06883-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="06883-104">UDT 可以包含多個項目而且可以具有行為，這點與單一 SQL Server 系統資料型別所組成的傳統別名資料型別不同。</span><span class="sxs-lookup"><span data-stu-id="06883-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06883-105">您必須安裝 .NET Framework 3.5 SP1 (或更新版本) 才能運用大型 UDT 的強化 SqlClient 支援。</span><span class="sxs-lookup"><span data-stu-id="06883-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="06883-106">之前 UDT 有 8 KB 的大小上限。</span><span class="sxs-lookup"><span data-stu-id="06883-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="06883-107">在 SQL Server 2008 中，使用 <xref:Microsoft.SqlServer.Server.Format.UserDefined> 格式的 UDT 已不再具有這項限制。</span><span class="sxs-lookup"><span data-stu-id="06883-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="06883-108">如需使用者定義型別的完整文件，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="06883-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="06883-109">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="06883-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="06883-110">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="06883-110">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="06883-111">使用 GetSchema 來擷取 UDT 結構描述</span><span class="sxs-lookup"><span data-stu-id="06883-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="06883-112"><xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> 的 <xref:System.Data.SqlClient.SqlConnection> 方法會在 <xref:System.Data.DataTable> 中傳回資料庫結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="06883-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="06883-113">如需詳細資訊，請參閱[SQL Server 結構描述集合](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="06883-113">For more information, see [SQL Server Schema Collections](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="06883-114">UDT 的 GetSchemaTable 資料行值</span><span class="sxs-lookup"><span data-stu-id="06883-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="06883-115"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> 的 <xref:System.Data.SqlClient.SqlDataReader> 方法會傳回描述資料行中繼資料的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="06883-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="06883-116">下表將針對 SQL Server 2005 與 SQL Server 2008 之間的大型 UDT 描述資料行中繼資料的差異。</span><span class="sxs-lookup"><span data-stu-id="06883-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="06883-117">SqlDataReader 資料行</span><span class="sxs-lookup"><span data-stu-id="06883-117">SqlDataReader column</span></span>|<span data-ttu-id="06883-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="06883-118">SQL Server 2005</span></span>|<span data-ttu-id="06883-119">SQL Server 2008 及更新版</span><span class="sxs-lookup"><span data-stu-id="06883-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="06883-120">視情況而定</span><span class="sxs-lookup"><span data-stu-id="06883-120">Varies</span></span>|<span data-ttu-id="06883-121">視情況而定</span><span class="sxs-lookup"><span data-stu-id="06883-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="06883-122">255</span><span class="sxs-lookup"><span data-stu-id="06883-122">255</span></span>|<span data-ttu-id="06883-123">255</span><span class="sxs-lookup"><span data-stu-id="06883-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="06883-124">255</span><span class="sxs-lookup"><span data-stu-id="06883-124">255</span></span>|<span data-ttu-id="06883-125">255</span><span class="sxs-lookup"><span data-stu-id="06883-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="06883-126">UDT 執行個體</span><span class="sxs-lookup"><span data-stu-id="06883-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="06883-127">UDT 執行個體</span><span class="sxs-lookup"><span data-stu-id="06883-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="06883-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="06883-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="06883-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="06883-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="06883-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="06883-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="06883-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="06883-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="06883-132">三部分名稱指定為*Database.SchemaName.TypeName*。</span><span class="sxs-lookup"><span data-stu-id="06883-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="06883-133">視情況而定</span><span class="sxs-lookup"><span data-stu-id="06883-133">Varies</span></span>|<span data-ttu-id="06883-134">視情況而定</span><span class="sxs-lookup"><span data-stu-id="06883-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="06883-135">SqlDataReader 考量</span><span class="sxs-lookup"><span data-stu-id="06883-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="06883-136">從 SQL Server 2008 開始，<xref:System.Data.SqlClient.SqlDataReader> 已擴充，可支援大型 UDT 值的擷取。</span><span class="sxs-lookup"><span data-stu-id="06883-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="06883-137"><xref:System.Data.SqlClient.SqlDataReader> 處理大型 UDT 值的方式取決於您所使用的 SQL Server 版本，以及連接字串中指定的 `Type System Version`。</span><span class="sxs-lookup"><span data-stu-id="06883-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="06883-138">如需詳細資訊，請參閱<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="06883-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="06883-139">當 <xref:System.Data.SqlClient.SqlDataReader> 設定為 SQL Server 2005 時，下列 <xref:System.Data.SqlTypes.SqlBinary> 方法會傳回 `Type System Version` 而非 UDT：</span><span class="sxs-lookup"><span data-stu-id="06883-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="06883-140">當 `Byte[]` 設定為 SQL Server 2005 時，下列方法會傳回 `Type System Version` 陣列而非 UDT：</span><span class="sxs-lookup"><span data-stu-id="06883-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="06883-141">請注意，尚未針對 ADO.NET 的目前版本進行任何轉換。</span><span class="sxs-lookup"><span data-stu-id="06883-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="06883-142">指定 SqlParameters</span><span class="sxs-lookup"><span data-stu-id="06883-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="06883-143">下列的 <xref:System.Data.SqlClient.SqlParameter> 屬性已經過擴充，可使用大型 UDT。</span><span class="sxs-lookup"><span data-stu-id="06883-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="06883-144">SqlParameter 屬性</span><span class="sxs-lookup"><span data-stu-id="06883-144">SqlParameter Property</span></span>|<span data-ttu-id="06883-145">描述</span><span class="sxs-lookup"><span data-stu-id="06883-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="06883-146">取得或設定代表參數值的物件。</span><span class="sxs-lookup"><span data-stu-id="06883-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="06883-147">預設為 null。</span><span class="sxs-lookup"><span data-stu-id="06883-147">The default is null.</span></span> <span data-ttu-id="06883-148">此屬性可以是 `SqlBinary`、`Byte[]` 或 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="06883-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="06883-149">取得或設定代表參數值的物件。</span><span class="sxs-lookup"><span data-stu-id="06883-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="06883-150">預設為 null。</span><span class="sxs-lookup"><span data-stu-id="06883-150">The default is null.</span></span> <span data-ttu-id="06883-151">此屬性可以是 `SqlBinary`、`Byte[]` 或 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="06883-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="06883-152">取得或設定要解析之參數值的大小。</span><span class="sxs-lookup"><span data-stu-id="06883-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="06883-153">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="06883-153">The default value is 0.</span></span> <span data-ttu-id="06883-154">屬性可以是代表參數值大小的整數。</span><span class="sxs-lookup"><span data-stu-id="06883-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="06883-155">對於大型 UDT 而言，這可能是 UDT 的實際大小，-1 則代表未知。</span><span class="sxs-lookup"><span data-stu-id="06883-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="06883-156">擷取資料範例</span><span class="sxs-lookup"><span data-stu-id="06883-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="06883-157">下列程式碼片段將示範如何擷取大型 UDT 資料。</span><span class="sxs-lookup"><span data-stu-id="06883-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="06883-158">`connectionString` 變數會假設 SQL Server 資料庫的有效連接，而且 `commandString` 變數會假設先列出主索引鍵資料行的有效 SELECT 陳述式 (Statement)。</span><span class="sxs-lookup"><span data-stu-id="06883-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06883-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06883-159">See Also</span></span>  
 [<span data-ttu-id="06883-160">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="06883-160">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="06883-161">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="06883-161">Retrieving Database Schema Information</span></span>](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="06883-162">SQL Server 資料類型對應</span><span class="sxs-lookup"><span data-stu-id="06883-162">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="06883-163">SQL Server 二進位和大量數值資料</span><span class="sxs-lookup"><span data-stu-id="06883-163">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="06883-164">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="06883-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
