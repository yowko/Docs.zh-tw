---
title: SQL Server 二進位和大量數值資料
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: a9296e83b0f4e4352423470433670bb2cbe5a248
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183035"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="3c130-102">SQL Server 二進位和大量數值資料</span><span class="sxs-lookup"><span data-stu-id="3c130-102">SQL Server Binary and Large-Value Data</span></span>

<span data-ttu-id="3c130-103">SQL Server 提供 `max` 指定名稱，可擴充 `varchar`、`nvarchar` 和 `varbinary` 資料類型的儲存容量。</span><span class="sxs-lookup"><span data-stu-id="3c130-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="3c130-104">`varchar(max)`、`nvarchar(max)` 和 `varbinary(max)` 統稱為「大數值資料類型」\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c130-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="3c130-105">您可以使用大數值資料類型來儲存最多可達 2^31-1 位元組的資料。</span><span class="sxs-lookup"><span data-stu-id="3c130-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="3c130-106">SQL Server 2008 引進了 FILESTREAM 屬性，其不是資料類型，而是可定義於資料行上的屬性，能夠將大數值資料儲存於檔案系統，而不是資料庫中。</span><span class="sxs-lookup"><span data-stu-id="3c130-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c130-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="3c130-107">In This Section</span></span>  

 [<span data-ttu-id="3c130-108">修改 ADO.NET 中的大型值 (最大) 資料</span><span class="sxs-lookup"><span data-stu-id="3c130-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="3c130-109">描述如何使用大數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="3c130-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="3c130-110">FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="3c130-110">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="3c130-111">描述如何使用以 FILESTREAM 屬性儲存在 SQL Server 2008 中的大型值資料。</span><span class="sxs-lookup"><span data-stu-id="3c130-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c130-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c130-112">See also</span></span>

- [<span data-ttu-id="3c130-113">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3c130-113">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="3c130-114">ADO.NET 中的 SQL Server 資料作業</span><span class="sxs-lookup"><span data-stu-id="3c130-114">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="3c130-115">在 ADO.NET 中傳送和修改資料</span><span class="sxs-lookup"><span data-stu-id="3c130-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- <span data-ttu-id="3c130-116">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="3c130-116">[ADO.NET Overview](../ado-net-overview.md)</span></span>
