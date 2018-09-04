---
title: 查詢運算式語法範例：資料分割
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: e5539d0052d5d5847475b1902b5fc74566883057
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536660"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="7609f-102">查詢運算式語法範例：資料分割</span><span class="sxs-lookup"><span data-stu-id="7609f-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="7609f-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.Skip%2A>並<xref:System.Linq.Enumerable.Take%2A>方法來查詢[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)透過查詢運算式語法。</span><span class="sxs-lookup"><span data-stu-id="7609f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="7609f-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="7609f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7609f-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="7609f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="7609f-106">Skip</span><span class="sxs-lookup"><span data-stu-id="7609f-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="7609f-107">範例</span><span class="sxs-lookup"><span data-stu-id="7609f-107">Example</span></span>  
 <span data-ttu-id="7609f-108">下列範例會使用 <xref:System.Linq.Enumerable.Skip%2A> 方法來取得西雅圖的所有地址 (前兩筆地址除外)。</span><span class="sxs-lookup"><span data-stu-id="7609f-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="7609f-109">Take</span><span class="sxs-lookup"><span data-stu-id="7609f-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="7609f-110">範例</span><span class="sxs-lookup"><span data-stu-id="7609f-110">Example</span></span>  
 <span data-ttu-id="7609f-111">下列範例會使用 <xref:System.Linq.Enumerable.Take%2A> 方法來取得西雅圖的前三筆地址。</span><span class="sxs-lookup"><span data-stu-id="7609f-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="7609f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7609f-112">See Also</span></span>  
 [<span data-ttu-id="7609f-113">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="7609f-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
