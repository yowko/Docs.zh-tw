---
title: 複雜類型
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 9d63660c441192bbc9ecb48bb3a86030b46461cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61880002"
---
# <a name="complex-type"></a><span data-ttu-id="13116-102">複雜類型</span><span class="sxs-lookup"><span data-stu-id="13116-102">complex type</span></span>
<span data-ttu-id="13116-103">A*複雜型別*是上定義豐富結構化屬性的範本[實體類型](../../../../docs/framework/data/adonet/entity-type.md)或其他複雜類型。</span><span class="sxs-lookup"><span data-stu-id="13116-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="13116-104">每個範本包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="13116-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="13116-105">唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="13116-105">A unique name.</span></span> <span data-ttu-id="13116-106">(必要項)</span><span class="sxs-lookup"><span data-stu-id="13116-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13116-107">複雜類型的名稱不可以與同一個命名空間中的實體類型名稱相同。</span><span class="sxs-lookup"><span data-stu-id="13116-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="13116-108">一或多個表單中的資料[屬性](../../../../docs/framework/data/adonet/property.md)。</span><span class="sxs-lookup"><span data-stu-id="13116-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="13116-109">(選擇性。)</span><span class="sxs-lookup"><span data-stu-id="13116-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13116-110">複雜類型的屬性可以是另一個複雜類型。</span><span class="sxs-lookup"><span data-stu-id="13116-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="13116-111">複雜類型與實體類型相似之處在於，複雜類型可以包含基本型別屬性或其他複雜類型形式的資料承載。</span><span class="sxs-lookup"><span data-stu-id="13116-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="13116-112">不過，複雜型別和實體類型之間還是有些重大的差異：</span><span class="sxs-lookup"><span data-stu-id="13116-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="13116-113">複雜類型不具有識別，因此無法獨立存在。</span><span class="sxs-lookup"><span data-stu-id="13116-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="13116-114">複雜類型只能以實體類型或其他複雜類型的屬性形式存在。</span><span class="sxs-lookup"><span data-stu-id="13116-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="13116-115">複雜型別不能參與[關聯](../../../../docs/framework/data/adonet/association-type.md)。</span><span class="sxs-lookup"><span data-stu-id="13116-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="13116-116">關聯的兩個端點可以是複雜類型，因此[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)不能定義於複雜型別。</span><span class="sxs-lookup"><span data-stu-id="13116-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13116-117">範例</span><span class="sxs-lookup"><span data-stu-id="13116-117">Example</span></span>  
 <span data-ttu-id="13116-118">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="13116-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="13116-119">下列 CSDL 以基底類型屬性 `StreetAddress`、`City`、`StateOrProvince`、`Country` 和 `PostalCode` 定義複雜類型 Address。</span><span class="sxs-lookup"><span data-stu-id="13116-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="13116-120">若要將上方的複雜類型 `Address` 定義為實體類型上的屬性，您必須在實體類型定義中宣告屬性型別。</span><span class="sxs-lookup"><span data-stu-id="13116-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="13116-121">下列 CSDL 會在實體類型 (Publisher) 上將 `Address` 屬性宣告為複雜類型：</span><span class="sxs-lookup"><span data-stu-id="13116-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="13116-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13116-122">See also</span></span>

- [<span data-ttu-id="13116-123">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="13116-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="13116-124">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="13116-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
