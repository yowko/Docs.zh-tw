---
title: "SQL Server 和 ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: effff61b424f914584ba1ffd963c100afbc3d745
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="e39a7-102">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e39a7-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="e39a7-103">本節說明 .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 特有的功能與行為。</span><span class="sxs-lookup"><span data-stu-id="e39a7-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="e39a7-104"><xref:System.Data.SqlClient> 封裝了資料庫特有的通訊協定，可讓您存取不同的 SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="e39a7-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="e39a7-105">該資料提供者的功能設計類似於 OLE DB、ODBC 及 Oracle 的 .NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="e39a7-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="e39a7-106"><xref:System.Data.SqlClient> 包含可直接與 SQL Server 通訊的表格式資料流 (TDS) 剖析器。</span><span class="sxs-lookup"><span data-stu-id="e39a7-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e39a7-107">若要使用 SQL Server 的 .NET Framework 資料提供者，應用程式必須參考 <xref:System.Data.SqlClient> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="e39a7-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e39a7-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e39a7-108">In This Section</span></span>  
 [<span data-ttu-id="e39a7-109">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="e39a7-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="e39a7-110">提供 SQL Server 安全性功能的概觀，以及可用於建立以 SQL Server 為目標之安全 ADO.NET 應用程式的應用程式案例。</span><span class="sxs-lookup"><span data-stu-id="e39a7-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="e39a7-111">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e39a7-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="e39a7-112">說明如何使用 SQL Server 資料型別，以及它們如何與 .NET Framework 資料型別互動。</span><span class="sxs-lookup"><span data-stu-id="e39a7-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="e39a7-113">SQL Server 二進位和大量數值資料</span><span class="sxs-lookup"><span data-stu-id="e39a7-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="e39a7-114">說明如何在 SQL Server 中使用大數值資料。</span><span class="sxs-lookup"><span data-stu-id="e39a7-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="e39a7-115">ADO.NET 中的 SQL Server 資料作業</span><span class="sxs-lookup"><span data-stu-id="e39a7-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="e39a7-116">說明如何使用 SQL Server 中的資料。</span><span class="sxs-lookup"><span data-stu-id="e39a7-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="e39a7-117">包含有關大量複製作業、MARS、非同步作業和資料表值參數的章節。</span><span class="sxs-lookup"><span data-stu-id="e39a7-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="e39a7-118">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e39a7-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="e39a7-119">說明對於 ADO.NET 應用程式開發人員很有用的 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="e39a7-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="e39a7-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e39a7-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="e39a7-121">說明建立 LINQ to SQL 應用程式所需的基本建置組塊 (Building Blocks)、處理序和技巧。</span><span class="sxs-lookup"><span data-stu-id="e39a7-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="e39a7-122">如需 SQL Server Database Engine 的完整文件，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="e39a7-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="e39a7-123">SQL Server 線上叢書</span><span class="sxs-lookup"><span data-stu-id="e39a7-123">SQL Server Books Online</span></span>](http://msdn.microsoft.com/library/ms130214.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="e39a7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e39a7-124">See Also</span></span>  
 <span data-ttu-id="e39a7-125">[設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e39a7-125">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) </span></span>  
 <span data-ttu-id="e39a7-126">[ADO.NET 中的資料類型對應](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) </span><span class="sxs-lookup"><span data-stu-id="e39a7-126">[Data Type Mappings in ADO.NET](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) </span></span>  
 <span data-ttu-id="e39a7-127">[DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) </span><span class="sxs-lookup"><span data-stu-id="e39a7-127">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) </span></span>  
 <span data-ttu-id="e39a7-128">[在 ADO.NET 中擷取和修改資料](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) </span><span class="sxs-lookup"><span data-stu-id="e39a7-128">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) </span></span>  
 [<span data-ttu-id="e39a7-129">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e39a7-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

