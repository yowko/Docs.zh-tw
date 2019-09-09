---
title: 關聯 End 多重性
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cdcf69e7118620b2f8febd02d7695d429bf8cc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786940"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="eb08a-102">關聯 End 多重性</span><span class="sxs-lookup"><span data-stu-id="eb08a-102">association end multiplicity</span></span>
<span data-ttu-id="eb08a-103">*關聯 end 多重性*會定義可位於[關聯](association-type.md)一端的[實體類型](entity-type.md)實例數目。</span><span class="sxs-lookup"><span data-stu-id="eb08a-103">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="eb08a-104">關聯 End 多重性可以具有下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="eb08a-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="eb08a-105">一（1）：表示只有一個實體類型實例存在於關聯 end。</span><span class="sxs-lookup"><span data-stu-id="eb08a-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="eb08a-106">零或一（0 ..1）：表示關聯 end 有零或一個實體類型實例。</span><span class="sxs-lookup"><span data-stu-id="eb08a-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="eb08a-107">many （\*）：表示關聯 end 有零個、一個或多個實體類型實例。</span><span class="sxs-lookup"><span data-stu-id="eb08a-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="eb08a-108">關聯通常以其關聯 End 多重性來區分。</span><span class="sxs-lookup"><span data-stu-id="eb08a-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="eb08a-109">例如，如果關聯的兩端具有多重性一（1）和多個（\*），則關聯稱為一對多關聯。</span><span class="sxs-lookup"><span data-stu-id="eb08a-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="eb08a-110">在下列範例中，`PublishedBy` 關聯集為一對多關聯 (一個發行者發行許多書籍，以及一本書籍由一個發行者發行)。</span><span class="sxs-lookup"><span data-stu-id="eb08a-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="eb08a-111">`WrittenBy` 關聯式多對多關聯 (一本書可以有多位作者，一位作者可以撰寫許多本書)。</span><span class="sxs-lookup"><span data-stu-id="eb08a-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb08a-112">範例</span><span class="sxs-lookup"><span data-stu-id="eb08a-112">Example</span></span>  
 <span data-ttu-id="eb08a-113">下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="eb08a-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="eb08a-114">`PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="eb08a-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="eb08a-115">`Publisher` End 的多重性是一（1），而`Book` end 的多重性則是多個（\*）。</span><span class="sxs-lookup"><span data-stu-id="eb08a-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![具有三個實體類型的範例模型](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="eb08a-117">ADO.NET Entity Framework 會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="eb08a-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="eb08a-118">下列 CSDL 定義上圖中的 `PublishedBy` 關聯。</span><span class="sxs-lookup"><span data-stu-id="eb08a-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="eb08a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb08a-119">See also</span></span>

- [<span data-ttu-id="eb08a-120">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="eb08a-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="eb08a-121">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="eb08a-121">Entity Data Model</span></span>](entity-data-model.md)
