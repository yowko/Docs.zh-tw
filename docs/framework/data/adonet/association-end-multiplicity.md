---
title: "關聯 End 多重性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0d66c141b83402b011fdebbb04c0b2a9adc5ec29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="81789-102">關聯 End 多重性</span><span class="sxs-lookup"><span data-stu-id="81789-102">association end multiplicity</span></span>
<span data-ttu-id="81789-103">*關聯 end 多重性*定義數目[實體類型](../../../../docs/framework/data/adonet/entity-type.md)可能是其中一端的執行個體[關聯](../../../../docs/framework/data/adonet/association-type.md)。</span><span class="sxs-lookup"><span data-stu-id="81789-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="81789-104">關聯 End 多重性可以具有下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="81789-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="81789-105">一 (1)：表示關聯 End 只存在唯一的一個實體類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="81789-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="81789-106">零或一 (0..1)：表示關聯 End 具有零個或一個實體類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="81789-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="81789-107">許多 (*)：表示關聯 End 具有零個、一個或多個實體類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="81789-107">many (*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="81789-108">關聯通常以其關聯 End 多重性來區分。</span><span class="sxs-lookup"><span data-stu-id="81789-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="81789-109">例如，如果關聯的 End 具有多重性一 (0) 和許多 (*)，則該關聯稱為一對多關聯。</span><span class="sxs-lookup"><span data-stu-id="81789-109">For example, if the ends of an association have multiplicities one (1) and many (*), the association is called a one-to-many association.</span></span> <span data-ttu-id="81789-110">在下列範例中，`PublishedBy` 關聯集為一對多關聯 (一個發行者發行許多書籍，以及一本書籍由一個發行者發行)。</span><span class="sxs-lookup"><span data-stu-id="81789-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="81789-111">`WrittenBy` 關聯式多對多關聯 (一本書可以有多位作者，一位作者可以撰寫許多本書)。</span><span class="sxs-lookup"><span data-stu-id="81789-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81789-112">範例</span><span class="sxs-lookup"><span data-stu-id="81789-112">Example</span></span>  
 <span data-ttu-id="81789-113">下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="81789-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="81789-114">`PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="81789-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="81789-115">`Publisher` 端的多重性是一 (1)，而 `Book` 端的多重性則是多個 (*)。</span><span class="sxs-lookup"><span data-stu-id="81789-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (*).</span></span>  
  
 <span data-ttu-id="81789-116">![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="81789-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="81789-117">ADO.NET Entity Framework 會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="81789-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="81789-118">下列 CSDL 定義上圖中的 `PublishedBy` 關聯。</span><span class="sxs-lookup"><span data-stu-id="81789-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="81789-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="81789-119">See Also</span></span>  
 [<span data-ttu-id="81789-120">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="81789-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="81789-121">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="81789-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
