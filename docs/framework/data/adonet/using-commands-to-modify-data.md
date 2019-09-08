---
title: 使用命令修改資料
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 34c73549f18cd4bebb8caf842b252828b7f0a185
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780569"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="04bc6-102">使用命令修改資料</span><span class="sxs-lookup"><span data-stu-id="04bc6-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="04bc6-103">您可以使用 .NET Framework 資料提供者來執行預存程序或資料定義語言陳述式 (例如 CREATE TABLE 和 ALTER COLUMN)，以執行資料庫或目錄的結構描述管理。</span><span class="sxs-lookup"><span data-stu-id="04bc6-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="04bc6-104">這些命令不會以查詢的形式傳回資料列，因此**Command**物件會提供**ExecuteNonQuery**來處理它們。</span><span class="sxs-lookup"><span data-stu-id="04bc6-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="04bc6-105">除了使用**ExecuteNonQuery**來修改架構，您也可以使用這個方法來處理修改資料的 SQL 語句，但不會傳回資料列，例如 INSERT、UPDATE 和 DELETE。</span><span class="sxs-lookup"><span data-stu-id="04bc6-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="04bc6-106">雖然**ExecuteNonQuery**方法不會傳回資料列，但輸入和輸出參數和傳回值可透過**Command**物件的**parameters**集合來傳遞和傳回。</span><span class="sxs-lookup"><span data-stu-id="04bc6-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04bc6-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="04bc6-107">In This Section</span></span>  
 [<span data-ttu-id="04bc6-108">更新資料來源中的資料</span><span class="sxs-lookup"><span data-stu-id="04bc6-108">Updating Data in a Data Source</span></span>](updating-data-in-a-data-source.md)  
 <span data-ttu-id="04bc6-109">說明如何執行修改資料庫資料的命令或預存程序。</span><span class="sxs-lookup"><span data-stu-id="04bc6-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="04bc6-110">執行目錄作業</span><span class="sxs-lookup"><span data-stu-id="04bc6-110">Performing Catalog Operations</span></span>](performing-catalog-operations.md)  
 <span data-ttu-id="04bc6-111">說明如何執行修改資料庫結構描述的命令。</span><span class="sxs-lookup"><span data-stu-id="04bc6-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bc6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04bc6-112">See also</span></span>

- [<span data-ttu-id="04bc6-113">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="04bc6-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="04bc6-114">命令和參數</span><span class="sxs-lookup"><span data-stu-id="04bc6-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="04bc6-115">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="04bc6-115">ADO.NET Overview</span></span>](ado-net-overview.md)
