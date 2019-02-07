---
title: 以方法為基礎的查詢語法範例：Projection
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 287be3648fa6c21df836fc09d197e1a23e83eec8
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827054"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="a0ab9-102">以方法為基礎的查詢語法範例：Projection</span><span class="sxs-lookup"><span data-stu-id="a0ab9-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="a0ab9-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.Select%2A>並<xref:System.Linq.Enumerable.SelectMany%2A>方法來查詢[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)使用以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="a0ab9-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="a0ab9-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="a0ab9-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a0ab9-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="a0ab9-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="a0ab9-106">選用版</span><span class="sxs-lookup"><span data-stu-id="a0ab9-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="a0ab9-107">範例</span><span class="sxs-lookup"><span data-stu-id="a0ab9-107">Example</span></span>  
 <span data-ttu-id="a0ab9-108">下列範例會使用 <xref:System.Linq.Queryable.Select%2A> 方法，將 `Product.Name` 和 `Product.ProductID` 屬性投影到匿名型別的序列中。</span><span class="sxs-lookup"><span data-stu-id="a0ab9-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="a0ab9-109">範例</span><span class="sxs-lookup"><span data-stu-id="a0ab9-109">Example</span></span>  
 <span data-ttu-id="a0ab9-110">下列範例會使用 <xref:System.Linq.Enumerable.Select%2A> 方法來單獨傳回產品名稱的序列。</span><span class="sxs-lookup"><span data-stu-id="a0ab9-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="a0ab9-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="a0ab9-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="a0ab9-112">範例</span><span class="sxs-lookup"><span data-stu-id="a0ab9-112">Example</span></span>  
 <span data-ttu-id="a0ab9-113">下列範例會使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來選取 `TotalDue` 少於 500.00 的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="a0ab9-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="a0ab9-114">範例</span><span class="sxs-lookup"><span data-stu-id="a0ab9-114">Example</span></span>  
 <span data-ttu-id="a0ab9-115">下列範例會使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來選取在 2002 年 10 月 1 日或之後下單的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="a0ab9-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="a0ab9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0ab9-116">See also</span></span>
- [<span data-ttu-id="a0ab9-117">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="a0ab9-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
