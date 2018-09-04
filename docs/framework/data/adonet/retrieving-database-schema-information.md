---
title: 擷取資料庫結構描述資訊
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 00cf0e36dd7886897c26adf50102f32892ebb18e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562700"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="e7212-102">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="e7212-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="e7212-103">從資料庫取得結構描述資訊是透過結構描述探索處理序來完成。</span><span class="sxs-lookup"><span data-stu-id="e7212-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="e7212-104">結構描述探索允許應用程式要求 managed 提供者尋找並傳回資料庫結構描述的相關資訊，也稱為*中繼資料*，針對給定的資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7212-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="e7212-105">不同的資料庫結構描述項目 (如資料表、資料行及預存程序) 都透過結構描述集合公開。</span><span class="sxs-lookup"><span data-stu-id="e7212-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="e7212-106">每個結構描述集合都包含正在使用的提供者之各種特定的結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="e7212-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="e7212-107">每個.NET Framework managed 提供者實作**GetSchema**方法中的**連線**類別，並從傳回的結構描述資訊**GetSchema**方法傳入的形式<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="e7212-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="e7212-108">**GetSchema**方法是多載的方法，提供選擇性參數指定要傳回的結構描述集合及限制傳回的資訊量。</span><span class="sxs-lookup"><span data-stu-id="e7212-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="e7212-109">提供.NET Framework Data Provider for OLE DB、 ODBC、 Oracle 和 SqlClient **GetSchemaTable**方法會傳回描述資料行中繼資料的 DataTable **DataReader**。</span><span class="sxs-lookup"><span data-stu-id="e7212-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="e7212-110">.NET Framework Data Provider for OLE DB 也會使用 <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> 物件的 <xref:System.Data.OleDb.OleDbConnection> 方法來公開結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="e7212-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="e7212-111">做為引數， **GetOleDbSchemaTable**採用<xref:System.Data.OleDb.OleDbSchemaGuid>可識別要傳回的結構描述資訊，並傳回資料行的那些限制陣列。</span><span class="sxs-lookup"><span data-stu-id="e7212-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="e7212-112">**GetOleDbSchemaTable**傳回<xref:System.Data.DataTable>填入要求的結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="e7212-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7212-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="e7212-113">In This Section</span></span>  
 [<span data-ttu-id="e7212-114">GetSchema 和結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e7212-114">GetSchema and Schema Collections</span></span>](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 <span data-ttu-id="e7212-115">描述**GetSchema**方法，以及如何使用它來擷取及限制資料庫的結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="e7212-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="e7212-116">結構描述限制</span><span class="sxs-lookup"><span data-stu-id="e7212-116">Schema Restrictions</span></span>  
 <span data-ttu-id="e7212-117">描述可以搭配使用的結構描述限制**GetSchema**。</span><span class="sxs-lookup"><span data-stu-id="e7212-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="e7212-118">一般結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e7212-118">Common Schema Collections</span></span>](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 <span data-ttu-id="e7212-119">說明所有 .NET Framework Managed 提供者支援的所有通用結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="e7212-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="e7212-120">SQL Server 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e7212-120">SQL Server Schema Collections</span></span>](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 <span data-ttu-id="e7212-121">說明 .NET Framework Provider for SQL Server 所支援的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="e7212-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="e7212-122">Oracle 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e7212-122">Oracle Schema Collections</span></span>](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 <span data-ttu-id="e7212-123">說明 .NET Framework Provider for Oracle 所支援的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="e7212-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="e7212-124">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e7212-124">ODBC Schema Collections</span></span>](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 <span data-ttu-id="e7212-125">說明 ODBC 驅動程式的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="e7212-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="e7212-126">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e7212-126">OLE DB Schema Collections</span></span>](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 <span data-ttu-id="e7212-127">說明 OLE DB 提供者的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="e7212-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e7212-128">參考資料</span><span class="sxs-lookup"><span data-stu-id="e7212-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="e7212-129">描述**GetSchema**方法<xref:System.Data.Common.DbConnection>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="e7212-130">描述**GetSchema**方法<xref:System.Data.Odbc.OdbcConnection>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="e7212-131">描述**GetSchema**方法<xref:System.Data.OleDb.OleDbConnection>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="e7212-132">描述**GetSchema**方法<xref:System.Data.OracleClient.OracleConnection>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="e7212-133">描述**GetSchema**方法<xref:System.Data.SqlClient.SqlConnection>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="e7212-134">描述**GetSchemaTable**方法<xref:System.Data.Common.DbDataReader>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="e7212-135">描述**GetSchemaTable**方法<xref:System.Data.Odbc.OdbcDataReader>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="e7212-136">描述**GetSchemaTable**方法<xref:System.Data.OleDb.OleDbDataReader>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="e7212-137">描述**GetSchemaTable**方法<xref:System.Data.OracleClient.OracleDataReader>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="e7212-138">描述**GetSchemaTable**方法<xref:System.Data.SqlClient.SqlDataReader>類別。</span><span class="sxs-lookup"><span data-stu-id="e7212-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7212-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7212-139">See Also</span></span>  
 [<span data-ttu-id="e7212-140">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="e7212-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="e7212-141">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e7212-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
