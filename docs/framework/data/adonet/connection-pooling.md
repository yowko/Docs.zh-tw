---
title: 連接共用
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: 4cba53993489f51ed39ac52bff4fa252beb9aafd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61880009"
---
# <a name="connection-pooling"></a><span data-ttu-id="0e25e-102">連接共用</span><span class="sxs-lookup"><span data-stu-id="0e25e-102">Connection Pooling</span></span>
<span data-ttu-id="0e25e-103">連接至資料來源可能會很耗時。</span><span class="sxs-lookup"><span data-stu-id="0e25e-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="0e25e-104">為了減少開啟連接的成本，ADO.NET 會使用名為的最佳化技術*連接共用*，以便有效減少重複開啟和關閉連接的成本。</span><span class="sxs-lookup"><span data-stu-id="0e25e-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="0e25e-105">連接共用的處理方式不同於 .NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="0e25e-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e25e-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="0e25e-106">In This Section</span></span>  
 [<span data-ttu-id="0e25e-107">SQL Server 連線共用 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0e25e-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="0e25e-108">提供連線集區的概觀，並描述連接共用如何在 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0e25e-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="0e25e-109">OLE DB、ODBC 和 Oracle 連接共用</span><span class="sxs-lookup"><span data-stu-id="0e25e-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="0e25e-110">描述 .NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC 和 .NET Framework Data Provider for Oracle 的連接共用。</span><span class="sxs-lookup"><span data-stu-id="0e25e-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e25e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e25e-111">See also</span></span>

- [<span data-ttu-id="0e25e-112">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="0e25e-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="0e25e-113">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0e25e-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
