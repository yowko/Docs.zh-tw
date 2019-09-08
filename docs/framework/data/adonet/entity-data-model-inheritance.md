---
title: 實體資料模型：繼承
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 21dbdff63c07dbcdac8de7bf4b3a8e5d0ece7901
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784076"
---
# <a name="entity-data-model-inheritance"></a><span data-ttu-id="0d0a5-102">實體資料模型：繼承</span><span class="sxs-lookup"><span data-stu-id="0d0a5-102">Entity Data Model: Inheritance</span></span>
<span data-ttu-id="0d0a5-103">實體資料模型（EDM）支援[實體類型](entity-type.md)的繼承。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-103">The Entity Data Model (EDM) supports inheritance for [entity types](entity-type.md).</span></span> <span data-ttu-id="0d0a5-104">EDM 中的繼承類似於物件導向程式設計語言中的類別繼承。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-104">Inheritance in the EDM is similar to inheritance for classes in object-oriented programming languages.</span></span> <span data-ttu-id="0d0a5-105">如同物件導向語言中的類別，您可以在概念模型中定義繼承自另一個實體類型（*基底類型*）的實體類型（*衍生型*別）。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-105">Like with classes in object-oriented languages, in a conceptual model you can define an entity type (a *derived type*) that inherits from another entity type (the *base type*).</span></span> <span data-ttu-id="0d0a5-106">不過，不同于物件導向程式設計中的類別，在概念模型中，衍生類型一律會繼承基底類型的所有[屬性](property.md)和[導覽屬性](navigation-property.md)。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-106">However, unlike classes in object-oriented programming, in a conceptual model the derived type always inherits all the [properties](property.md) and [navigation properties](navigation-property.md) of the base type.</span></span> <span data-ttu-id="0d0a5-107">您不能覆寫衍生型別中的繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-107">You cannot override inherited properties in a derived type.</span></span>  
  
 <span data-ttu-id="0d0a5-108">在概念模型中，您可以組建繼承階層，其中的衍生型別繼承自另一種衍生型別。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-108">In a conceptual model you can build inheritance hierarchies in which a derived type inherits from another derived type.</span></span> <span data-ttu-id="0d0a5-109">階層頂端的類型（階層中不是衍生類型的類型）稱為*根類型*。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-109">The type at the top of the hierarchy (the one type in the hierarchy that is not a derived type) is called the *root type*.</span></span> <span data-ttu-id="0d0a5-110">在繼承階層架構中，必須在根類型上定義[實體索引鍵](entity-key.md)。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-110">In an inheritance hierarchy, the [entity key](entity-key.md) must be defined on the root type.</span></span>  
  
 <span data-ttu-id="0d0a5-111">您不可建置衍生型別繼承自多個型別的繼承階層。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-111">You cannot build inheritance hierarchies in which a derived type inherits from more than one type.</span></span> <span data-ttu-id="0d0a5-112">例如，在具有 `Book` 實體類型的概念模型中，您可以定義分別繼承自 `FictionBook` 的衍生型別 `NonFictionBook` 和 `Book`。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-112">For example, in a conceptual model with a `Book` entity type, you could define derived types `FictionBook` and `NonFictionBook` that each inherit from `Book`.</span></span> <span data-ttu-id="0d0a5-113">不過，您可能無法定義同時繼承自 `FictionBook` 和 `NonFictionBook` 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-113">However, you could not then define a type that inherits from both the `FictionBook` and `NonFictionBook` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d0a5-114">範例</span><span class="sxs-lookup"><span data-stu-id="0d0a5-114">Example</span></span>  

<span data-ttu-id="0d0a5-115">下圖顯示具有四種實體類型的概念模型： `Book`、 `FictionBook`、 `Publisher`和`Author`。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-115">The following diagram shows a conceptual model with four entity types: `Book`, `FictionBook`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="0d0a5-116">`FictionBook` 實體類型為衍生型別，繼承自 `Book` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-116">The `FictionBook` entity type is a derived type, inheriting from the `Book` entity type.</span></span> <span data-ttu-id="0d0a5-117">`FictionBook` 型別繼承自 `ISBN (Key)`、`Title` 和 `Revision` 屬性，並且定義稱為 `Genre` 的額外屬性。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-117">The `FictionBook` type inherits the `ISBN (Key)`, `Title`, and `Revision` properties, and defines an additional property called `Genre`.</span></span>  
  
 ![顯示具有四個實體類型之概念模型的圖表。](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 <span data-ttu-id="0d0a5-119">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="0d0a5-119">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="0d0a5-120">下列 CSDL 定義實體類型 `FictionBook`，此實體類型繼承自 `Book` 型別 (如上圖所示)：</span><span class="sxs-lookup"><span data-stu-id="0d0a5-120">The following CSDL defines an entity type, `FictionBook`, that inherits from the `Book` type (as in the diagram above):</span></span>  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a><span data-ttu-id="0d0a5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d0a5-121">See also</span></span>

- [<span data-ttu-id="0d0a5-122">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="0d0a5-122">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="0d0a5-123">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="0d0a5-123">Entity Data Model</span></span>](entity-data-model.md)
