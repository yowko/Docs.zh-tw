---
title: "查詢運算式語法範例：導覽關聯性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 85e023eb07d247a032453d15b53ce94a89991806
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="f8658-102">查詢運算式語法範例：導覽關聯性</span><span class="sxs-lookup"><span data-stu-id="f8658-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="f8658-103">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 中的導覽屬性是用來尋找位於關聯兩端之實體的捷徑屬性。</span><span class="sxs-lookup"><span data-stu-id="f8658-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="f8658-104">導覽屬性可讓使用者在不同實體之間巡覽，或是透過關聯集從某個實體巡覽至相關的實體。</span><span class="sxs-lookup"><span data-stu-id="f8658-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="f8658-105">本主題提供的查詢運算式語法範例將說明如何透過 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢中的導覽屬性來巡覽關聯性。</span><span class="sxs-lookup"><span data-stu-id="f8658-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="f8658-106">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="f8658-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f8658-107">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="f8658-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="f8658-108">範例</span><span class="sxs-lookup"><span data-stu-id="f8658-108">Example</span></span>  
 <span data-ttu-id="f8658-109">下列範例會使用 <xref:System.Linq.Queryable.Select%2A> 方法來取得所有連絡人識別碼，以及姓氏為 "Zhou" 之每位連絡人總金額的總和。</span><span class="sxs-lookup"><span data-stu-id="f8658-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="f8658-110">`Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="f8658-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="f8658-111">`Sum` 方法會使用 `Contact.SalesOrderHeader` 導覽屬性來加總每位連絡人之所有訂單的應付總額。</span><span class="sxs-lookup"><span data-stu-id="f8658-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="f8658-112">範例</span><span class="sxs-lookup"><span data-stu-id="f8658-112">Example</span></span>  
 <span data-ttu-id="f8658-113">下列範例會取得姓氏為 "Zhou" 之連絡人的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="f8658-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="f8658-114">`Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="f8658-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="f8658-115">該連絡人的名稱和訂單會以匿名型別的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="f8658-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="f8658-116">範例</span><span class="sxs-lookup"><span data-stu-id="f8658-116">Example</span></span>  
 <span data-ttu-id="f8658-117">下列範例會使用 `SalesOrderHeader.Address` 和 `SalesOrderHeader.Contact` 導覽屬性來取得與每筆訂單相關聯之 `Address` 和 `Contact` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="f8658-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="f8658-118">到西雅圖城市之每一筆訂單的連絡人姓氏、街道地址、銷售訂單編號及應付總額會以匿名型別的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="f8658-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="f8658-119">範例</span><span class="sxs-lookup"><span data-stu-id="f8658-119">Example</span></span>  
 <span data-ttu-id="f8658-120">下列範例會使用 `Where` 方法來尋找在 2003 年 12 月 1 日之後下單的訂單，然後使用 `order.SalesOrderDetail` 導覽屬性來取得每筆訂單的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f8658-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="f8658-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8658-121">See Also</span></span>  
 [<span data-ttu-id="f8658-122">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="f8658-122">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
