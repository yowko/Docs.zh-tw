---
title: 查詢運算式語法範例：巡覽關聯性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: a99d7d31ce23629bf7a0f390244c1fe67b4554e3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854404"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="30643-102">查詢運算式語法範例：巡覽關聯性</span><span class="sxs-lookup"><span data-stu-id="30643-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="30643-103">Entity Framework 中的導覽屬性是用來尋找位於關聯兩端之實體的快捷方式屬性。</span><span class="sxs-lookup"><span data-stu-id="30643-103">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="30643-104">導覽屬性可讓使用者在不同實體之間巡覽，或是透過關聯集從某個實體巡覽至相關的實體。</span><span class="sxs-lookup"><span data-stu-id="30643-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="30643-105">本主題提供查詢運算式語法中的範例，說明如何透過 LINQ to Entities 查詢中的導覽屬性來導覽關聯性。</span><span class="sxs-lookup"><span data-stu-id="30643-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="30643-106">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="30643-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="30643-107">本主題中的範例會使用下列`using` / `Imports`語句：</span><span class="sxs-lookup"><span data-stu-id="30643-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="30643-108">範例</span><span class="sxs-lookup"><span data-stu-id="30643-108">Example</span></span>  
 <span data-ttu-id="30643-109">下列範例會使用 <xref:System.Linq.Queryable.Select%2A> 方法來取得所有連絡人識別碼，以及姓氏為 "Zhou" 之每位連絡人總金額的總和。</span><span class="sxs-lookup"><span data-stu-id="30643-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="30643-110">`Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="30643-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="30643-111">`Sum` 方法會使用 `Contact.SalesOrderHeader` 導覽屬性來加總每位連絡人之所有訂單的應付總額。</span><span class="sxs-lookup"><span data-stu-id="30643-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="30643-112">範例</span><span class="sxs-lookup"><span data-stu-id="30643-112">Example</span></span>  
 <span data-ttu-id="30643-113">下列範例會取得姓氏為 "Zhou" 之連絡人的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="30643-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="30643-114">`Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="30643-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="30643-115">該連絡人的名稱和訂單會以匿名型別的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="30643-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="30643-116">範例</span><span class="sxs-lookup"><span data-stu-id="30643-116">Example</span></span>  
 <span data-ttu-id="30643-117">下列範例會使用 `SalesOrderHeader.Address` 和 `SalesOrderHeader.Contact` 導覽屬性來取得與每筆訂單相關聯之 `Address` 和 `Contact` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="30643-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="30643-118">到西雅圖城市之每一筆訂單的連絡人姓氏、街道地址、銷售訂單編號及應付總額會以匿名型別的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="30643-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="30643-119">範例</span><span class="sxs-lookup"><span data-stu-id="30643-119">Example</span></span>  
 <span data-ttu-id="30643-120">下列範例會使用 `Where` 方法來尋找在 2003 年 12 月 1 日之後下單的訂單，然後使用 `order.SalesOrderDetail` 導覽屬性來取得每筆訂單的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="30643-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="30643-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30643-121">See also</span></span>

- [<span data-ttu-id="30643-122">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="30643-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
