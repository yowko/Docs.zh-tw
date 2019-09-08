---
title: 擷取資料庫結構描述資訊
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 26b234e35a0d0849914d87b61f4e8c8a87599448
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782734"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="88831-102">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="88831-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="88831-103">從資料庫取得結構描述資訊是透過結構描述探索處理序來完成。</span><span class="sxs-lookup"><span data-stu-id="88831-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="88831-104">架構探索可讓應用程式要求 managed 提供者尋找並傳回指定資料庫之資料庫架構（也稱為*中繼資料*）的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="88831-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="88831-105">不同的資料庫結構描述項目 (如資料表、資料行及預存程序) 都透過結構描述集合公開。</span><span class="sxs-lookup"><span data-stu-id="88831-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="88831-106">每個結構描述集合都包含正在使用的提供者之各種特定的結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="88831-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="88831-107">每個 .NET Framework managed 提供者都會在**Connection**類別中執行**GetSchema**方法，而從**GetSchema**方法傳回的架構資訊則會<xref:System.Data.DataTable>以形式呈現。</span><span class="sxs-lookup"><span data-stu-id="88831-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="88831-108">**GetSchema**方法是一種多載的方法，它會提供選擇性參數來指定要傳回的架構集合，以及限制傳回的資訊量。</span><span class="sxs-lookup"><span data-stu-id="88831-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="88831-109">OLE DB、ODBC、Oracle 和 SqlClient 的 .NET Framework 資料提供者所提供的**GetSchemaTable**方法，會傳回描述**DataReader**之資料行中繼資料的 DataTable。</span><span class="sxs-lookup"><span data-stu-id="88831-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="88831-110">.NET Framework Data Provider for OLE DB 也會使用 <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> 物件的 <xref:System.Data.OleDb.OleDbConnection> 方法來公開結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="88831-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="88831-111">做為自變數，GetOleDbSchemaTable <xref:System.Data.OleDb.OleDbSchemaGuid>會採用識別要傳回之架構資訊的，以及對這些傳回之資料行的限制陣列。</span><span class="sxs-lookup"><span data-stu-id="88831-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="88831-112">**GetOleDbSchemaTable 會**傳回以所要求的架構資訊填入的。<xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="88831-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88831-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="88831-113">In This Section</span></span>  
 [<span data-ttu-id="88831-114">GetSchema 和結構描述集合</span><span class="sxs-lookup"><span data-stu-id="88831-114">GetSchema and Schema Collections</span></span>](getschema-and-schema-collections.md)  
 <span data-ttu-id="88831-115">描述**GetSchema**方法，以及如何使用它來從資料庫中取出和限制架構資訊。</span><span class="sxs-lookup"><span data-stu-id="88831-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="88831-116">結構描述限制</span><span class="sxs-lookup"><span data-stu-id="88831-116">Schema Restrictions</span></span>  
 <span data-ttu-id="88831-117">說明可搭配**GetSchema**使用的架構限制。</span><span class="sxs-lookup"><span data-stu-id="88831-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="88831-118">一般結構描述集合</span><span class="sxs-lookup"><span data-stu-id="88831-118">Common Schema Collections</span></span>](common-schema-collections.md)  
 <span data-ttu-id="88831-119">說明所有 .NET Framework Managed 提供者支援的所有通用結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="88831-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="88831-120">SQL Server 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="88831-120">SQL Server Schema Collections</span></span>](sql-server-schema-collections.md)  
 <span data-ttu-id="88831-121">說明 .NET Framework Provider for SQL Server 所支援的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="88831-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="88831-122">Oracle 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="88831-122">Oracle Schema Collections</span></span>](oracle-schema-collections.md)  
 <span data-ttu-id="88831-123">說明 .NET Framework Provider for Oracle 所支援的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="88831-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="88831-124">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="88831-124">ODBC Schema Collections</span></span>](odbc-schema-collections.md)  
 <span data-ttu-id="88831-125">說明 ODBC 驅動程式的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="88831-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="88831-126">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="88831-126">OLE DB Schema Collections</span></span>](ole-db-schema-collections.md)  
 <span data-ttu-id="88831-127">說明 OLE DB 提供者的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="88831-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="88831-128">參考資料</span><span class="sxs-lookup"><span data-stu-id="88831-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="88831-129">說明<xref:System.Data.Common.DbConnection>類別的**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="88831-130">說明<xref:System.Data.Odbc.OdbcConnection>類別的**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="88831-131">說明<xref:System.Data.OleDb.OleDbConnection>類別的**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="88831-132">說明<xref:System.Data.OracleClient.OracleConnection>類別的**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="88831-133">說明<xref:System.Data.SqlClient.SqlConnection>類別的**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="88831-134">說明<xref:System.Data.Common.DbDataReader>類別的**GetSchemaTable**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="88831-135">說明<xref:System.Data.Odbc.OdbcDataReader>類別的**GetSchemaTable**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="88831-136">說明<xref:System.Data.OleDb.OleDbDataReader>類別的**GetSchemaTable**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="88831-137">說明<xref:System.Data.OracleClient.OracleDataReader>類別的**GetSchemaTable**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="88831-138">說明<xref:System.Data.SqlClient.SqlDataReader>類別的**GetSchemaTable**方法。</span><span class="sxs-lookup"><span data-stu-id="88831-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88831-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88831-139">See also</span></span>

- [<span data-ttu-id="88831-140">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="88831-140">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="88831-141">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="88831-141">ADO.NET Overview</span></span>](ado-net-overview.md)
