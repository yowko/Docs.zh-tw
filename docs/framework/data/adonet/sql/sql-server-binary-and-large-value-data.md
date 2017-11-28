---
title: "SQL Server 二進位和大量數值資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9065f467cd353c17471db2c0d67001a188459819
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="e9248-102">SQL Server 二進位和大量數值資料</span><span class="sxs-lookup"><span data-stu-id="e9248-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="e9248-103">SQL Server 提供 `max` 規範，可擴充 `varchar`、`nvarchar` 和 `varbinary` 資料類型的儲存容量。</span><span class="sxs-lookup"><span data-stu-id="e9248-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="e9248-104">`varchar(max)``nvarchar(max)`，和`varbinary(max)`統稱為 「*大數值資料型別*。</span><span class="sxs-lookup"><span data-stu-id="e9248-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="e9248-105">您可以使用大數值資料型別來儲存最多可達 2^31-1 位元組的資料。</span><span class="sxs-lookup"><span data-stu-id="e9248-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="e9248-106">SQL Server 2008 導入了 FILESTREAM 屬性。這個屬性不是資料型別，而是可針對資料行定義的屬性，允許大數值資料儲存在檔案系統上，而非資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e9248-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9248-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e9248-107">In This Section</span></span>  
 [<span data-ttu-id="e9248-108">修改 ADO.NET 中的大數值 (max) 資料</span><span class="sxs-lookup"><span data-stu-id="e9248-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="e9248-109">說明如何使用大型值資料類型。</span><span class="sxs-lookup"><span data-stu-id="e9248-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="e9248-110">FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="e9248-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="e9248-111">說明如何使用儲存在 SQL Server 2008 中的大數值資料搭配 FILESTREAM 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9248-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9248-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9248-112">See Also</span></span>  
 [<span data-ttu-id="e9248-113">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e9248-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="e9248-114">ADO.NET 中的 SQL Server 資料作業</span><span class="sxs-lookup"><span data-stu-id="e9248-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="e9248-115">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="e9248-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="e9248-116">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e9248-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
