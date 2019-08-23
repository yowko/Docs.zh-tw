---
title: 多項大量複製作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 8ee0fdbfc167c819942d8282aca56b7c5168fd87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946857"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="e23b2-102">多項大量複製作業</span><span class="sxs-lookup"><span data-stu-id="e23b2-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="e23b2-103">您可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別的單一執行個體，執行多項大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="e23b2-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="e23b2-104">如果作業參數在複本之間有所變更 (例如目的地資料表的名稱), 您必須在任何後續呼叫任何**WriteToServer**方法之前更新它們, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e23b2-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="e23b2-105">除非明確地變更，否則所有屬性值都會保持與給定執行個體之前次大量複製作業時的值相同。</span><span class="sxs-lookup"><span data-stu-id="e23b2-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e23b2-106">執行多項大量複製作業時，使用同一個 <xref:System.Data.SqlClient.SqlBulkCopy> 執行個體通常會比每個作業使用不同的執行個體更有效率。</span><span class="sxs-lookup"><span data-stu-id="e23b2-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="e23b2-107">使用相同的 <xref:System.Data.SqlClient.SqlBulkCopy> 物件執行數個大量複製作業時，對每個作業中的來源或目標資訊是否相等或不同並沒有限制。</span><span class="sxs-lookup"><span data-stu-id="e23b2-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="e23b2-108">但是，您必須確保每次寫入伺服器時，資料行關聯資訊的設定都正確。</span><span class="sxs-lookup"><span data-stu-id="e23b2-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e23b2-109">除非您已如[大量複製範例設定](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)中所述建立工作資料表, 否則此範例不會執行。</span><span class="sxs-lookup"><span data-stu-id="e23b2-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="e23b2-110">這段程式碼是為了示範只使用**SqlBulkCopy**的語法而提供。</span><span class="sxs-lookup"><span data-stu-id="e23b2-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="e23b2-111">如果來源及目的地資料表位於相同的 SQL Server 執行個體中，則使用 Transact-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。</span><span class="sxs-lookup"><span data-stu-id="e23b2-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e23b2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e23b2-112">See also</span></span>

- [<span data-ttu-id="e23b2-113">在 SQL Server 中執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="e23b2-113">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="e23b2-114">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e23b2-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
