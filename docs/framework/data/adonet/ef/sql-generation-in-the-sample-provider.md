---
title: 範例提供者中的 SQL 產生
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 88223930b65ccec9d030104c62d8b4b2e77ddbe2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079410"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="2c380-102">範例提供者中的 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="2c380-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="2c380-103">[Entity Framework 範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)之 ADO.NET 資料提供者支援的新元件會示範[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2c380-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="2c380-104">它會使用 SQL Server 2005 資料庫並且實作成 System.Data.SqlClient ADO.NET 2.0 資料提供者的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="2c380-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="2c380-105">此範例提供者的 SQL 產生模組 (位於 SQL Generation 資料夾底下，但 DmlSqlGenerator.cs 檔案除外) 會接受輸入 DbQueryCommandTree 並且產生單一 SQL SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2c380-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c380-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="2c380-106">In This Section</span></span>  
 <span data-ttu-id="2c380-107">本節包括下列主題：</span><span class="sxs-lookup"><span data-stu-id="2c380-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="2c380-108">架構和設計</span><span class="sxs-lookup"><span data-stu-id="2c380-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="2c380-109">逐步解說：SQL 產生</span><span class="sxs-lookup"><span data-stu-id="2c380-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c380-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c380-110">See also</span></span>

- [<span data-ttu-id="2c380-111">SQL 產生</span><span class="sxs-lookup"><span data-stu-id="2c380-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
