---
title: 使用命令修改資料
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: f2e3d162bfbdcb79cfecefa4ddc8e6a0dc46ee3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102449"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="5faa7-102">使用命令修改資料</span><span class="sxs-lookup"><span data-stu-id="5faa7-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="5faa7-103">您可以使用 .NET Framework 資料提供者來執行預存程序或資料定義語言陳述式 (例如 CREATE TABLE 和 ALTER COLUMN)，以執行資料庫或目錄的結構描述管理。</span><span class="sxs-lookup"><span data-stu-id="5faa7-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="5faa7-104">這些命令不會傳回資料列像查詢一樣，因此**命令**物件提供**ExecuteNonQuery**加以處理。</span><span class="sxs-lookup"><span data-stu-id="5faa7-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="5faa7-105">除了使用**ExecuteNonQuery**修改結構描述，您也可以使用這個方法來處理 SQL 陳述式所修改的資料，但是，不傳回資料列，例如插入、 更新和刪除。</span><span class="sxs-lookup"><span data-stu-id="5faa7-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="5faa7-106">雖然不會傳回資料列**ExecuteNonQuery**方法、 輸入和輸出參數和傳回值可以傳遞和傳回透過**參數**集合**命令**物件。</span><span class="sxs-lookup"><span data-stu-id="5faa7-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5faa7-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="5faa7-107">In This Section</span></span>  
 [<span data-ttu-id="5faa7-108">更新資料來源中的資料</span><span class="sxs-lookup"><span data-stu-id="5faa7-108">Updating Data in a Data Source</span></span>](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 <span data-ttu-id="5faa7-109">說明如何執行修改資料庫資料的命令或預存程序。</span><span class="sxs-lookup"><span data-stu-id="5faa7-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="5faa7-110">執行目錄作業</span><span class="sxs-lookup"><span data-stu-id="5faa7-110">Performing Catalog Operations</span></span>](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 <span data-ttu-id="5faa7-111">說明如何執行修改資料庫結構描述的命令。</span><span class="sxs-lookup"><span data-stu-id="5faa7-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5faa7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5faa7-112">See also</span></span>

- [<span data-ttu-id="5faa7-113">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="5faa7-113">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="5faa7-114">命令和參數</span><span class="sxs-lookup"><span data-stu-id="5faa7-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="5faa7-115">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="5faa7-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
