---
title: "將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ac310542ba9dea360acbc2a0fbcbb07b7a8d6fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="d339e-102">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="d339e-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="d339e-103">XML 結構描述定義語言 (XSD) 允許在其定義的項目和屬性上指定條件約束。</span><span class="sxs-lookup"><span data-stu-id="d339e-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="d339e-104">對應到關聯式結構描述中的 XML 結構描述時<xref:System.Data.DataSet>，XML 結構描述條件約束會對應至適當的資料表與資料行內的關聯式條件約束**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d339e-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="d339e-105">本節討論下列 XML 結構描述條件約束的對應：</span><span class="sxs-lookup"><span data-stu-id="d339e-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
-   <span data-ttu-id="d339e-106">使用指定的唯一性條件約束**唯一**項目。</span><span class="sxs-lookup"><span data-stu-id="d339e-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
-   <span data-ttu-id="d339e-107">使用指定的索引鍵條件約束**金鑰**項目。</span><span class="sxs-lookup"><span data-stu-id="d339e-107">The key constraint specified using the **key** element.</span></span>  
  
-   <span data-ttu-id="d339e-108">使用指定的 keyref 條件約束**keyref**項目。</span><span class="sxs-lookup"><span data-stu-id="d339e-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="d339e-109">您可以在項目或屬性上使用條件約束，為文件內任何執行個體項目的值指定特定限制。</span><span class="sxs-lookup"><span data-stu-id="d339e-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="d339e-110">例如，索引鍵條件約束**CustomerID**子項目**客戶**結構描述中的項目表示的值**CustomerID**子元素必須是在任何文件執行個體中是唯一而且不允許 null 值。</span><span class="sxs-lookup"><span data-stu-id="d339e-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="d339e-111">您也可以在文件的項目和屬性間指定條件約束，以便在文件中建立關係。</span><span class="sxs-lookup"><span data-stu-id="d339e-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="d339e-112">結構描述中會使用索引鍵條件約束和 keyref 條件約束在文件內指定條件約束，以建立文件項目和屬性之間的關係。</span><span class="sxs-lookup"><span data-stu-id="d339e-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="d339e-113">對應處理序會將這些結構描述條件約束轉換成適當的條件約束內所建立的資料表上**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d339e-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d339e-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="d339e-114">In This Section</span></span>  
 [<span data-ttu-id="d339e-115">將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="d339e-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d339e-116">說明用來建立唯一條件約束中的 XML 結構描述項目**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d339e-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="d339e-117">將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="d339e-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d339e-118">描述用來建立索引鍵條件約束 （唯一的條件約束不允許 null 值） 的 XML 結構描述項目中**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d339e-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="d339e-119">將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="d339e-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d339e-120">說明用來建立 keyref （外部索引鍵） 條件約束中的 XML 結構描述項目**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d339e-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d339e-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="d339e-121">Related Sections</span></span>  
 [<span data-ttu-id="d339e-122">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="d339e-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="d339e-123">描述關聯式結構描述的**資料集**從 XSD 結構描述中建立的。</span><span class="sxs-lookup"><span data-stu-id="d339e-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="d339e-124">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="d339e-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="d339e-125">說明用來在資料表資料行間建立關聯的 XML 結構描述項目**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d339e-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d339e-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="d339e-126">See Also</span></span>  
 [<span data-ttu-id="d339e-127">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d339e-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
