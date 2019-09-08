---
title: SQL Server 二進位和大量數值資料
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791680"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="3221c-102">SQL Server 二進位和大量數值資料</span><span class="sxs-lookup"><span data-stu-id="3221c-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="3221c-103">SQL Server 提供 `max` 規範，可擴充 `varchar`、`nvarchar` 和 `varbinary` 資料類型的儲存容量。</span><span class="sxs-lookup"><span data-stu-id="3221c-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="3221c-104">`varchar(max)`、 `nvarchar(max)`和`varbinary(max)`統稱為*大數值資料類型*。</span><span class="sxs-lookup"><span data-stu-id="3221c-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="3221c-105">您可以使用大數值資料型別來儲存最多可達 2^31-1 位元組的資料。</span><span class="sxs-lookup"><span data-stu-id="3221c-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="3221c-106">SQL Server 2008 導入了 FILESTREAM 屬性。這個屬性不是資料型別，而是可針對資料行定義的屬性，允許大數值資料儲存在檔案系統上，而非資料庫中。</span><span class="sxs-lookup"><span data-stu-id="3221c-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3221c-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="3221c-107">In This Section</span></span>  
 [<span data-ttu-id="3221c-108">在 ADO.NET 中修改大量數值 (max) 資料</span><span class="sxs-lookup"><span data-stu-id="3221c-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="3221c-109">說明如何使用大型值資料類型。</span><span class="sxs-lookup"><span data-stu-id="3221c-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="3221c-110">FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="3221c-110">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="3221c-111">說明如何使用儲存在 SQL Server 2008 中的大數值資料搭配 FILESTREAM 屬性。</span><span class="sxs-lookup"><span data-stu-id="3221c-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3221c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3221c-112">See also</span></span>

- [<span data-ttu-id="3221c-113">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3221c-113">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="3221c-114">ADO.NET 中的 SQL Server 資料作業</span><span class="sxs-lookup"><span data-stu-id="3221c-114">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="3221c-115">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="3221c-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="3221c-116">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="3221c-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
