---
title: "連接共用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c7398fbea3b59cafed6f9a7f2f4f0440ef29b80a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="connection-pooling"></a><span data-ttu-id="2e137-102">連接共用</span><span class="sxs-lookup"><span data-stu-id="2e137-102">Connection Pooling</span></span>
<span data-ttu-id="2e137-103">連接至資料來源可能會很耗時。</span><span class="sxs-lookup"><span data-stu-id="2e137-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="2e137-104">為了減少開啟連接的成本，ADO.NET 會使用名為的最佳化技術*連接共用*，以便有效減少重複開啟和關閉連接的成本。</span><span class="sxs-lookup"><span data-stu-id="2e137-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="2e137-105">連接共用的處理方式不同於 .NET Framework 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="2e137-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e137-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="2e137-106">In This Section</span></span>  
 [<span data-ttu-id="2e137-107">SQL Server 連接共用 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2e137-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="2e137-108">提供連接共用的概觀並描述連接共用如何在 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 中運作。</span><span class="sxs-lookup"><span data-stu-id="2e137-108">Provides an overview of connection pooling and describes how connection pooling works in [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="2e137-109">OLE DB、 ODBC 和 Oracle 連接共用</span><span class="sxs-lookup"><span data-stu-id="2e137-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="2e137-110">描述 .NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC 和 .NET Framework Data Provider for Oracle 的連接共用。</span><span class="sxs-lookup"><span data-stu-id="2e137-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e137-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e137-111">See Also</span></span>  
 [<span data-ttu-id="2e137-112">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="2e137-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="2e137-113">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="2e137-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
