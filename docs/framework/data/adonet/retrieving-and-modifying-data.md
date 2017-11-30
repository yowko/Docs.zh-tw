---
title: "在 ADO.NET 中傳送和修改資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 35de20b1cb35fdcd87a653f1ac202c01d345c317
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="40456-102">在 ADO.NET 中傳送和修改資料</span><span class="sxs-lookup"><span data-stu-id="40456-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="40456-103">任何資料庫應用程式都有一個主要功能，那就是連接到資料來源並擷取其內含的資料。</span><span class="sxs-lookup"><span data-stu-id="40456-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="40456-104">ADO.NET 的.NET Framework 資料提供者做為應用程式和資料來源之間的橋樑可讓您執行命令以及有關使用擷取資料**DataReader**或**DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="40456-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="40456-105">任何資料庫應用程式都有一個主要功能，那就是更新資料庫中儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="40456-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="40456-106">在 ADO.NET 中，更新資料牽涉到使用**DataAdapter**和<xref:System.Data.DataSet>，和**命令**物件; 並且也可能需要使用交易。</span><span class="sxs-lookup"><span data-stu-id="40456-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40456-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="40456-107">In This Section</span></span>  
 [<span data-ttu-id="40456-108">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="40456-108">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 <span data-ttu-id="40456-109">說明如何建立資料來源的連接，以及如何使用連接事件。</span><span class="sxs-lookup"><span data-stu-id="40456-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="40456-110">連接字串</span><span class="sxs-lookup"><span data-stu-id="40456-110">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 <span data-ttu-id="40456-111">包含一些主題，其中說明連接字串 (包含連接字串關鍵字、安全性資訊) 的使用、儲存和擷取的各種層面。</span><span class="sxs-lookup"><span data-stu-id="40456-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="40456-112">連接共用</span><span class="sxs-lookup"><span data-stu-id="40456-112">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 <span data-ttu-id="40456-113">說明 .NET Framework 資料提供者的連接共用 (Connection Pooling)。</span><span class="sxs-lookup"><span data-stu-id="40456-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="40456-114">命令和參數</span><span class="sxs-lookup"><span data-stu-id="40456-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="40456-115">包含一些主題，其中說明如何建立命令和命令產生器、設定參數，以及執行命令來擷取和修改資料。</span><span class="sxs-lookup"><span data-stu-id="40456-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="40456-116">Dataadapter 和 Datareader</span><span class="sxs-lookup"><span data-stu-id="40456-116">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 <span data-ttu-id="40456-117">包含一些主題，其中說明 DataReader、DataAdapter、參數、處理 DataAdapter 事件，以及執行批次作業。</span><span class="sxs-lookup"><span data-stu-id="40456-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="40456-118">異動和並行存取</span><span class="sxs-lookup"><span data-stu-id="40456-118">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="40456-119">包含一些主題，其中說明如何執行本機異動、分散式異動，以及使用開放式並行存取 (Optimistic Concurrency)。</span><span class="sxs-lookup"><span data-stu-id="40456-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="40456-120">擷取識別或自動編號值</span><span class="sxs-lookup"><span data-stu-id="40456-120">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="40456-121">提供將產生的值對應的範例**識別**中的資料行[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]資料表或**Autonumber**欄位在 Microsoft Access 資料表中，資料表中插入資料列資料行。</span><span class="sxs-lookup"><span data-stu-id="40456-121">Provides an example of mapping the values generated for an **identity** column in a [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="40456-122">討論如何在 `DataTable` 中合併識別值。</span><span class="sxs-lookup"><span data-stu-id="40456-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="40456-123">擷取二進位資料</span><span class="sxs-lookup"><span data-stu-id="40456-123">Retrieving Binary Data</span></span>](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 <span data-ttu-id="40456-124">描述如何擷取二進位資料或使用大型資料結構`CommandBehavior`。`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="40456-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="40456-125">若要修改的預設行為`DataReader`。</span><span class="sxs-lookup"><span data-stu-id="40456-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="40456-126">使用預存程序修改資料</span><span class="sxs-lookup"><span data-stu-id="40456-126">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="40456-127">說明如何使用預存程序 (Stored Procedure) 輸入參數和輸出參數，將資料列插入資料庫中，並傳回新的識別值。</span><span class="sxs-lookup"><span data-stu-id="40456-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="40456-128">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="40456-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 <span data-ttu-id="40456-129">說明如何取得資料來源的可用資料庫或目錄、資料庫中的資料表和檢視表、資料表的條件約束，以及其他結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="40456-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="40456-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="40456-130">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="40456-131">說明提供者 Factory 模型並示範如何使用 `System.Data.Common` 命名空間 (Namespace) 中的基底類別 (Base Class)。</span><span class="sxs-lookup"><span data-stu-id="40456-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="40456-132">在 ADO.NET 中的資料追蹤</span><span class="sxs-lookup"><span data-stu-id="40456-132">Data Tracing in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-tracing.md)  
 <span data-ttu-id="40456-133">說明 ADO.NET 如何提供內建資料追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="40456-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="40456-134">效能計數器</span><span class="sxs-lookup"><span data-stu-id="40456-134">Performance Counters</span></span>](../../../../docs/framework/data/adonet/performance-counters.md)  
 <span data-ttu-id="40456-135">說明適用於 `SqlClient` 和 `OracleClient` 的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="40456-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="40456-136">非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="40456-136">Asynchronous Programming</span></span>](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 <span data-ttu-id="40456-137">描述 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 支援非同步程式設計。</span><span class="sxs-lookup"><span data-stu-id="40456-137">Describes [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="40456-138">SqlClient 串流支援</span><span class="sxs-lookup"><span data-stu-id="40456-138">SqlClient Streaming Support</span></span>](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 <span data-ttu-id="40456-139">討論如何撰寫從 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 串流資料而不需將它完全載入到記憶體中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="40456-139">Discusses how to write applications that stream data from [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40456-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40456-140">See Also</span></span>  
 [<span data-ttu-id="40456-141">ADO.NET 中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="40456-141">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="40456-142">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="40456-142">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="40456-143">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="40456-143">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="40456-144">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="40456-144">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="40456-145">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="40456-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
