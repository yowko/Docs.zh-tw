---
title: 關聯 End 多重性
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cf9e6b5af0dc6a33af364901c631b4ce66fe0480
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153504"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="4406b-102">關聯 End 多重性</span><span class="sxs-lookup"><span data-stu-id="4406b-102">association end multiplicity</span></span>

<span data-ttu-id="4406b-103">*關聯 end 多重性*定義可以位於[關聯](association-type.md)某一端的[實體類型](entity-type.md)實例的數目。</span><span class="sxs-lookup"><span data-stu-id="4406b-103">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="4406b-104">關聯 End 多重性可以具有下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="4406b-104">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="4406b-105">一 (1)：表示關聯 End 只存在唯一的一個實體類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="4406b-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="4406b-106">零或一 (0..1)：表示關聯 End 具有零個或一個實體類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="4406b-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="4406b-107">許多 (\*) ：表示存在於關聯 end 的零個、一個或多個實體類型實例。</span><span class="sxs-lookup"><span data-stu-id="4406b-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="4406b-108">關聯通常以其關聯 End 多重性來區分。</span><span class="sxs-lookup"><span data-stu-id="4406b-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="4406b-109">例如，如果關聯的兩端具有多重性 1 (1) 和許多 (\*) ，則關聯稱為一對多關聯。</span><span class="sxs-lookup"><span data-stu-id="4406b-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="4406b-110">在下列範例中，`PublishedBy` 關聯集為一對多關聯 (一個發行者發行許多書籍，以及一本書籍由一個發行者發行)。</span><span class="sxs-lookup"><span data-stu-id="4406b-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="4406b-111">`WrittenBy` 關聯式多對多關聯 (一本書可以有多位作者，一位作者可以撰寫許多本書)。</span><span class="sxs-lookup"><span data-stu-id="4406b-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4406b-112">範例</span><span class="sxs-lookup"><span data-stu-id="4406b-112">Example</span></span>  

 <span data-ttu-id="4406b-113">下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="4406b-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="4406b-114">`PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="4406b-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="4406b-115">End 的多重性 `Publisher` 是一個 (1) 而 end 的多重性 `Book` 是許多 (\*) 。</span><span class="sxs-lookup"><span data-stu-id="4406b-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![包含三種實體類型的範例模型](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="4406b-117">ADO.NET Entity Framework 會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。</span><span class="sxs-lookup"><span data-stu-id="4406b-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="4406b-118">下列 CSDL 定義上圖中的 `PublishedBy` 關聯。</span><span class="sxs-lookup"><span data-stu-id="4406b-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="4406b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4406b-119">See also</span></span>

- [<span data-ttu-id="4406b-120">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="4406b-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="4406b-121">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="4406b-121">Entity Data Model</span></span>](entity-data-model.md)
