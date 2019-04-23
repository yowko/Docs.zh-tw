---
title: 實體資料模型：命名空間
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 7772172512d35b9ce9cf07a992c1c5f0ecd8c55b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180558"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="702e7-102">實體資料模型：命名空間</span><span class="sxs-lookup"><span data-stu-id="702e7-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="702e7-103">在 Entity Data Model (EDM) 中的命名空間是抽象的容器，如[實體類型](../../../../docs/framework/data/adonet/entity-type.md)，[複雜型別](../../../../docs/framework/data/adonet/complex-type.md)，並[關聯](../../../../docs/framework/data/adonet/association-type.md)。</span><span class="sxs-lookup"><span data-stu-id="702e7-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](../../../../docs/framework/data/adonet/entity-type.md), [complex types](../../../../docs/framework/data/adonet/complex-type.md), and [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="702e7-104">EDM 中的命名空間類似於程式設計語言中的命名空間：針對它們所包含的物件提供內容，並且提供方法讓名稱相同 (但包含在不同命名空間中) 的物件意義清楚。</span><span class="sxs-lookup"><span data-stu-id="702e7-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="702e7-105">範例</span><span class="sxs-lookup"><span data-stu-id="702e7-105">Example</span></span>  
 <span data-ttu-id="702e7-106">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="702e7-106">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="702e7-107">下列 CSDL 程式碼使用命名空間來識別在不同概念模型中定義的型別。</span><span class="sxs-lookup"><span data-stu-id="702e7-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="702e7-108">此範例定義的實體類型 (`Publisher`) 具有從 `Address` 命名空間匯入的複雜類型屬性 (`ExtendedBooksModel`)。</span><span class="sxs-lookup"><span data-stu-id="702e7-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="702e7-109">請注意，`Using` 項目代表已匯入命名空間。</span><span class="sxs-lookup"><span data-stu-id="702e7-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="702e7-110">亦請注意，`Address` 屬性的型別是利用其完整名稱 (`ExtendedBooksModel.Address`) 來定義，表示此型別是在 `ExtendedBooksModel` 命名空間中定義的。</span><span class="sxs-lookup"><span data-stu-id="702e7-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="702e7-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="702e7-111">See also</span></span>

- [<span data-ttu-id="702e7-112">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="702e7-112">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="702e7-113">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="702e7-113">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
