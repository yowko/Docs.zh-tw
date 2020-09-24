---
title: SQL Server 功能和 ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 2839529b-a79b-4450-be5d-07a98dbc7a0f
ms.openlocfilehash: 121381114fadd8b20978d2e932bf3ec8bdcdb193
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177315"
---
# <a name="sql-server-features-and-adonet"></a><span data-ttu-id="e5cd9-102">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e5cd9-102">SQL Server Features and ADO.NET</span></span>

<span data-ttu-id="e5cd9-103">本節中的主題將討論使用 ADO.NET 來開發資料庫應用程式的 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-103">The topics in this section discuss features in SQL Server that are targeted at developing database applications using ADO.NET.</span></span>  
  
 <span data-ttu-id="e5cd9-104">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》，如下列表格所列。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-104">For more information, see SQL Server Books Online for the version of SQL Server you are using, as listed in the following table.</span></span>  
  
 <span data-ttu-id="e5cd9-105">**SQL Server 文件**</span><span class="sxs-lookup"><span data-stu-id="e5cd9-105">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="e5cd9-106">[開發 (Database Engine)](/previous-versions/sql/sql-server-2008/bb500155(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="e5cd9-106">[Development (Database Engine)](/previous-versions/sql/sql-server-2008/bb500155(v=sql.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5cd9-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="e5cd9-107">In This Section</span></span>  

 [<span data-ttu-id="e5cd9-108">列舉 SQL Server (ADO.NET 的實例) </span><span class="sxs-lookup"><span data-stu-id="e5cd9-108">Enumerating Instances of SQL Server (ADO.NET)</span></span>](enumerating-instances-of-sql-server.md)  
 <span data-ttu-id="e5cd9-109">說明如何列舉 SQL Server 的使用中執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-109">Describes how to enumerate active instances of SQL Server.</span></span>  
  
 [<span data-ttu-id="e5cd9-110">SQL Server 的提供者統計資料</span><span class="sxs-lookup"><span data-stu-id="e5cd9-110">Provider Statistics for SQL Server</span></span>](provider-statistics-for-sql-server.md)  
 <span data-ttu-id="e5cd9-111">描述對取得 SQL Server 執行階段統計資料的支援。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-111">Describes support for obtaining SQL Server run-time statistics.</span></span>  
  
 [<span data-ttu-id="e5cd9-112">SQL Server Express 使用者實例</span><span class="sxs-lookup"><span data-stu-id="e5cd9-112">SQL Server Express User Instances</span></span>](sql-server-express-user-instances.md)  
 <span data-ttu-id="e5cd9-113">描述對 SQL Server Express 使用者執行個體的支援。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-113">Describes support for SQL Server Express user instances.</span></span>  
  
 [<span data-ttu-id="e5cd9-114">SQL Server 中的資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="e5cd9-114">Database Mirroring in SQL Server</span></span>](database-mirroring-in-sql-server.md)  
 <span data-ttu-id="e5cd9-115">描述資料庫鏡像功能。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-115">Describes database mirroring functionality.</span></span>  
  
 [<span data-ttu-id="e5cd9-116">SQL Server Common Language Runtime 整合</span><span class="sxs-lookup"><span data-stu-id="e5cd9-116">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)  
 <span data-ttu-id="e5cd9-117">說明如何從 SQL Server 中的 Common Language Runtime (CLR) 資料庫物件存取資料。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-117">Describes how data can be accessed from within a common language runtime (CLR) database object in SQL Server.</span></span>  
  
 [<span data-ttu-id="e5cd9-118">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="e5cd9-118">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)  
 <span data-ttu-id="e5cd9-119">說明當資料已經變更時，.NET Framework 應用程式如何向 SQL Server 要求通知。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-119">Describes how .NET Framework applications can request notification from SQL Server when data has changed.</span></span>  
  
 [<span data-ttu-id="e5cd9-120">SQL Server 中的快照集隔離</span><span class="sxs-lookup"><span data-stu-id="e5cd9-120">Snapshot Isolation in SQL Server</span></span>](snapshot-isolation-in-sql-server.md)  
 <span data-ttu-id="e5cd9-121">描述對快照集隔離的支援，這是為了減少交易式應用程式中的封鎖而設計的資料列版本設定機制。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-121">Describes support for snapshot isolation, a row versioning mechanism designed to reduce blocking in transactional applications.</span></span>  
  
 [<span data-ttu-id="e5cd9-122">高可用性、嚴重損壞修復的 SqlClient 支援</span><span class="sxs-lookup"><span data-stu-id="e5cd9-122">SqlClient Support for High Availability, Disaster Recovery</span></span>](sqlclient-support-for-high-availability-disaster-recovery.md)  
 <span data-ttu-id="e5cd9-123">描述 SqlClient 對高可用性、災害復原 (AlwaysOn) 可用性群組的支援。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-123">Describes SqlClient support for high-availability, disaster recovery (AlwaysOn) availability groups.</span></span>  
  
 [<span data-ttu-id="e5cd9-124">LocalDB 的 SqlClient 支援</span><span class="sxs-lookup"><span data-stu-id="e5cd9-124">SqlClient Support for LocalDB</span></span>](sqlclient-support-for-localdb.md)  
 <span data-ttu-id="e5cd9-125">描述 SqlClient 對 LocalDB 資料庫的支援。</span><span class="sxs-lookup"><span data-stu-id="e5cd9-125">Describes SqlClient support for LocalDB databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5cd9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5cd9-126">See also</span></span>

- [<span data-ttu-id="e5cd9-127">ADO.NET 中的 SQL Server 資料作業</span><span class="sxs-lookup"><span data-stu-id="e5cd9-127">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="e5cd9-128">在 ADO.NET 中傳送和修改資料</span><span class="sxs-lookup"><span data-stu-id="e5cd9-128">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="e5cd9-129">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e5cd9-129">LINQ to SQL</span></span>](./linq/index.md)
- <span data-ttu-id="e5cd9-130">[SQL Server and ADO.NET](index.md) (SQL Server 和 ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e5cd9-130">[SQL Server and ADO.NET](index.md)</span></span>
- <span data-ttu-id="e5cd9-131">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="e5cd9-131">[ADO.NET Overview](../ado-net-overview.md)</span></span>
