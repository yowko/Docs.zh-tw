---
title: 以方法為基礎的查詢語法範例：巡覽關聯性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: 56ae913da3ca06a08b5bacc5ce225597980467a6
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539465"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="8a832-102">以方法為基礎的查詢語法範例：巡覽關聯性</span><span class="sxs-lookup"><span data-stu-id="8a832-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="8a832-103">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 中的導覽屬性是用來尋找位於關聯兩端之實體的捷徑屬性。</span><span class="sxs-lookup"><span data-stu-id="8a832-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="8a832-104">導覽屬性可讓使用者在不同實體之間巡覽，或是透過關聯集從某個實體巡覽至相關的實體。</span><span class="sxs-lookup"><span data-stu-id="8a832-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="8a832-105">本主題提供以方法為基礎的查詢語法範例，示範如何巡覽關聯性，透過在 LINQ to Entities 查詢的導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="8a832-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="8a832-106">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="8a832-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8a832-107">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="8a832-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="8a832-108">範例</span><span class="sxs-lookup"><span data-stu-id="8a832-108">Example</span></span>  
 <span data-ttu-id="8a832-109">下列以方法為基礎的查詢語法範例會使用 <xref:System.Linq.Queryable.SelectMany%2A> 方法取得姓氏為 "Zhou" 之連絡人的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="8a832-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="8a832-110">`Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="8a832-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="8a832-111">範例</span><span class="sxs-lookup"><span data-stu-id="8a832-111">Example</span></span>  
 <span data-ttu-id="8a832-112">下列以方法為基礎的查詢語法範例會使用 <xref:System.Linq.Queryable.Select%2A> 方法來取得所有連絡人識別碼以及姓氏為 "Zhou" 之每位連絡人的應付總額。</span><span class="sxs-lookup"><span data-stu-id="8a832-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="8a832-113">`Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="8a832-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="8a832-114">`Sum` 方法會使用 `Contact.SalesOrderHeader` 導覽屬性來加總每位連絡人之所有訂單的應付總額。</span><span class="sxs-lookup"><span data-stu-id="8a832-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="8a832-115">範例</span><span class="sxs-lookup"><span data-stu-id="8a832-115">Example</span></span>  
 <span data-ttu-id="8a832-116">下列以方法為基礎之查詢語法的範例會取得姓氏為 "Zhou" 之連絡人的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="8a832-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="8a832-117">`Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="8a832-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="8a832-118">該連絡人的名稱和訂單會以匿名型別的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="8a832-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="8a832-119">範例</span><span class="sxs-lookup"><span data-stu-id="8a832-119">Example</span></span>  
 <span data-ttu-id="8a832-120">下列範例會使用 `SalesOrderHeader.Address` 和 `SalesOrderHeader.Contact` 導覽屬性來取得與每筆訂單相關聯之 `Address` 和 `Contact` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="8a832-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="8a832-121">到西雅圖城市之每一筆訂單的連絡人姓氏、街道地址、銷售訂單編號及應付總額會以匿名型別的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="8a832-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="8a832-122">範例</span><span class="sxs-lookup"><span data-stu-id="8a832-122">Example</span></span>  
 <span data-ttu-id="8a832-123">下列範例會使用 `Where` 方法來尋找在 2003 年 12 月 1 日之後下單的訂單，然後使用 `order.SalesOrderDetail` 導覽屬性來取得每筆訂單的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8a832-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="8a832-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a832-124">See also</span></span>

- [<span data-ttu-id="8a832-125">關聯性、 導覽屬性和外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="8a832-125">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
- [<span data-ttu-id="8a832-126">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="8a832-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
