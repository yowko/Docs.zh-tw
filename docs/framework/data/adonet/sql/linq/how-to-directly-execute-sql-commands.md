---
title: HOW TO：直接執行 SQL 命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: eeac6272f176ac8e780b72b0076d032ad9e8f108
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078898"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="2c93f-102">HOW TO：直接執行 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="2c93f-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="2c93f-103">在假設使用 <xref:System.Data.Linq.DataContext> 集合的情況下，您可以使用 <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> 執行不會傳回物件的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="2c93f-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c93f-104">範例</span><span class="sxs-lookup"><span data-stu-id="2c93f-104">Example</span></span>  
 <span data-ttu-id="2c93f-105">下列範例會讓 SQL Server 將 UnitPrice 增加 1.00。</span><span class="sxs-lookup"><span data-stu-id="2c93f-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2c93f-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c93f-106">See also</span></span>

- [<span data-ttu-id="2c93f-107">HOW TO：直接執行 SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="2c93f-107">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="2c93f-108">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="2c93f-108">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
