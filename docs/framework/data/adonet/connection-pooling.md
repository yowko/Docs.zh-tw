---
title: 連接共用
description: 瞭解連接共用，這是一種優化技術，ADO.NET 用來將開啟連接至資料來源的成本降至最低。
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: b8f89dfda7edbde14dbb5945f10f2284ac43c3d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287086"
---
# <a name="connection-pooling"></a><span data-ttu-id="ea103-103">連接共用</span><span class="sxs-lookup"><span data-stu-id="ea103-103">Connection Pooling</span></span>
<span data-ttu-id="ea103-104">連接至資料來源可能會很耗時。</span><span class="sxs-lookup"><span data-stu-id="ea103-104">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="ea103-105">為了將開啟連接的成本降至最低，ADO.NET 會使用稱為「*連接*共用」的優化技術，將重複開啟和關閉連接的成本降到最低。</span><span class="sxs-lookup"><span data-stu-id="ea103-105">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="ea103-106">連接共用的處理方式不同於 .NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="ea103-106">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea103-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="ea103-107">In This Section</span></span>  
 [<span data-ttu-id="ea103-108">SQL Server 連接集區 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ea103-108">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="ea103-109">提供連接共用的總覽，並描述連接共用在 SQL Server 中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="ea103-109">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="ea103-110">OLE DB、ODBC 和 Oracle 連接共用</span><span class="sxs-lookup"><span data-stu-id="ea103-110">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="ea103-111">描述 .NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC 和 .NET Framework Data Provider for Oracle 的連接共用。</span><span class="sxs-lookup"><span data-stu-id="ea103-111">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea103-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea103-112">See also</span></span>

- [<span data-ttu-id="ea103-113">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="ea103-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="ea103-114">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="ea103-114">[ADO.NET Overview](ado-net-overview.md)</span></span>
