---
title: 多項大量複製作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: d447f09fcbfe108346b81a2bced44cf305e2844b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172667"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="bb7c2-102">多項大量複製作業</span><span class="sxs-lookup"><span data-stu-id="bb7c2-102">Multiple Bulk Copy Operations</span></span>

<span data-ttu-id="bb7c2-103">您可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別的單一執行個體，執行多項大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="bb7c2-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="bb7c2-104">如果作業參數在複本之間變更 (例如，目的地資料表的名稱) ，您必須在任何 **WriteToServer** 方法的後續呼叫之前更新這些參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bb7c2-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="bb7c2-105">除非已明確地變更，所有屬性值與之前指定執行個體上的大量複製作業維持相同。</span><span class="sxs-lookup"><span data-stu-id="bb7c2-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb7c2-106">比起對每項作業使用個別的執行個體，使用 <xref:System.Data.SqlClient.SqlBulkCopy> 的相同執行個體來執行多項大量複製作業通常更有效率。</span><span class="sxs-lookup"><span data-stu-id="bb7c2-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="bb7c2-107">如果您使用相同的 <xref:System.Data.SqlClient.SqlBulkCopy> 物件執行數項大量複製作業，並未限制來源或目標資訊在每項作業中是否相等或不同。</span><span class="sxs-lookup"><span data-stu-id="bb7c2-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="bb7c2-108">不過，當您每次寫入到伺服器時，必須確定資料行關聯資訊已正確設定。</span><span class="sxs-lookup"><span data-stu-id="bb7c2-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bb7c2-109">除非您已依照 [大量複製範例設定](bulk-copy-example-setup.md)所述建立工作資料表，否則此範例不會執行。</span><span class="sxs-lookup"><span data-stu-id="bb7c2-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="bb7c2-110">這個程式碼僅是為了示範使用 **SqlBulkCopy** 的語法而提供。</span><span class="sxs-lookup"><span data-stu-id="bb7c2-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="bb7c2-111">如果來源和目的地資料表位於相同的 SQL Server 執行個體，則使用 Transact-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。</span><span class="sxs-lookup"><span data-stu-id="bb7c2-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bb7c2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb7c2-112">See also</span></span>

- [<span data-ttu-id="bb7c2-113">在 SQL Server 中執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="bb7c2-113">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- <span data-ttu-id="bb7c2-114">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="bb7c2-114">[ADO.NET Overview](../ado-net-overview.md)</span></span>
