---
title: 實體資料模型
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: 1742b04d0e3d8387e990d40d832e355dd15c4311
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783953"
---
# <a name="entity-data-model"></a><span data-ttu-id="a2d99-102">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="a2d99-102">Entity Data Model</span></span>
<span data-ttu-id="a2d99-103">實體資料模型 (EDM) 是描述資料結構的概念集，不論其預存形式為何。</span><span class="sxs-lookup"><span data-stu-id="a2d99-103">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="a2d99-104">EDM 借用 Peter Chen 於 1976 年描述的實體關聯模型 (Entity-Relationship Model)，但同時補強實體關聯模型並延伸其傳統用法。</span><span class="sxs-lookup"><span data-stu-id="a2d99-104">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="a2d99-105">EDM 解決資料儲存形式過多所導致的難題。</span><span class="sxs-lookup"><span data-stu-id="a2d99-105">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="a2d99-106">例如，試想將資料儲存在關聯式資料庫、文字檔、XML 檔、試算表及報告中的企業。</span><span class="sxs-lookup"><span data-stu-id="a2d99-106">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="a2d99-107">這代表著資料模型、應用程式設計及資料存取各方面的重大挑戰。</span><span class="sxs-lookup"><span data-stu-id="a2d99-107">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="a2d99-108">設計資料導向應用程式時，難題在於撰寫有效率且可維護的程式碼，而不需犧牲資料存取、儲存的效率及擴充性。</span><span class="sxs-lookup"><span data-stu-id="a2d99-108">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="a2d99-109">資料具有關聯結構時，資料存取、儲存及擴充性非常有效率，但維持寫入效率及可維護的程式碼則更為困難。</span><span class="sxs-lookup"><span data-stu-id="a2d99-109">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="a2d99-110">當資料具有物件結構時，會反轉取捨：撰寫有效率且可維護的程式碼，是以有效率的資料存取、儲存和擴充性為代價。</span><span class="sxs-lookup"><span data-stu-id="a2d99-110">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="a2d99-111">即使能在這些取捨當中找到平衡，在不同形式之間轉移資料時仍會出現新的挑戰。</span><span class="sxs-lookup"><span data-stu-id="a2d99-111">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="a2d99-112">實體資料模型能夠依據獨立於任何儲存結構描述的實體和關聯來描述資料結構，因此可以解決這些難題。</span><span class="sxs-lookup"><span data-stu-id="a2d99-112">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="a2d99-113">這也讓資料的預存形式與應用設計和開發不相關。</span><span class="sxs-lookup"><span data-stu-id="a2d99-113">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="a2d99-114">同時，由於實體和關聯會以應用程式中使用資料的方式 (而非其預存形式) 來描述資料結構，因此可以隨著應用程式的演進而演進。</span><span class="sxs-lookup"><span data-stu-id="a2d99-114">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="a2d99-115">`conceptual model`是以實體和關係代表資料結構的特定表示，而且通常是以實作 EDM 概念的特定定義域語言 (DSL) 定義而成。</span><span class="sxs-lookup"><span data-stu-id="a2d99-115">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="a2d99-116">[概念結構定義語言（CSDL）](./ef/language-reference/csdl-specification.md)是這類特定領域語言的範例。</span><span class="sxs-lookup"><span data-stu-id="a2d99-116">[Conceptual schema definition language (CSDL)](./ef/language-reference/csdl-specification.md) is an example of such a domain-specific language.</span></span> <span data-ttu-id="a2d99-117">您可以將概念模型中描述的實體和關聯視為應用程式中的抽象物件和關聯。</span><span class="sxs-lookup"><span data-stu-id="a2d99-117">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="a2d99-118">這樣可讓開發人員專注於概念模型，不需擔心儲存結構描述，也可以讓他們有效率地撰寫程式碼並兼顧可維護性。</span><span class="sxs-lookup"><span data-stu-id="a2d99-118">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="a2d99-119">同時，儲存結構描述設計人員可以專注於資料存取、儲存的效率及擴充性。</span><span class="sxs-lookup"><span data-stu-id="a2d99-119">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2d99-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="a2d99-120">In This Section</span></span>  
 <span data-ttu-id="a2d99-121">本節的主題描述實體資料模型的概念。</span><span class="sxs-lookup"><span data-stu-id="a2d99-121">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="a2d99-122">實作 EDM 介面的任何 DSL 都應包括此處描述的概念。</span><span class="sxs-lookup"><span data-stu-id="a2d99-122">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="a2d99-123">請注意， [ADO.NET Entity Framework](./ef/index.md)會使用 CSDL 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="a2d99-123">Note that the [ADO.NET Entity Framework](./ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="a2d99-124">如需詳細資訊，請參閱 [CSDL Specification](./ef/language-reference/csdl-specification.md)。</span><span class="sxs-lookup"><span data-stu-id="a2d99-124">For more information, see [CSDL Specification](./ef/language-reference/csdl-specification.md).</span></span>  
  
 [<span data-ttu-id="a2d99-125">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="a2d99-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="a2d99-126">實體資料模型：命名空間</span><span class="sxs-lookup"><span data-stu-id="a2d99-126">Entity Data Model: Namespaces</span></span>](entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="a2d99-127">實體資料模型：基本資料類型</span><span class="sxs-lookup"><span data-stu-id="a2d99-127">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="a2d99-128">實體資料模型：繼承性</span><span class="sxs-lookup"><span data-stu-id="a2d99-128">Entity Data Model: Inheritance</span></span>](entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="a2d99-129">關聯 End</span><span class="sxs-lookup"><span data-stu-id="a2d99-129">association end</span></span>](association-end.md)  
  
 [<span data-ttu-id="a2d99-130">關聯 End 多重性</span><span class="sxs-lookup"><span data-stu-id="a2d99-130">association end multiplicity</span></span>](association-end-multiplicity.md)  
  
 [<span data-ttu-id="a2d99-131">關聯集</span><span class="sxs-lookup"><span data-stu-id="a2d99-131">association set</span></span>](association-set.md)  
  
 [<span data-ttu-id="a2d99-132">關聯集 End</span><span class="sxs-lookup"><span data-stu-id="a2d99-132">association set end</span></span>](association-set-end.md)  
  
 [<span data-ttu-id="a2d99-133">關聯類型</span><span class="sxs-lookup"><span data-stu-id="a2d99-133">association type</span></span>](association-type.md)  
  
 [<span data-ttu-id="a2d99-134">複雜類型</span><span class="sxs-lookup"><span data-stu-id="a2d99-134">complex type</span></span>](complex-type.md)  
  
 [<span data-ttu-id="a2d99-135">實體容器</span><span class="sxs-lookup"><span data-stu-id="a2d99-135">entity container</span></span>](entity-container.md)  
  
 [<span data-ttu-id="a2d99-136">實體索引鍵</span><span class="sxs-lookup"><span data-stu-id="a2d99-136">entity key</span></span>](entity-key.md)  
  
 [<span data-ttu-id="a2d99-137">實體集</span><span class="sxs-lookup"><span data-stu-id="a2d99-137">entity set</span></span>](entity-set.md)  
  
 [<span data-ttu-id="a2d99-138">實體類型</span><span class="sxs-lookup"><span data-stu-id="a2d99-138">entity type</span></span>](entity-type.md)  
  
 [<span data-ttu-id="a2d99-139">facet</span><span class="sxs-lookup"><span data-stu-id="a2d99-139">facet</span></span>](facet.md)  
  
 [<span data-ttu-id="a2d99-140">外部索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="a2d99-140">foreign key property</span></span>](foreign-key-property.md)  
  
 [<span data-ttu-id="a2d99-141">模型宣告函式</span><span class="sxs-lookup"><span data-stu-id="a2d99-141">model-declared function</span></span>](model-declared-function.md)  
  
 [<span data-ttu-id="a2d99-142">模型定義函式</span><span class="sxs-lookup"><span data-stu-id="a2d99-142">model-defined function</span></span>](model-defined-function.md)  
  
 [<span data-ttu-id="a2d99-143">導覽屬性</span><span class="sxs-lookup"><span data-stu-id="a2d99-143">navigation property</span></span>](navigation-property.md)  
  
 [<span data-ttu-id="a2d99-144">屬性</span><span class="sxs-lookup"><span data-stu-id="a2d99-144">property</span></span>](property.md)  
  
 [<span data-ttu-id="a2d99-145">參考完整性條件約束</span><span class="sxs-lookup"><span data-stu-id="a2d99-145">referential integrity constraint</span></span>](referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="a2d99-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2d99-146">See also</span></span>

- <span data-ttu-id="a2d99-147">[ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a2d99-147">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="a2d99-148">[.edmx 檔案總覽](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a2d99-148">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="a2d99-149">CSDL 規格</span><span class="sxs-lookup"><span data-stu-id="a2d99-149">CSDL Specification</span></span>](./ef/language-reference/csdl-specification.md)
