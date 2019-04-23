---
title: HOW TO：建立資料服務，使用反映提供者 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 233b17de17b7f50547b2f4fbf6a543d7258183cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517092"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="79e93-102">HOW TO：建立資料服務，使用反映提供者 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="79e93-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="79e93-103">可讓您定義以任意類別為基礎的資料模型，只要將這些類別公開為實作 <xref:System.Linq.IQueryable%601> 介面的物件即可。</span><span class="sxs-lookup"><span data-stu-id="79e93-103">enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="79e93-104">如需詳細資訊，請參閱 <<c0> [ 資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="79e93-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79e93-105">範例</span><span class="sxs-lookup"><span data-stu-id="79e93-105">Example</span></span>  
 <span data-ttu-id="79e93-106">下列範例定義包含 `Orders` 及 `Items` 的資料模型。</span><span class="sxs-lookup"><span data-stu-id="79e93-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="79e93-107">實體容器類別 `OrderItemData` 具有兩個會傳回 <xref:System.Linq.IQueryable%601> 介面的公開方法。</span><span class="sxs-lookup"><span data-stu-id="79e93-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="79e93-108">這些介面是 `Orders` 和 `Items` 實體類型的實體集。</span><span class="sxs-lookup"><span data-stu-id="79e93-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="79e93-109">`Order` 可以包括多個 `Items`，因此 `Orders` 實體類型具有一個 `Items` 導覽屬性，該屬性會傳回 `Items` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="79e93-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="79e93-110">`OrderItemData` 實體容器類別是 <xref:System.Data.Services.DataService%601> 類別的泛型型別，`OrderItems` 資料服務即衍生於此。</span><span class="sxs-lookup"><span data-stu-id="79e93-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79e93-111">由於本範例示範的是記憶體內部資料提供者，在目前物件執行個體外部所進行的變更將無法持續，因此實作 <xref:System.Data.Services.IUpdatable> 介面並不會產生任何益處。</span><span class="sxs-lookup"><span data-stu-id="79e93-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="79e93-112">如需範例，可實作<xref:System.Data.Services.IUpdatable>介面，請參閱[How to:建立使用 LINQ to SQL 資料來源的資料服務](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="79e93-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="79e93-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79e93-113">See also</span></span>

- [<span data-ttu-id="79e93-114">如何：建立使用 LINQ to SQL 資料來源的資料服務</span><span class="sxs-lookup"><span data-stu-id="79e93-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="79e93-115">資料服務提供者</span><span class="sxs-lookup"><span data-stu-id="79e93-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="79e93-116">如何：建立使用 ADO.NET Entity Framework 資料來源的資料服務</span><span class="sxs-lookup"><span data-stu-id="79e93-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
