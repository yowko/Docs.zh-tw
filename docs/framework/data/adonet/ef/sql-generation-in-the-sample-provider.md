---
title: 範例提供者中的 SQL 產生
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: d0e058cdc4dd3f7a1a04ab6eea5acf4d3deabb89
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248502"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="90485-102">範例提供者中的 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="90485-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="90485-103">[Entity Framework 範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)會示範支援的[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]ADO.NET 資料提供者的新元件。</span><span class="sxs-lookup"><span data-stu-id="90485-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="90485-104">它會使用 SQL Server 2005 資料庫並且實作成 System.Data.SqlClient ADO.NET 2.0 資料提供者的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="90485-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="90485-105">此範例提供者的 SQL 產生模組 (位於 SQL Generation 資料夾底下，但 DmlSqlGenerator.cs 檔案除外) 會接受輸入 DbQueryCommandTree 並且產生單一 SQL SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="90485-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90485-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="90485-106">In This Section</span></span>  
 <span data-ttu-id="90485-107">本節包括下列主題：</span><span class="sxs-lookup"><span data-stu-id="90485-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="90485-108">架構和設計</span><span class="sxs-lookup"><span data-stu-id="90485-108">Architecture and Design</span></span>](architecture-and-design.md)  
  
 [<span data-ttu-id="90485-109">逐步解說：SQL 產生</span><span class="sxs-lookup"><span data-stu-id="90485-109">Walkthrough: SQL Generation</span></span>](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="90485-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90485-110">See also</span></span>

- [<span data-ttu-id="90485-111">SQL 產生</span><span class="sxs-lookup"><span data-stu-id="90485-111">SQL Generation</span></span>](sql-generation.md)
