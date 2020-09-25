---
title: SQL Server 和 ADO.NET
description: 瞭解 SQL Server 的 .NET Framework Data Provider 的功能和行為，這會封裝資料庫特定的通訊協定。
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: a517bccd9b60d00f6c6c636c9164d63fb5966de3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197387"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="3e90e-103">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3e90e-103">SQL Server and ADO.NET</span></span>

<span data-ttu-id="3e90e-104">本節說明 .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 特有的功能與行為。</span><span class="sxs-lookup"><span data-stu-id="3e90e-104">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="3e90e-105"><xref:System.Data.SqlClient> 讓您能夠存取 SQL Server 版本，其中封裝了資料庫專屬的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="3e90e-105"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="3e90e-106">該資料提供者的功能設計類似於 OLE DB、ODBC 及 Oracle 的 .NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="3e90e-106">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="3e90e-107"><xref:System.Data.SqlClient> 包含表格式資料流 (TDS) 剖析器，可以直接與 SQL Server 通訊。</span><span class="sxs-lookup"><span data-stu-id="3e90e-107"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e90e-108">若要使用 SQL Server 的 .NET Framework 資料提供者，應用程式必須參考 <xref:System.Data.SqlClient> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="3e90e-108">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e90e-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="3e90e-109">In This Section</span></span>  

 [<span data-ttu-id="3e90e-110">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="3e90e-110">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="3e90e-111">提供 SQL Server 安全性功能的概觀及應用程式案例，適用於建立以 SQL Server 為目標的安全 ADO.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3e90e-111">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="3e90e-112">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3e90e-112">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="3e90e-113">說明如何使用 SQL Server 資料型別，以及它們如何與 .NET Framework 資料型別互動。</span><span class="sxs-lookup"><span data-stu-id="3e90e-113">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="3e90e-114">SQL Server 二進位和大數值資料</span><span class="sxs-lookup"><span data-stu-id="3e90e-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="3e90e-115">說明如何在 SQL Server 中使用大型數值資料。</span><span class="sxs-lookup"><span data-stu-id="3e90e-115">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="3e90e-116">ADO.NET 中的 SQL Server 資料作業</span><span class="sxs-lookup"><span data-stu-id="3e90e-116">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="3e90e-117">說明如何使用 SQL Server 中的資料。</span><span class="sxs-lookup"><span data-stu-id="3e90e-117">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="3e90e-118">包含大量複製作業、MARS、非同步作業和資料表值參數的相關章節。</span><span class="sxs-lookup"><span data-stu-id="3e90e-118">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="3e90e-119">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3e90e-119">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="3e90e-120">描述 ADO.NET 應用程式開發人員適用的 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="3e90e-120">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="3e90e-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3e90e-121">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="3e90e-122">說明建立 LINQ to SQL 應用程式所需的基本建置組塊 (Building Blocks)、處理序和技巧。</span><span class="sxs-lookup"><span data-stu-id="3e90e-122">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="3e90e-123">如需 SQL Server 資料庫引擎的完整文件，請依據您使用的 SQL Server 版本參閱 SQL Server 線上叢書。</span><span class="sxs-lookup"><span data-stu-id="3e90e-123">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="3e90e-124">SQL Server 線上叢書</span><span class="sxs-lookup"><span data-stu-id="3e90e-124">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="3e90e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e90e-125">See also</span></span>

- [<span data-ttu-id="3e90e-126">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="3e90e-126">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="3e90e-127">ADO.NET 中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="3e90e-127">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="3e90e-128">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="3e90e-128">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="3e90e-129">在 ADO.NET 中傳送和修改資料</span><span class="sxs-lookup"><span data-stu-id="3e90e-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- <span data-ttu-id="3e90e-130">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="3e90e-130">[ADO.NET Overview](../ado-net-overview.md)</span></span>
