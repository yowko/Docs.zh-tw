---
title: 以方法為基礎的查詢語法範例：資料分割
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 6a1f4d13a75f787730d6155161296c3307b845f6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395349"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="b3c90-102">以方法為基礎的查詢語法範例：資料分割</span><span class="sxs-lookup"><span data-stu-id="b3c90-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="b3c90-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.Skip%2A>，並<xref:System.Linq.Enumerable.Take%2A>方法來查詢[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)透過查詢運算式語法。</span><span class="sxs-lookup"><span data-stu-id="b3c90-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="b3c90-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="b3c90-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b3c90-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="b3c90-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="b3c90-106">Skip</span><span class="sxs-lookup"><span data-stu-id="b3c90-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="b3c90-107">範例</span><span class="sxs-lookup"><span data-stu-id="b3c90-107">Example</span></span>  
 <span data-ttu-id="b3c90-108">下列範例會使用 <xref:System.Linq.Enumerable.Skip%2A> 方法來取得 Contact 資料表的所有連絡人 (前五位連絡人除外)。</span><span class="sxs-lookup"><span data-stu-id="b3c90-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="b3c90-109">範例</span><span class="sxs-lookup"><span data-stu-id="b3c90-109">Example</span></span>  
 <span data-ttu-id="b3c90-110">下列範例會使用 <xref:System.Linq.Enumerable.Skip%2A> 方法來取得西雅圖的所有地址 (前兩筆地址除外)。</span><span class="sxs-lookup"><span data-stu-id="b3c90-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="b3c90-111">Take</span><span class="sxs-lookup"><span data-stu-id="b3c90-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="b3c90-112">範例</span><span class="sxs-lookup"><span data-stu-id="b3c90-112">Example</span></span>  
 <span data-ttu-id="b3c90-113">下列範例會使用 <xref:System.Linq.Enumerable.Take%2A> 方法，單獨從 Contact 資料表中取得前五位連絡人。</span><span class="sxs-lookup"><span data-stu-id="b3c90-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="b3c90-114">範例</span><span class="sxs-lookup"><span data-stu-id="b3c90-114">Example</span></span>  
 <span data-ttu-id="b3c90-115">下列範例會使用 <xref:System.Linq.Enumerable.Take%2A> 方法來取得西雅圖的前三筆地址。</span><span class="sxs-lookup"><span data-stu-id="b3c90-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="b3c90-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3c90-116">See Also</span></span>  
 [<span data-ttu-id="b3c90-117">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="b3c90-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
