---
title: 擷取資料庫結構描述資訊
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: c0aaadc82771d1c2a36d797bc157d88b8d3cacdc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177354"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="13378-102">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="13378-102">Retrieving Database Schema Information</span></span>

<span data-ttu-id="13378-103">從資料庫取得結構描述資訊是透過結構描述探索處理序來完成。</span><span class="sxs-lookup"><span data-stu-id="13378-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="13378-104">架構探索可讓應用程式要求受管理的提供者尋找並傳回指定資料庫之資料庫架構（也稱為 *中繼資料*）的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="13378-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="13378-105">不同的資料庫結構描述項目 (如資料表、資料行及預存程序) 都透過結構描述集合公開。</span><span class="sxs-lookup"><span data-stu-id="13378-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="13378-106">每個結構描述集合都包含正在使用的提供者之各種特定的結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="13378-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="13378-107">每個 .NET Framework managed 提供者都會在**連接**類別中執行**GetSchema**方法，而從**GetSchema**方法傳回的架構資訊則會以的形式呈現 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="13378-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="13378-108">**GetSchema**方法是一種多載方法，可提供選擇性參數來指定要傳回的架構集合，以及限制傳回的資訊量。</span><span class="sxs-lookup"><span data-stu-id="13378-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="13378-109">適用于 OLE DB、ODBC、Oracle 和 SqlClient 的 .NET Framework 資料提供者會提供 **GetSchemaTable** 方法，以傳回描述 **DataReader**之資料行中繼資料的 DataTable。</span><span class="sxs-lookup"><span data-stu-id="13378-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="13378-110">.NET Framework Data Provider for OLE DB 也會使用 <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> 物件的 <xref:System.Data.OleDb.OleDbConnection> 方法來公開結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="13378-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="13378-111">作為引數， **GetOleDbSchemaTable** 會接受 <xref:System.Data.OleDb.OleDbSchemaGuid> ，以識別要傳回的架構資訊，以及對這些傳回之資料行的限制陣列。</span><span class="sxs-lookup"><span data-stu-id="13378-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="13378-112">**GetOleDbSchemaTable** 會傳回 <xref:System.Data.DataTable> 填入所要求架構資訊的。</span><span class="sxs-lookup"><span data-stu-id="13378-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13378-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="13378-113">In This Section</span></span>  

 [<span data-ttu-id="13378-114">GetSchema 和結構描述集合</span><span class="sxs-lookup"><span data-stu-id="13378-114">GetSchema and Schema Collections</span></span>](getschema-and-schema-collections.md)  
 <span data-ttu-id="13378-115">描述 **GetSchema** 方法，以及如何使用它來從資料庫中取出和限制架構資訊。</span><span class="sxs-lookup"><span data-stu-id="13378-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="13378-116">結構描述限制</span><span class="sxs-lookup"><span data-stu-id="13378-116">Schema Restrictions</span></span>  
 <span data-ttu-id="13378-117">描述可搭配 **GetSchema**使用的架構限制。</span><span class="sxs-lookup"><span data-stu-id="13378-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="13378-118">一般結構描述集合</span><span class="sxs-lookup"><span data-stu-id="13378-118">Common Schema Collections</span></span>](common-schema-collections.md)  
 <span data-ttu-id="13378-119">說明所有 .NET Framework Managed 提供者支援的所有通用結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="13378-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="13378-120">SQL Server 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="13378-120">SQL Server Schema Collections</span></span>](sql-server-schema-collections.md)  
 <span data-ttu-id="13378-121">說明 .NET Framework Provider for SQL Server 所支援的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="13378-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="13378-122">Oracle 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="13378-122">Oracle Schema Collections</span></span>](oracle-schema-collections.md)  
 <span data-ttu-id="13378-123">說明 .NET Framework Provider for Oracle 所支援的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="13378-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="13378-124">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="13378-124">ODBC Schema Collections</span></span>](odbc-schema-collections.md)  
 <span data-ttu-id="13378-125">說明 ODBC 驅動程式的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="13378-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="13378-126">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="13378-126">OLE DB Schema Collections</span></span>](ole-db-schema-collections.md)  
 <span data-ttu-id="13378-127">說明 OLE DB 提供者的結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="13378-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="13378-128">參考</span><span class="sxs-lookup"><span data-stu-id="13378-128">Reference</span></span>  

 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="13378-129">描述類別的 **GetSchema** 方法 <xref:System.Data.Common.DbConnection> 。</span><span class="sxs-lookup"><span data-stu-id="13378-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="13378-130">描述類別的 **GetSchema** 方法 <xref:System.Data.Odbc.OdbcConnection> 。</span><span class="sxs-lookup"><span data-stu-id="13378-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="13378-131">描述類別的 **GetSchema** 方法 <xref:System.Data.OleDb.OleDbConnection> 。</span><span class="sxs-lookup"><span data-stu-id="13378-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="13378-132">描述類別的 **GetSchema** 方法 <xref:System.Data.OracleClient.OracleConnection> 。</span><span class="sxs-lookup"><span data-stu-id="13378-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="13378-133">描述類別的 **GetSchema** 方法 <xref:System.Data.SqlClient.SqlConnection> 。</span><span class="sxs-lookup"><span data-stu-id="13378-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="13378-134">描述類別的 **GetSchemaTable** 方法 <xref:System.Data.Common.DbDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="13378-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="13378-135">描述類別的 **GetSchemaTable** 方法 <xref:System.Data.Odbc.OdbcDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="13378-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="13378-136">描述類別的 **GetSchemaTable** 方法 <xref:System.Data.OleDb.OleDbDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="13378-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="13378-137">描述類別的 **GetSchemaTable** 方法 <xref:System.Data.OracleClient.OracleDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="13378-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="13378-138">描述類別的 **GetSchemaTable** 方法 <xref:System.Data.SqlClient.SqlDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="13378-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13378-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13378-139">See also</span></span>

- [<span data-ttu-id="13378-140">在 ADO.NET 中傳送和修改資料</span><span class="sxs-lookup"><span data-stu-id="13378-140">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="13378-141">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="13378-141">[ADO.NET Overview](ado-net-overview.md)</span></span>
