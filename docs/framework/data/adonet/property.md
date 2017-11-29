---
title: "屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c052c53488fde0ea767a46f51ef349dd6a7d2766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="property"></a><span data-ttu-id="4a472-102">屬性</span><span class="sxs-lookup"><span data-stu-id="4a472-102">property</span></span>
<span data-ttu-id="4a472-103">*屬性*是基本建置組塊的[實體類型](../../../../docs/framework/data/adonet/entity-type.md)和[複雜型別](../../../../docs/framework/data/adonet/complex-type.md)。</span><span class="sxs-lookup"><span data-stu-id="4a472-103">*Properties* are the fundamental building blocks of [entity types](../../../../docs/framework/data/adonet/entity-type.md) and [complex types](../../../../docs/framework/data/adonet/complex-type.md).</span></span> <span data-ttu-id="4a472-104">屬性可定義實體類型執行個體或複雜類型執行個體將包含的資料圖案和特性。</span><span class="sxs-lookup"><span data-stu-id="4a472-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="4a472-105">概念模型中的屬性類似類別中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a472-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="4a472-106">如同類別上的屬性可定義類別的圖形並包含關於物件的資訊，概念模型的屬性可定義實體類別的圖形，並包含關於實體類型執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="4a472-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a472-107">如本章所述，屬性與導覽屬性不同。</span><span class="sxs-lookup"><span data-stu-id="4a472-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="4a472-108">如需詳細資訊，請參閱[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)。</span><span class="sxs-lookup"><span data-stu-id="4a472-108">For more information, see [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md).</span></span>  
  
 <span data-ttu-id="4a472-109">屬性定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="4a472-109">A property definition contains the following information:</span></span>  
  
-   <span data-ttu-id="4a472-110">屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="4a472-110">A property name.</span></span> <span data-ttu-id="4a472-111">(必要項)</span><span class="sxs-lookup"><span data-stu-id="4a472-111">(Required)</span></span>  
  
-   <span data-ttu-id="4a472-112">屬性型別。</span><span class="sxs-lookup"><span data-stu-id="4a472-112">A property type.</span></span> <span data-ttu-id="4a472-113">(必要項)</span><span class="sxs-lookup"><span data-stu-id="4a472-113">(Required)</span></span>  
  
-   <span data-ttu-id="4a472-114">一組[facet](../../../../docs/framework/data/adonet/facet.md)。</span><span class="sxs-lookup"><span data-stu-id="4a472-114">A set of [facets](../../../../docs/framework/data/adonet/facet.md).</span></span> <span data-ttu-id="4a472-115">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="4a472-115">(Optional)</span></span>  
  
 <span data-ttu-id="4a472-116">屬性可以包含基底資料 (例如字串、整數或布林值) 或結構化資料 (例如複雜類型)。</span><span class="sxs-lookup"><span data-stu-id="4a472-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="4a472-117">屬於基本型別的屬性亦稱為純量屬性。</span><span class="sxs-lookup"><span data-stu-id="4a472-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="4a472-118">如需詳細資訊，請參閱[實體資料模型： 基本資料型別](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4a472-118">For more information, see [Entity Data Model: Primitive Data Types](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a472-119">複雜類型本身可以包含複雜類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a472-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a472-120">範例</span><span class="sxs-lookup"><span data-stu-id="4a472-120">Example</span></span>  
 <span data-ttu-id="4a472-121">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="4a472-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="4a472-122">雖然圖中並提供每個屬性的型別資訊，但每個實體類型均具有數個屬性。</span><span class="sxs-lookup"><span data-stu-id="4a472-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="4a472-123">屬性都[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)皆加註 （索引鍵）。</span><span class="sxs-lookup"><span data-stu-id="4a472-123">Properties that are [entity keys](../../../../docs/framework/data/adonet/entity-key.md) are denoted with (Key).</span></span>  
  
 <span data-ttu-id="4a472-124">![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="4a472-124">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="4a472-125">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="4a472-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="4a472-126">下列 CSDL 定義 `Book` 實體類型 (如上圖所示)，並且使用 XML 屬性 (attribute) 指出各個屬性 (property) 的型別和名稱。</span><span class="sxs-lookup"><span data-stu-id="4a472-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="4a472-127">`Nullable` (選擇性 Facet) 也是使用 XML 屬性所定義。</span><span class="sxs-lookup"><span data-stu-id="4a472-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="4a472-128">圖中顯示的其中一個屬性可能會是複雜類型屬性。</span><span class="sxs-lookup"><span data-stu-id="4a472-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="4a472-129">例如，`Address`實體型別上的 `Publisher` 屬性可能是複雜類型屬性，由數個包純量屬性組成，例如 `StreetAddress`、`City`、`StateOrProvince`、`Country` 和 `PostalCode`。</span><span class="sxs-lookup"><span data-stu-id="4a472-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="4a472-130">此類複雜類型的 CSDL 表示如下所示：</span><span class="sxs-lookup"><span data-stu-id="4a472-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="4a472-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a472-131">See Also</span></span>  
 [<span data-ttu-id="4a472-132">實體資料模型的重要概念</span><span class="sxs-lookup"><span data-stu-id="4a472-132">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="4a472-133">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="4a472-133">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
