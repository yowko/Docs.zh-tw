---
title: 實體資料模型
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: e76527b497434ada06762fcab931522fffa2a16b
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529063"
---
# <a name="entity-data-model"></a><span data-ttu-id="e1d0e-102">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="e1d0e-102">Entity Data Model</span></span>
<span data-ttu-id="e1d0e-103">實體資料模型 (EDM) 是描述資料結構的概念集，不論其預存形式為何。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-103">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="e1d0e-104">EDM 借用 Peter Chen 於 1976 年描述的實體關聯模型 (Entity-Relationship Model)，但同時補強實體關聯模型並延伸其傳統用法。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-104">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="e1d0e-105">EDM 解決資料儲存形式過多所導致的難題。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-105">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="e1d0e-106">例如，試想將資料儲存在關聯式資料庫、文字檔、XML 檔、試算表及報告中的企業。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-106">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="e1d0e-107">這代表著資料模型、應用程式設計及資料存取各方面的重大挑戰。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-107">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="e1d0e-108">設計資料導向應用程式時，難題在於撰寫有效率且可維護的程式碼，而不需犧牲資料存取、儲存的效率及擴充性。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-108">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="e1d0e-109">資料具有關聯結構時，資料存取、儲存及擴充性非常有效率，但維持寫入效率及可維護的程式碼則更為困難。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-109">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="e1d0e-110">資料具有物件結構時，取捨則是相反的：必須犧牲資料存取及儲存的效率和擴充性，以換取寫入效率和可維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-110">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="e1d0e-111">即使能在這些取捨當中找到平衡，在不同形式之間轉移資料時仍會出現新的挑戰。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-111">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="e1d0e-112">實體資料模型能夠依據獨立於任何儲存結構描述的實體和關聯來描述資料結構，因此可以解決這些難題。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-112">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="e1d0e-113">這也讓資料的預存形式與應用設計和開發不相關。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-113">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="e1d0e-114">同時，由於實體和關聯會以應用程式中使用資料的方式 (而非其預存形式) 來描述資料結構，因此可以隨著應用程式的演進而演進。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-114">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="e1d0e-115">`conceptual model`是以實體和關係代表資料結構的特定表示，而且通常是以實作 EDM 概念的特定定義域語言 (DSL) 定義而成。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-115">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="e1d0e-116">[概念結構定義語言 (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)是這類特定領域語言的範例。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-116">[Conceptual schema definition language (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) is an example of such a domain-specific language.</span></span> <span data-ttu-id="e1d0e-117">您可以將概念模型中描述的實體和關聯視為應用程式中的抽象物件和關聯。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-117">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="e1d0e-118">這樣可讓開發人員專注於概念模型，不需擔心儲存結構描述，也可以讓他們有效率地撰寫程式碼並兼顧可維護性。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-118">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="e1d0e-119">同時，儲存結構描述設計人員可以專注於資料存取、儲存的效率及擴充性。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-119">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1d0e-120">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e1d0e-120">In This Section</span></span>  
 <span data-ttu-id="e1d0e-121">本節的主題描述實體資料模型的概念。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-121">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="e1d0e-122">實作 EDM 介面的任何 DSL 都應包括此處描述的概念。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-122">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="e1d0e-123">請注意， [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用 CSDL 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-123">Note that the [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="e1d0e-124">如需詳細資訊，請參閱 < [CSDL 規格](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)。</span><span class="sxs-lookup"><span data-stu-id="e1d0e-124">For more information, see [CSDL Specification](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span>  
  
 [<span data-ttu-id="e1d0e-125">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="e1d0e-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="e1d0e-126">實體資料模型：命名空間</span><span class="sxs-lookup"><span data-stu-id="e1d0e-126">Entity Data Model: Namespaces</span></span>](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="e1d0e-127">實體資料模型：基本資料類型</span><span class="sxs-lookup"><span data-stu-id="e1d0e-127">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="e1d0e-128">實體資料模型：繼承</span><span class="sxs-lookup"><span data-stu-id="e1d0e-128">Entity Data Model: Inheritance</span></span>](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="e1d0e-129">關聯 End</span><span class="sxs-lookup"><span data-stu-id="e1d0e-129">association end</span></span>](../../../../docs/framework/data/adonet/association-end.md)  
  
 [<span data-ttu-id="e1d0e-130">關聯 End 多重性</span><span class="sxs-lookup"><span data-stu-id="e1d0e-130">association end multiplicity</span></span>](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [<span data-ttu-id="e1d0e-131">關聯集</span><span class="sxs-lookup"><span data-stu-id="e1d0e-131">association set</span></span>](../../../../docs/framework/data/adonet/association-set.md)  
  
 [<span data-ttu-id="e1d0e-132">關聯集 End</span><span class="sxs-lookup"><span data-stu-id="e1d0e-132">association set end</span></span>](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [<span data-ttu-id="e1d0e-133">關聯類型</span><span class="sxs-lookup"><span data-stu-id="e1d0e-133">association type</span></span>](../../../../docs/framework/data/adonet/association-type.md)  
  
 [<span data-ttu-id="e1d0e-134">複雜類型</span><span class="sxs-lookup"><span data-stu-id="e1d0e-134">complex type</span></span>](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [<span data-ttu-id="e1d0e-135">實體容器</span><span class="sxs-lookup"><span data-stu-id="e1d0e-135">entity container</span></span>](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [<span data-ttu-id="e1d0e-136">實體索引鍵</span><span class="sxs-lookup"><span data-stu-id="e1d0e-136">entity key</span></span>](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [<span data-ttu-id="e1d0e-137">實體集</span><span class="sxs-lookup"><span data-stu-id="e1d0e-137">entity set</span></span>](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [<span data-ttu-id="e1d0e-138">實體類型</span><span class="sxs-lookup"><span data-stu-id="e1d0e-138">entity type</span></span>](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [<span data-ttu-id="e1d0e-139">facet</span><span class="sxs-lookup"><span data-stu-id="e1d0e-139">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)  
  
 [<span data-ttu-id="e1d0e-140">外部索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="e1d0e-140">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [<span data-ttu-id="e1d0e-141">模型宣告函式</span><span class="sxs-lookup"><span data-stu-id="e1d0e-141">model-declared function</span></span>](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [<span data-ttu-id="e1d0e-142">模型定義函式</span><span class="sxs-lookup"><span data-stu-id="e1d0e-142">model-defined function</span></span>](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [<span data-ttu-id="e1d0e-143">導覽屬性</span><span class="sxs-lookup"><span data-stu-id="e1d0e-143">navigation property</span></span>](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [<span data-ttu-id="e1d0e-144">屬性</span><span class="sxs-lookup"><span data-stu-id="e1d0e-144">property</span></span>](../../../../docs/framework/data/adonet/property.md)  
  
 [<span data-ttu-id="e1d0e-145">參考完整性條件約束</span><span class="sxs-lookup"><span data-stu-id="e1d0e-145">referential integrity constraint</span></span>](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="e1d0e-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1d0e-146">See Also</span></span>  
 [<span data-ttu-id="e1d0e-147">ADO.NET 實體資料模型工具</span><span class="sxs-lookup"><span data-stu-id="e1d0e-147">ADO.NET Entity Data Model  Tools</span></span>](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="e1d0e-148">.edmx 檔案概觀</span><span class="sxs-lookup"><span data-stu-id="e1d0e-148">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="e1d0e-149">CSDL 規格</span><span class="sxs-lookup"><span data-stu-id="e1d0e-149">CSDL Specification</span></span>](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
