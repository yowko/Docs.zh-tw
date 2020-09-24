---
title: 抓取和修改資料
description: 在 .NET Framework 中，ADO.NET 中的資料提供者可做為應用程式與資料來源之間的橋樑，以讀取和更新資料。
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 7620843e77b25606b2dec2bf6eae3a4f40d1b9fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150670"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="1c0f1-103">在 ADO.NET 中傳送和修改資料</span><span class="sxs-lookup"><span data-stu-id="1c0f1-103">Retrieving and Modifying Data in ADO.NET</span></span>

<span data-ttu-id="1c0f1-104">任何資料庫應用程式都有一個主要功能，那就是連接到資料來源並擷取其內含的資料。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-104">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="1c0f1-105">ADO.NET 的 .NET Framework 資料提供者可做為應用程式與資料來源之間的橋樑，讓您可以執行命令，以及使用 **DataReader** 或 **DataAdapter**來取出資料。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-105">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="1c0f1-106">任何資料庫應用程式都有一個主要功能，那就是更新資料庫中儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-106">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="1c0f1-107">在 ADO.NET 中，更新資料牽涉到使用 **DataAdapter** 和和 <xref:System.Data.DataSet> **命令** 物件，而且也可能牽涉到使用交易。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-107">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c0f1-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="1c0f1-108">In This Section</span></span>  

 [<span data-ttu-id="1c0f1-109">連接到資料來源</span><span class="sxs-lookup"><span data-stu-id="1c0f1-109">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="1c0f1-110">說明如何建立資料來源的連接，以及如何使用連接事件。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-110">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="1c0f1-111">連接字串</span><span class="sxs-lookup"><span data-stu-id="1c0f1-111">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="1c0f1-112">包含一些主題，其中說明連接字串 (包含連接字串關鍵字、安全性資訊) 的使用、儲存和擷取的各種層面。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-112">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="1c0f1-113">連接共用</span><span class="sxs-lookup"><span data-stu-id="1c0f1-113">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="1c0f1-114">說明 .NET Framework 資料提供者的連接共用 (Connection Pooling)。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-114">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="1c0f1-115">命令和參數</span><span class="sxs-lookup"><span data-stu-id="1c0f1-115">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="1c0f1-116">包含一些主題，其中說明如何建立命令和命令產生器、設定參數，以及執行命令來擷取和修改資料。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-116">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="1c0f1-117">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="1c0f1-117">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="1c0f1-118">包含一些主題，其中說明 DataReader、DataAdapter、參數、處理 DataAdapter 事件，以及執行批次作業。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-118">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="1c0f1-119">異動和並行存取</span><span class="sxs-lookup"><span data-stu-id="1c0f1-119">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="1c0f1-120">包含一些主題，其中說明如何執行本機異動、分散式異動，以及使用開放式並行存取 (Optimistic Concurrency)。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-120">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="1c0f1-121">擷取識別或自動編號值</span><span class="sxs-lookup"><span data-stu-id="1c0f1-121">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="1c0f1-122">提供範例，說明如何將 SQL Server 資料表中的 **標識** 列或 Microsoft Access 資料表中的 **自動編號** 欄位所產生的值，對應至資料表中插入之資料列的資料行。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-122">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="1c0f1-123">討論如何在 `DataTable` 中合併識別值。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-123">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="1c0f1-124">擷取二進位資料</span><span class="sxs-lookup"><span data-stu-id="1c0f1-124">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="1c0f1-125">描述如何使用取出二進位資料或大型資料結構 `CommandBehavior` 。`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="1c0f1-125">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="1c0f1-126">修改的預設行為 `DataReader` 。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-126">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="1c0f1-127">使用預存程序修改資料</span><span class="sxs-lookup"><span data-stu-id="1c0f1-127">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="1c0f1-128">說明如何使用預存程序 (Stored Procedure) 輸入參數和輸出參數，將資料列插入資料庫中，並傳回新的識別值。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-128">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="1c0f1-129">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="1c0f1-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="1c0f1-130">說明如何取得資料來源的可用資料庫或目錄、資料庫中的資料表和檢視表、資料表的條件約束，以及其他結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-130">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="1c0f1-131">DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="1c0f1-131">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="1c0f1-132">說明提供者 Factory 模型並示範如何使用 `System.Data.Common` 命名空間 (Namespace) 中的基底類別 (Base Class)。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-132">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="1c0f1-133">ADO.NET 中的資料追蹤</span><span class="sxs-lookup"><span data-stu-id="1c0f1-133">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="1c0f1-134">說明 ADO.NET 如何提供內建資料追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-134">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="1c0f1-135">效能計數器</span><span class="sxs-lookup"><span data-stu-id="1c0f1-135">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="1c0f1-136">說明適用於 `SqlClient` 和 `OracleClient` 的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-136">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="1c0f1-137">非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="1c0f1-137">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="1c0f1-138">描述非同步程式設計的 ADO.NET 支援。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-138">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="1c0f1-139">SqlClient 資料流支援</span><span class="sxs-lookup"><span data-stu-id="1c0f1-139">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="1c0f1-140">討論如何撰寫應用程式，以從 SQL Server 串流資料，而不需要將它完全載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="1c0f1-140">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0f1-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c0f1-141">See also</span></span>

- [<span data-ttu-id="1c0f1-142">ADO.NET 中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="1c0f1-142">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="1c0f1-143">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="1c0f1-143">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="1c0f1-144">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="1c0f1-144">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- <span data-ttu-id="1c0f1-145">[SQL Server and ADO.NET](./sql/index.md) (SQL Server 和 ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1c0f1-145">[SQL Server and ADO.NET](./sql/index.md)</span></span>
- <span data-ttu-id="1c0f1-146">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="1c0f1-146">[ADO.NET Overview](ado-net-overview.md)</span></span>
