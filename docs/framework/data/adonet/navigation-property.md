---
title: 導覽屬性
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 09c0e5e5dbc7b2be89e044c4d111fdd65fada7c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662175"
---
# <a name="navigation-property"></a><span data-ttu-id="80e22-102">導覽屬性</span><span class="sxs-lookup"><span data-stu-id="80e22-102">navigation property</span></span>
<span data-ttu-id="80e22-103">A*導覽屬性*上為選擇性屬性[實體型別](../../../../docs/framework/data/adonet/entity-type.md)，可讓不同的瀏覽[結束](../../../../docs/framework/data/adonet/association-end.md)的[關聯](../../../../docs/framework/data/adonet/association-type.md)至另一端。</span><span class="sxs-lookup"><span data-stu-id="80e22-103">A *navigation property* is an optional property on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that allows for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="80e22-104">不同於其他[屬性](../../../../docs/framework/data/adonet/property.md)，導覽屬性不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="80e22-104">Unlike other [properties](../../../../docs/framework/data/adonet/property.md), navigation properties do not carry data.</span></span>  
  
 <span data-ttu-id="80e22-105">導覽屬性包含下列定義：</span><span class="sxs-lookup"><span data-stu-id="80e22-105">A navigation property definition includes the following:</span></span>  
  
-   <span data-ttu-id="80e22-106">名稱。</span><span class="sxs-lookup"><span data-stu-id="80e22-106">A name.</span></span> <span data-ttu-id="80e22-107">(必要項)</span><span class="sxs-lookup"><span data-stu-id="80e22-107">(Required)</span></span>  
  
-   <span data-ttu-id="80e22-108">巡覽的關聯。</span><span class="sxs-lookup"><span data-stu-id="80e22-108">The association that it navigates.</span></span> <span data-ttu-id="80e22-109">(必要項)</span><span class="sxs-lookup"><span data-stu-id="80e22-109">(Required)</span></span>  
  
-   <span data-ttu-id="80e22-110">巡覽的關聯 End。</span><span class="sxs-lookup"><span data-stu-id="80e22-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="80e22-111">(必要項)</span><span class="sxs-lookup"><span data-stu-id="80e22-111">(Required)</span></span>  
  
 <span data-ttu-id="80e22-112">請注意，在關聯各端點的實體類型上，導覽屬性是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="80e22-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="80e22-113">如果您在關聯其中一個端點的實體類型上定義導覽屬性，就不必在關聯另一個端點的實體類型上定義導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="80e22-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>  
  
 <span data-ttu-id="80e22-114">導覽屬性的資料類型由[多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md)的其遠端[關聯 end](../../../../docs/framework/data/adonet/association-end.md)。</span><span class="sxs-lookup"><span data-stu-id="80e22-114">The data type of a navigation property is determined by the [multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) of its remote [association end](../../../../docs/framework/data/adonet/association-end.md).</span></span> <span data-ttu-id="80e22-115">例如，假設 `OrdersNavProp` 實體類型上有一個導覽屬性 `Customer`，則該導覽屬性可巡覽 `Customer` 和 `Order` 之間一對多的關聯。</span><span class="sxs-lookup"><span data-stu-id="80e22-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="80e22-116">因為導覽屬性的遠端關聯 End 具有「多 (\*)」多重性，因此其資料型別是 (`Order` 的) 集合。</span><span class="sxs-lookup"><span data-stu-id="80e22-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="80e22-117">同樣地，如果 `CustomerNavProp` 實體類型上有一個導覽屬性 `Order`，其資料類型應為 `Customer`，因為遠端 End 的多重性是「一 (1)」。</span><span class="sxs-lookup"><span data-stu-id="80e22-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80e22-118">範例</span><span class="sxs-lookup"><span data-stu-id="80e22-118">Example</span></span>  
 <span data-ttu-id="80e22-119">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="80e22-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="80e22-120">導覽屬性、`Publisher` 和 `Authors` 均在 Book 實體類型上定義。</span><span class="sxs-lookup"><span data-stu-id="80e22-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="80e22-121">導覽屬性 `Books` 在 Publisher 實體類型和 `Author` 實體類型上定義。</span><span class="sxs-lookup"><span data-stu-id="80e22-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>  
  
 <span data-ttu-id="80e22-122">![具有導覽屬性的模型](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span><span class="sxs-lookup"><span data-stu-id="80e22-122">![Model with Navigation Properties](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span></span>  
  
 <span data-ttu-id="80e22-123">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="80e22-123">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="80e22-124">下列 CSDL 定義上圖所顯示的 `Book` 實體類型：</span><span class="sxs-lookup"><span data-stu-id="80e22-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="80e22-125">請注意，XML 屬性用來傳達定義導覽屬性所需的資訊：屬性`Name`包含屬性的名稱`Relationship`包含巡覽的關聯的名稱並`FromRole`和`ToRole`包含關聯的兩端。</span><span class="sxs-lookup"><span data-stu-id="80e22-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e22-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e22-126">See also</span></span>
- [<span data-ttu-id="80e22-127">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="80e22-127">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="80e22-128">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="80e22-128">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
