---
title: 導覽屬性
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: eaf22ad4dd24b4bf046f14ccabd435a9ecd1776f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094380"
---
# <a name="navigation-property"></a><span data-ttu-id="5bb9c-102">導覽屬性</span><span class="sxs-lookup"><span data-stu-id="5bb9c-102">Navigation property</span></span>

<span data-ttu-id="5bb9c-103">*導覽屬性*是[實體類型](entity-type.md)上的選擇性屬性，可讓您從[關聯](association-type.md)[的一端導覽](association-end.md)至另一端。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="5bb9c-104">不同于其他[屬性](property.md)，導覽屬性不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="5bb9c-105">導覽屬性包含下列定義：</span><span class="sxs-lookup"><span data-stu-id="5bb9c-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="5bb9c-106">名稱。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-106">A name.</span></span> <span data-ttu-id="5bb9c-107">(必要)</span><span class="sxs-lookup"><span data-stu-id="5bb9c-107">(Required)</span></span>

- <span data-ttu-id="5bb9c-108">巡覽的關聯。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-108">The association that it navigates.</span></span> <span data-ttu-id="5bb9c-109">(必要)</span><span class="sxs-lookup"><span data-stu-id="5bb9c-109">(Required)</span></span>

- <span data-ttu-id="5bb9c-110">巡覽的關聯 End。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="5bb9c-111">(必要)</span><span class="sxs-lookup"><span data-stu-id="5bb9c-111">(Required)</span></span>

<span data-ttu-id="5bb9c-112">在關聯的兩端，這兩個實體類型的導覽屬性都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-112">Navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="5bb9c-113">如果您在關聯其中一個端點的實體類型上定義導覽屬性，就不必在關聯另一個端點的實體類型上定義導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="5bb9c-114">導覽屬性的資料類型取決於其遠端[關聯 end](association-end.md)的[多重性](association-end-multiplicity.md)。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="5bb9c-115">例如，假設 `OrdersNavProp` 實體類型上有一個導覽屬性 `Customer`，則該導覽屬性可巡覽 `Customer` 和 `Order` 之間一對多的關聯。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="5bb9c-116">因為導覽屬性的遠端關聯 end 具有「多（\*）」的多重性，所以其資料型別為集合（屬於 `Order`）。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="5bb9c-117">同樣地，如果 `CustomerNavProp` 實體類型上有一個導覽屬性 `Order`，其資料類型應為 `Customer`，因為遠端 End 的多重性是「一 (1)」。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="5bb9c-118">範例</span><span class="sxs-lookup"><span data-stu-id="5bb9c-118">Example</span></span>

<span data-ttu-id="5bb9c-119">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="5bb9c-120">`Publisher` 和 `Authors` 的導覽屬性是在 Book 實體類型上定義。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-120">The navigation properties `Publisher` and `Authors` are defined on the Book entity type.</span></span> <span data-ttu-id="5bb9c-121">導覽屬性 `Books` 在 Publisher 實體類型和 `Author` 實體類型上定義。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

![顯示具有三個實體類型之概念模型的圖表。](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="5bb9c-123">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的特定領域語言（DSL）來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="5bb9c-124">下列 CSDL 定義上圖所顯示的 `Book` 實體類型：</span><span class="sxs-lookup"><span data-stu-id="5bb9c-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="5bb9c-125">XML 屬性是用來傳達定義導覽屬性所需的資訊：屬性 `Name` 包含屬性的名稱，`Relationship` 包含它所導覽之關聯的名稱，而 `FromRole` 和 `ToRole` 包含關聯的端點。</span><span class="sxs-lookup"><span data-stu-id="5bb9c-125">XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bb9c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bb9c-126">See also</span></span>

- [<span data-ttu-id="5bb9c-127">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="5bb9c-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="5bb9c-128">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="5bb9c-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="5bb9c-129">關聯性、導覽屬性和外鍵</span><span class="sxs-lookup"><span data-stu-id="5bb9c-129">Relationships, navigation properties, and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
