---
title: HOW TO：直接執行 SQL 命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 3f28351a29915bebd698e00113bb05647d8412b4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781990"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="90901-102">HOW TO：直接執行 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="90901-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="90901-103">在假設使用 <xref:System.Data.Linq.DataContext> 集合的情況下，您可以使用 <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> 執行不會傳回物件的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="90901-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90901-104">範例</span><span class="sxs-lookup"><span data-stu-id="90901-104">Example</span></span>  
 <span data-ttu-id="90901-105">下列範例會讓 SQL Server 將 UnitPrice 增加 1.00。</span><span class="sxs-lookup"><span data-stu-id="90901-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="90901-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90901-106">See also</span></span>

- [<span data-ttu-id="90901-107">如何：直接執行 SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="90901-107">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="90901-108">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="90901-108">Communicating with the Database</span></span>](communicating-with-the-database.md)
