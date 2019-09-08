---
title: HOW TO：顯示 LINQ to SQL 命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
ms.openlocfilehash: 2f562dfd8f13c107249e697b77de7538df56fe2f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781955"
---
# <a name="how-to-display-linq-to-sql-commands"></a><span data-ttu-id="3e382-102">作法：顯示 LINQ to SQL 命令</span><span class="sxs-lookup"><span data-stu-id="3e382-102">How to: Display LINQ to SQL Commands</span></span>
<span data-ttu-id="3e382-103">使用 <xref:System.Data.Linq.DataContext.GetCommand%2A>，可以顯示 SQL 命令和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3e382-103">Use <xref:System.Data.Linq.DataContext.GetCommand%2A> to display SQL commands and other information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e382-104">範例</span><span class="sxs-lookup"><span data-stu-id="3e382-104">Example</span></span>  
 <span data-ttu-id="3e382-105">在下列範例中，主控台視窗會顯示查詢的輸出，後面依序接著產生的 SQL 命令、命令的型別，以及連接的型別。</span><span class="sxs-lookup"><span data-stu-id="3e382-105">In the following example, the console window displays the output from the query, followed by the SQL commands that are generated, the type of commands, and the type of connection.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 <span data-ttu-id="3e382-106">顯示的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="3e382-106">Output appears as follows:</span></span>  
  
```  
Customers from London:  
    Thomas Hardy  
    Victoria Ashworth  
    Elizabeth Brown  
    Ann Devon  
    Simon Crowther  
    Marie Bertrand  
    Hari Kumar  
    Dominique Perrier  
```  
  
```  
Command Text:  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
  
Command Type: Text  
  
Connection: System.Data.SqlClient.SqlConnection  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e382-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e382-107">See also</span></span>

- [<span data-ttu-id="3e382-108">偵錯支援</span><span class="sxs-lookup"><span data-stu-id="3e382-108">Debugging Support</span></span>](debugging-support.md)
