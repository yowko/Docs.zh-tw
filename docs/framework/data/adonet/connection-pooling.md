---
title: 連接共用
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: 28a1036f377326b5f1fdfafa1eaffd8a47bc05bc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139627"
---
# <a name="connection-pooling"></a><span data-ttu-id="40cd0-102">連接共用</span><span class="sxs-lookup"><span data-stu-id="40cd0-102">Connection Pooling</span></span>
<span data-ttu-id="40cd0-103">連接至資料來源可能會很耗時。</span><span class="sxs-lookup"><span data-stu-id="40cd0-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="40cd0-104">為了減少開啟連接的成本，ADO.NET 會使用名為的最佳化技術*連接共用*，以便有效減少重複開啟和關閉連接的成本。</span><span class="sxs-lookup"><span data-stu-id="40cd0-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="40cd0-105">連接共用的處理方式不同於 .NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="40cd0-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40cd0-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="40cd0-106">In This Section</span></span>  
 [<span data-ttu-id="40cd0-107">SQL Server 連線共用 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="40cd0-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="40cd0-108">提供連線集區的概觀，並描述連接共用如何在 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="40cd0-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="40cd0-109">OLE DB、ODBC 和 Oracle 連接共用</span><span class="sxs-lookup"><span data-stu-id="40cd0-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="40cd0-110">描述 .NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC 和 .NET Framework Data Provider for Oracle 的連接共用。</span><span class="sxs-lookup"><span data-stu-id="40cd0-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40cd0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40cd0-111">See Also</span></span>  
 [<span data-ttu-id="40cd0-112">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="40cd0-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="40cd0-113">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="40cd0-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
