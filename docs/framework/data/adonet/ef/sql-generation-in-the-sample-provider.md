---
title: 範例提供者中的 SQL 產生
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 5aa6e31cfc93a4ae1871da63f466864b4ea6f5d9
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149714"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="240b2-102">範例提供者中的 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="240b2-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="240b2-103">[Entity Framework 範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)之 ADO.NET 資料提供者支援的新元件會示範[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="240b2-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="240b2-104">它會使用 SQL Server 2005 資料庫並且實作成 System.Data.SqlClient ADO.NET 2.0 資料提供者的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="240b2-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="240b2-105">此範例提供者的 SQL 產生模組 (位於 SQL Generation 資料夾底下，但 DmlSqlGenerator.cs 檔案除外) 會接受輸入 DbQueryCommandTree 並且產生單一 SQL SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="240b2-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="240b2-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="240b2-106">In This Section</span></span>  
 <span data-ttu-id="240b2-107">本節包括下列主題：</span><span class="sxs-lookup"><span data-stu-id="240b2-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="240b2-108">架構和設計</span><span class="sxs-lookup"><span data-stu-id="240b2-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="240b2-109">逐步解說：SQL 產生</span><span class="sxs-lookup"><span data-stu-id="240b2-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="240b2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="240b2-110">See Also</span></span>  
 [<span data-ttu-id="240b2-111">SQL 產生</span><span class="sxs-lookup"><span data-stu-id="240b2-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
