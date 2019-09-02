---
title: 將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b0082b534b8df10ac5277cf2f5aa5b2d2e40c11b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204628"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="b27b9-102">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="b27b9-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="b27b9-103">XML 結構描述定義語言 (XSD) 允許在其定義的項目和屬性上指定條件約束。</span><span class="sxs-lookup"><span data-stu-id="b27b9-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="b27b9-104">將 xml 架構對應至中<xref:System.Data.DataSet>的關聯式結構描述時, xml 架構條件約束會對應至**資料集**內資料表和資料行上適當的關聯式條件約束。</span><span class="sxs-lookup"><span data-stu-id="b27b9-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="b27b9-105">本節討論下列 XML 結構描述條件約束的對應：</span><span class="sxs-lookup"><span data-stu-id="b27b9-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="b27b9-106">使用**unique**元素指定的唯一性條件約束。</span><span class="sxs-lookup"><span data-stu-id="b27b9-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="b27b9-107">使用**key**元素指定的索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="b27b9-107">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="b27b9-108">使用**keyref**元素指定的 keyref 條件約束。</span><span class="sxs-lookup"><span data-stu-id="b27b9-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="b27b9-109">您可以在項目或屬性上使用條件約束，為文件內任何執行個體項目的值指定特定限制。</span><span class="sxs-lookup"><span data-stu-id="b27b9-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="b27b9-110">例如, 在架構中, **Customer**專案之**customerid**子項目的索引鍵條件約束表示**CustomerID**子項目的值在任何檔實例中必須是唯一的, 而且不允許 null 值。</span><span class="sxs-lookup"><span data-stu-id="b27b9-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="b27b9-111">您也可以在文件的項目和屬性間指定條件約束，以便在文件中建立關係。</span><span class="sxs-lookup"><span data-stu-id="b27b9-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="b27b9-112">結構描述中會使用索引鍵條件約束和 keyref 條件約束在文件內指定條件約束，以建立文件項目和屬性之間的關係。</span><span class="sxs-lookup"><span data-stu-id="b27b9-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="b27b9-113">對應程式會將這些架構條件約束轉換成在**資料集**內建立之資料表的適當條件約束。</span><span class="sxs-lookup"><span data-stu-id="b27b9-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b27b9-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="b27b9-114">In This Section</span></span>  
 [<span data-ttu-id="b27b9-115">將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="b27b9-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="b27b9-116">描述用來在**資料集中**建立唯一條件約束的 XML 架構元素。</span><span class="sxs-lookup"><span data-stu-id="b27b9-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="b27b9-117">將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="b27b9-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="b27b9-118">描述**資料集**內用來建立索引鍵條件約束 (不允許 null 值的唯一條件約束) 的 XML 架構元素。</span><span class="sxs-lookup"><span data-stu-id="b27b9-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="b27b9-119">將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="b27b9-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="b27b9-120">描述用來在**資料集**內建立 keyref (外鍵) 條件約束的 XML 架構專案。</span><span class="sxs-lookup"><span data-stu-id="b27b9-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b27b9-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="b27b9-121">Related Sections</span></span>  
 [<span data-ttu-id="b27b9-122">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="b27b9-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="b27b9-123">描述從 XSD 架構建立之**資料集**的關聯式結構 (或架構)。</span><span class="sxs-lookup"><span data-stu-id="b27b9-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="b27b9-124">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="b27b9-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="b27b9-125">描述用來在**資料集**內的資料表資料行之間建立關聯的 XML 架構元素。</span><span class="sxs-lookup"><span data-stu-id="b27b9-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b27b9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b27b9-126">See also</span></span>

- [<span data-ttu-id="b27b9-127">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b27b9-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
