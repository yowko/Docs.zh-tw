---
title: 以方法為基礎的查詢語法範例：資料分割
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 168fea5ffe6b8fbb4c08b95578beebbdee171c9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398483"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="ef662-102">以方法為基礎的查詢語法範例：分割</span><span class="sxs-lookup"><span data-stu-id="ef662-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="ef662-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.Skip%2A>、和<xref:System.Linq.Enumerable.Take%2A>方法，利用查詢運算式語法來查詢[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="ef662-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="ef662-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="ef662-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ef662-105">本主題中的範例會使用下列`using` / `Imports`語句：</span><span class="sxs-lookup"><span data-stu-id="ef662-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="ef662-106">Skip</span><span class="sxs-lookup"><span data-stu-id="ef662-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="ef662-107">範例</span><span class="sxs-lookup"><span data-stu-id="ef662-107">Example</span></span>  
 <span data-ttu-id="ef662-108">下列範例會使用 <xref:System.Linq.Enumerable.Skip%2A> 方法來取得 Contact 資料表的所有連絡人 (前五位連絡人除外)。</span><span class="sxs-lookup"><span data-stu-id="ef662-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="ef662-109">範例</span><span class="sxs-lookup"><span data-stu-id="ef662-109">Example</span></span>  
 <span data-ttu-id="ef662-110">下列範例會使用 <xref:System.Linq.Enumerable.Skip%2A> 方法來取得西雅圖的所有地址 (前兩筆地址除外)。</span><span class="sxs-lookup"><span data-stu-id="ef662-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="ef662-111">Take</span><span class="sxs-lookup"><span data-stu-id="ef662-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="ef662-112">範例</span><span class="sxs-lookup"><span data-stu-id="ef662-112">Example</span></span>  
 <span data-ttu-id="ef662-113">下列範例會使用 <xref:System.Linq.Enumerable.Take%2A> 方法，單獨從 Contact 資料表中取得前五位連絡人。</span><span class="sxs-lookup"><span data-stu-id="ef662-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="ef662-114">範例</span><span class="sxs-lookup"><span data-stu-id="ef662-114">Example</span></span>  
 <span data-ttu-id="ef662-115">下列範例會使用 <xref:System.Linq.Enumerable.Take%2A> 方法來取得西雅圖的前三筆地址。</span><span class="sxs-lookup"><span data-stu-id="ef662-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="ef662-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef662-116">See also</span></span>

- [<span data-ttu-id="ef662-117">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="ef662-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
