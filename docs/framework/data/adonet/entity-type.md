---
title: Entity Type - 實體類型
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: efd3ea0972148e885d4b22b49040640539bb28cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795127"
---
# <a name="entity-type"></a><span data-ttu-id="ee99d-102">Entity Type - 實體類型</span><span class="sxs-lookup"><span data-stu-id="ee99d-102">entity type</span></span>
<span data-ttu-id="ee99d-103">*實體類型*是使用實體資料模型（EDM）描述資料結構的基本建立區塊。</span><span class="sxs-lookup"><span data-stu-id="ee99d-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="ee99d-104">在概念模型中，實體類型代表最上層概念的結構，例如客戶或訂單。</span><span class="sxs-lookup"><span data-stu-id="ee99d-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="ee99d-105">實體類型是實體類型執行個體的範本。</span><span class="sxs-lookup"><span data-stu-id="ee99d-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="ee99d-106">每個範本包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ee99d-106">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="ee99d-107">唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="ee99d-107">A unique name.</span></span> <span data-ttu-id="ee99d-108">(必要項。)</span><span class="sxs-lookup"><span data-stu-id="ee99d-108">(Required.)</span></span>  
  
- <span data-ttu-id="ee99d-109">由一個或多個屬性所定義的[實體索引鍵](entity-key.md)。</span><span class="sxs-lookup"><span data-stu-id="ee99d-109">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="ee99d-110">(必要項。)</span><span class="sxs-lookup"><span data-stu-id="ee99d-110">(Required.)</span></span>  
  
- <span data-ttu-id="ee99d-111">[屬性](property.md)形式的資料。</span><span class="sxs-lookup"><span data-stu-id="ee99d-111">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="ee99d-112">(選擇性。)</span><span class="sxs-lookup"><span data-stu-id="ee99d-112">(Optional.)</span></span>  
  
- <span data-ttu-id="ee99d-113">允許從[關聯](association-type.md)[的一端導覽](association-end.md)至另一端的[導覽屬性](navigation-property.md)。</span><span class="sxs-lookup"><span data-stu-id="ee99d-113">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="ee99d-114">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="ee99d-114">(Optional)</span></span>  
  
 <span data-ttu-id="ee99d-115">在應用程式中，實體類型的執行個體代表特定的物件 (例如特定的客戶或訂單)。</span><span class="sxs-lookup"><span data-stu-id="ee99d-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="ee99d-116">實體類型的每個實例在[實體集](entity-set.md)內都必須有唯一的[實體索引鍵](entity-key.md)。</span><span class="sxs-lookup"><span data-stu-id="ee99d-116">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="ee99d-117">如果兩個實體類型執行個體屬於相同類型，而且索引鍵的值也相同，則會將這兩個執行個體視為相等。</span><span class="sxs-lookup"><span data-stu-id="ee99d-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee99d-118">範例</span><span class="sxs-lookup"><span data-stu-id="ee99d-118">Example</span></span>  
 <span data-ttu-id="ee99d-119">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型：</span><span class="sxs-lookup"><span data-stu-id="ee99d-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![具有三個實體類型的範例模型](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="ee99d-121">請注意，構成實體索引鍵的每個實體類型屬性皆加註「(索引鍵)」。</span><span class="sxs-lookup"><span data-stu-id="ee99d-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="ee99d-122">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="ee99d-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ee99d-123">下列 CSDL 定義上圖所顯示的 `Book` 實體類型：</span><span class="sxs-lookup"><span data-stu-id="ee99d-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ee99d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee99d-124">See also</span></span>

- [<span data-ttu-id="ee99d-125">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="ee99d-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="ee99d-126">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="ee99d-126">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="ee99d-127">facet</span><span class="sxs-lookup"><span data-stu-id="ee99d-127">facet</span></span>](facet.md)
