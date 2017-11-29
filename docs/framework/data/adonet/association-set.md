---
title: "Association Set - 關聯集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db293cbc636d0ae4e532f24b2852444395f603c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="association-set"></a><span data-ttu-id="43d2c-102">Association Set - 關聯集</span><span class="sxs-lookup"><span data-stu-id="43d2c-102">association set</span></span>
<span data-ttu-id="43d2c-103">*關聯集*是邏輯容器[關聯](../../../../docs/framework/data/adonet/association-type.md)相同類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="43d2c-103">An *association set* is a logical container for [association](../../../../docs/framework/data/adonet/association-type.md) instances of the same type.</span></span> <span data-ttu-id="43d2c-104">關聯集不是資料模型建構，也就是說，它不會描述資料或關聯性的結構。</span><span class="sxs-lookup"><span data-stu-id="43d2c-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="43d2c-105">反之，關聯集會提供建構，讓裝載或儲存環境 (例如 Common Language Runtime 或 SQL Server 資料庫) 群組關聯執行個體，以將其對應至資料存放區。</span><span class="sxs-lookup"><span data-stu-id="43d2c-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="43d2c-106">關聯集內定義[實體容器](../../../../docs/framework/data/adonet/entity-container.md)，這是的邏輯群組[實體集](../../../../docs/framework/data/adonet/entity-set.md)和關聯集。</span><span class="sxs-lookup"><span data-stu-id="43d2c-106">An association set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="43d2c-107">關聯集的定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="43d2c-107">A definition for an association set contains the following information:</span></span>  
  
-   <span data-ttu-id="43d2c-108">關聯集名稱。</span><span class="sxs-lookup"><span data-stu-id="43d2c-108">The association set name.</span></span> <span data-ttu-id="43d2c-109">(必要項)</span><span class="sxs-lookup"><span data-stu-id="43d2c-109">(Required)</span></span>  
  
-   <span data-ttu-id="43d2c-110">將包含執行個體的關聯。</span><span class="sxs-lookup"><span data-stu-id="43d2c-110">The association of which it will contain instances.</span></span> <span data-ttu-id="43d2c-111">(必要項)</span><span class="sxs-lookup"><span data-stu-id="43d2c-111">(Required)</span></span>  
  
-   <span data-ttu-id="43d2c-112">兩個[關聯集 end](../../../../docs/framework/data/adonet/association-set-end.md)。</span><span class="sxs-lookup"><span data-stu-id="43d2c-112">Two [association set ends](../../../../docs/framework/data/adonet/association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43d2c-113">範例</span><span class="sxs-lookup"><span data-stu-id="43d2c-113">Example</span></span>  
 <span data-ttu-id="43d2c-114">下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="43d2c-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="43d2c-115">雖然圖中並未提供關聯集的相關資訊，但下圖會顯示以此模型為基礎的關聯集和實體集範例。</span><span class="sxs-lookup"><span data-stu-id="43d2c-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 <span data-ttu-id="43d2c-116">![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="43d2c-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="43d2c-117">下列範例顯示以前述概念模型為基礎的一個關聯集 (`PublishedBy`) 和兩個實體集 (`Books` 和 `Publishers`)。</span><span class="sxs-lookup"><span data-stu-id="43d2c-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="43d2c-118">在 bi`Books`實體集表示的執行個體`Book`在執行階段的實體類型。</span><span class="sxs-lookup"><span data-stu-id="43d2c-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="43d2c-119">同樣地，Pj 代表`Publisher`執行個體中`Publishers`實體集。</span><span class="sxs-lookup"><span data-stu-id="43d2c-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="43d2c-120">BiPj 表示的執行個體`PublishedBy`中的關聯`PublishedBy`關聯集。</span><span class="sxs-lookup"><span data-stu-id="43d2c-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="43d2c-121">![設定範例](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="43d2c-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="43d2c-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="43d2c-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="43d2c-123">下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。</span><span class="sxs-lookup"><span data-stu-id="43d2c-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="43d2c-124">請注意，每個關聯集的名稱和關聯都是使用 XML 屬性定義的。</span><span class="sxs-lookup"><span data-stu-id="43d2c-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="43d2c-125">您可定義每個關聯，只要沒有兩個關聯集共用的多個關聯集[關聯集 end](../../../../docs/framework/data/adonet/association-set-end.md)。</span><span class="sxs-lookup"><span data-stu-id="43d2c-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](../../../../docs/framework/data/adonet/association-set-end.md).</span></span> <span data-ttu-id="43d2c-126">下列 CSDL 可定義具有兩個 `WrittenBy` 關聯之關聯集的實體容體。</span><span class="sxs-lookup"><span data-stu-id="43d2c-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="43d2c-127">請注意，`Book` 和 `Author` 實體類型皆定義了多個實體集，且所有關聯集皆不共用關聯集 End。</span><span class="sxs-lookup"><span data-stu-id="43d2c-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="43d2c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43d2c-128">See Also</span></span>  
 [<span data-ttu-id="43d2c-129">實體資料模型的重要概念</span><span class="sxs-lookup"><span data-stu-id="43d2c-129">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="43d2c-130">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="43d2c-130">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="43d2c-131">外部索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="43d2c-131">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)
