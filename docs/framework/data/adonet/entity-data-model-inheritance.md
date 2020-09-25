---
title: 實體資料模型：繼承
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 057040eee411988c46adc9c4cabcfe5f5a185e1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175456"
---
# <a name="entity-data-model-inheritance"></a><span data-ttu-id="bc385-102">實體資料模型：繼承</span><span class="sxs-lookup"><span data-stu-id="bc385-102">Entity Data Model: Inheritance</span></span>

<span data-ttu-id="bc385-103">實體資料模型 (EDM) 支援 [實體類型](entity-type.md)的繼承。</span><span class="sxs-lookup"><span data-stu-id="bc385-103">The Entity Data Model (EDM) supports inheritance for [entity types](entity-type.md).</span></span> <span data-ttu-id="bc385-104">EDM 中的繼承類似於物件導向程式設計語言中的類別繼承。</span><span class="sxs-lookup"><span data-stu-id="bc385-104">Inheritance in the EDM is similar to inheritance for classes in object-oriented programming languages.</span></span> <span data-ttu-id="bc385-105">就像物件導向語言中的類別一樣，在概念模型中，您可以定義實體類型 (*衍生類型*) 繼承自另一個實體類型，) *基底類型* (。</span><span class="sxs-lookup"><span data-stu-id="bc385-105">Like with classes in object-oriented languages, in a conceptual model you can define an entity type (a *derived type*) that inherits from another entity type (the *base type*).</span></span> <span data-ttu-id="bc385-106">不過，不同于物件導向程式設計中的類別，在概念模型中，衍生型別一律會繼承基底類型的所有 [屬性](property.md) 和 [導覽屬性](navigation-property.md) 。</span><span class="sxs-lookup"><span data-stu-id="bc385-106">However, unlike classes in object-oriented programming, in a conceptual model the derived type always inherits all the [properties](property.md) and [navigation properties](navigation-property.md) of the base type.</span></span> <span data-ttu-id="bc385-107">您不能覆寫衍生型別中的繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="bc385-107">You cannot override inherited properties in a derived type.</span></span>  
  
 <span data-ttu-id="bc385-108">在概念模型中，您可以組建繼承階層，其中的衍生型別繼承自另一種衍生型別。</span><span class="sxs-lookup"><span data-stu-id="bc385-108">In a conceptual model you can build inheritance hierarchies in which a derived type inherits from another derived type.</span></span> <span data-ttu-id="bc385-109">階層頂端的型別 (階層中不是衍生型別) 的型別稱為「根型別」（ *root type*）。</span><span class="sxs-lookup"><span data-stu-id="bc385-109">The type at the top of the hierarchy (the one type in the hierarchy that is not a derived type) is called the *root type*.</span></span> <span data-ttu-id="bc385-110">在繼承階層中，必須在根型別上定義 [實體索引鍵](entity-key.md) 。</span><span class="sxs-lookup"><span data-stu-id="bc385-110">In an inheritance hierarchy, the [entity key](entity-key.md) must be defined on the root type.</span></span>  
  
 <span data-ttu-id="bc385-111">您不可建置衍生型別繼承自多個型別的繼承階層。</span><span class="sxs-lookup"><span data-stu-id="bc385-111">You cannot build inheritance hierarchies in which a derived type inherits from more than one type.</span></span> <span data-ttu-id="bc385-112">例如，在具有 `Book` 實體類型的概念模型中，您可以定義分別繼承自 `FictionBook` 的衍生型別 `NonFictionBook` 和 `Book`。</span><span class="sxs-lookup"><span data-stu-id="bc385-112">For example, in a conceptual model with a `Book` entity type, you could define derived types `FictionBook` and `NonFictionBook` that each inherit from `Book`.</span></span> <span data-ttu-id="bc385-113">不過，您可能無法定義同時繼承自 `FictionBook` 和 `NonFictionBook` 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="bc385-113">However, you could not then define a type that inherits from both the `FictionBook` and `NonFictionBook` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc385-114">範例</span><span class="sxs-lookup"><span data-stu-id="bc385-114">Example</span></span>  

<span data-ttu-id="bc385-115">下圖顯示具有四個實體類型的概念模型： `Book` 、 `FictionBook` 、 `Publisher` 和 `Author` 。</span><span class="sxs-lookup"><span data-stu-id="bc385-115">The following diagram shows a conceptual model with four entity types: `Book`, `FictionBook`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="bc385-116">`FictionBook` 實體類型為衍生型別，繼承自 `Book` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="bc385-116">The `FictionBook` entity type is a derived type, inheriting from the `Book` entity type.</span></span> <span data-ttu-id="bc385-117">`FictionBook` 型別繼承自 `ISBN (Key)`、`Title` 和 `Revision` 屬性，並且定義稱為 `Genre` 的額外屬性。</span><span class="sxs-lookup"><span data-stu-id="bc385-117">The `FictionBook` type inherits the `ISBN (Key)`, `Title`, and `Revision` properties, and defines an additional property called `Genre`.</span></span>  
  
 ![顯示具有四個實體類型之概念模型的圖表。](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 <span data-ttu-id="bc385-119">[ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。</span><span class="sxs-lookup"><span data-stu-id="bc385-119">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="bc385-120">下列 CSDL 定義實體類型 `FictionBook`，此實體類型繼承自 `Book` 型別 (如上圖所示)：</span><span class="sxs-lookup"><span data-stu-id="bc385-120">The following CSDL defines an entity type, `FictionBook`, that inherits from the `Book` type (as in the diagram above):</span></span>  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a><span data-ttu-id="bc385-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc385-121">See also</span></span>

- [<span data-ttu-id="bc385-122">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="bc385-122">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="bc385-123">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="bc385-123">Entity Data Model</span></span>](entity-data-model.md)
