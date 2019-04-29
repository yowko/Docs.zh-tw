---
title: 導覽屬性-ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: b57ecf9329aa9ea8afc07507613c9e3961bfd0a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772235"
---
# <a name="navigation-property"></a><span data-ttu-id="fb925-102">導覽屬性</span><span class="sxs-lookup"><span data-stu-id="fb925-102">Navigation property</span></span>

<span data-ttu-id="fb925-103">A*導覽屬性*上為選擇性屬性[實體型別](entity-type.md)，可讓不同的瀏覽[結束](association-end.md)的[關聯](association-type.md)至另一端。</span><span class="sxs-lookup"><span data-stu-id="fb925-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="fb925-104">不同於其他[屬性](property.md)，導覽屬性不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="fb925-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="fb925-105">導覽屬性包含下列定義：</span><span class="sxs-lookup"><span data-stu-id="fb925-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="fb925-106">名稱。</span><span class="sxs-lookup"><span data-stu-id="fb925-106">A name.</span></span> <span data-ttu-id="fb925-107">(必要項)</span><span class="sxs-lookup"><span data-stu-id="fb925-107">(Required)</span></span>

- <span data-ttu-id="fb925-108">巡覽的關聯。</span><span class="sxs-lookup"><span data-stu-id="fb925-108">The association that it navigates.</span></span> <span data-ttu-id="fb925-109">(必要項)</span><span class="sxs-lookup"><span data-stu-id="fb925-109">(Required)</span></span>

- <span data-ttu-id="fb925-110">巡覽的關聯 End。</span><span class="sxs-lookup"><span data-stu-id="fb925-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="fb925-111">(必要項)</span><span class="sxs-lookup"><span data-stu-id="fb925-111">(Required)</span></span>

<span data-ttu-id="fb925-112">請注意，在關聯各端點的實體類型上，導覽屬性是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="fb925-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="fb925-113">如果您在關聯其中一個端點的實體類型上定義導覽屬性，就不必在關聯另一個端點的實體類型上定義導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="fb925-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="fb925-114">導覽屬性的資料類型由[多重性](association-end-multiplicity.md)的其遠端[關聯 end](association-end.md)。</span><span class="sxs-lookup"><span data-stu-id="fb925-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="fb925-115">例如，假設 `OrdersNavProp` 實體類型上有一個導覽屬性 `Customer`，則該導覽屬性可巡覽 `Customer` 和 `Order` 之間一對多的關聯。</span><span class="sxs-lookup"><span data-stu-id="fb925-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="fb925-116">因為導覽屬性的遠端關聯 end 具有多重性為許多 (\*)，其資料型別是集合 (的`Order`)。</span><span class="sxs-lookup"><span data-stu-id="fb925-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="fb925-117">同樣地，如果 `CustomerNavProp` 實體類型上有一個導覽屬性 `Order`，其資料類型應為 `Customer`，因為遠端 End 的多重性是「一 (1)」。</span><span class="sxs-lookup"><span data-stu-id="fb925-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="fb925-118">範例</span><span class="sxs-lookup"><span data-stu-id="fb925-118">Example</span></span>

<span data-ttu-id="fb925-119">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="fb925-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="fb925-120">導覽屬性、`Publisher` 和 `Authors` 均在 Book 實體類型上定義。</span><span class="sxs-lookup"><span data-stu-id="fb925-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="fb925-121">導覽屬性 `Books` 在 Publisher 實體類型和 `Author` 實體類型上定義。</span><span class="sxs-lookup"><span data-stu-id="fb925-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

 ![顯示具有三種實體類型的概念模型的圖表。](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="fb925-123">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](./ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="fb925-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="fb925-124">下列 CSDL 定義上圖所顯示的 `Book` 實體類型：</span><span class="sxs-lookup"><span data-stu-id="fb925-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="fb925-125">請注意，XML 屬性用來傳達定義導覽屬性所需的資訊：屬性`Name`包含屬性的名稱`Relationship`包含巡覽的關聯的名稱並`FromRole`和`ToRole`包含關聯的兩端。</span><span class="sxs-lookup"><span data-stu-id="fb925-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb925-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb925-126">See also</span></span>

- [<span data-ttu-id="fb925-127">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="fb925-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="fb925-128">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="fb925-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="fb925-129">關聯性、 導覽屬性和外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="fb925-129">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
