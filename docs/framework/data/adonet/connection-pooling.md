---
title: 連接共用
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: c431011cf57fd9ef79c2f0a099ab1080116c571f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786706"
---
# <a name="connection-pooling"></a><span data-ttu-id="b372c-102">連接共用</span><span class="sxs-lookup"><span data-stu-id="b372c-102">Connection Pooling</span></span>
<span data-ttu-id="b372c-103">連接至資料來源可能會很耗時。</span><span class="sxs-lookup"><span data-stu-id="b372c-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="b372c-104">為了將開啟連接的成本降至最低，ADO.NET 會使用稱為「*連接*共用」的優化技術，將重複開啟和關閉連接的成本降到最低。</span><span class="sxs-lookup"><span data-stu-id="b372c-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="b372c-105">連接共用的處理方式不同於 .NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="b372c-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b372c-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="b372c-106">In This Section</span></span>  
 [<span data-ttu-id="b372c-107">SQL Server 連線共用 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b372c-107">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="b372c-108">提供連接共用的總覽，並描述連接共用在 SQL Server 中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="b372c-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="b372c-109">OLE DB、ODBC 和 Oracle 連接共用</span><span class="sxs-lookup"><span data-stu-id="b372c-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="b372c-110">描述 .NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC 和 .NET Framework Data Provider for Oracle 的連接共用。</span><span class="sxs-lookup"><span data-stu-id="b372c-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b372c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b372c-111">See also</span></span>

- [<span data-ttu-id="b372c-112">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="b372c-112">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="b372c-113">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="b372c-113">ADO.NET Overview</span></span>](ado-net-overview.md)
