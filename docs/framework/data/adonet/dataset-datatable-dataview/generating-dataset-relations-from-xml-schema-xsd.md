---
title: 從 XML 結構描述 (XSD) 產生資料集關聯
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151126"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="09c85-102">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="09c85-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="09c85-103">您可以在 <xref:System.Data.DataSet> 內建立父子關係，以建立兩個或多個資料行之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="09c85-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="09c85-104">在 XML 架構定義語言 （XSD） 架構中，有三種方法可以表示**DataSet**關係：</span><span class="sxs-lookup"><span data-stu-id="09c85-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="09c85-105">指定巢狀複雜類型。</span><span class="sxs-lookup"><span data-stu-id="09c85-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="09c85-106">使用**msdata：關係**注釋。</span><span class="sxs-lookup"><span data-stu-id="09c85-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="09c85-107">指定一個沒有 msdata**的 xs：keyref：\*\*\*\*僅約束**注釋。</span><span class="sxs-lookup"><span data-stu-id="09c85-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="09c85-108">巢狀複雜類型</span><span class="sxs-lookup"><span data-stu-id="09c85-108">Nested Complex Types</span></span>  
 <span data-ttu-id="09c85-109">結構描述中的巢狀複雜類型定義表示項目的父子關係。</span><span class="sxs-lookup"><span data-stu-id="09c85-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="09c85-110">以下 XML 架構片段顯示**OrderDetail**是**Order**元素的子項目。</span><span class="sxs-lookup"><span data-stu-id="09c85-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>
       <xs:element name="OrderDetail" />  
           <xs:complexType>
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="09c85-111">XML 架構映射過程在**DataSet**中創建對應于架構中嵌套複雜類型的表。</span><span class="sxs-lookup"><span data-stu-id="09c85-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="09c85-112">它還創建其他列，這些列用作生成的表**-** 的父子列。</span><span class="sxs-lookup"><span data-stu-id="09c85-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="09c85-113">請注意，這些父**-** 子列指定關係，這與指定主鍵/外鍵約束不同。</span><span class="sxs-lookup"><span data-stu-id="09c85-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="09c85-114">msdata:Relationship 註釋</span><span class="sxs-lookup"><span data-stu-id="09c85-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="09c85-115">**msdata：關係**注釋允許您顯式指定架構中未嵌套的元素之間的父子關係。</span><span class="sxs-lookup"><span data-stu-id="09c85-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="09c85-116">下面的示例顯示了**關係**元素的結構。</span><span class="sxs-lookup"><span data-stu-id="09c85-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="09c85-117">**msdata：關係**注釋的屬性標識父子關係中涉及的元素，以及關係中涉及的**父鍵**和**子鍵**元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="09c85-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="09c85-118">映射過程使用此資訊在**DataSet**中生成表，並在這些表之間創建主鍵/外鍵關係。</span><span class="sxs-lookup"><span data-stu-id="09c85-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="09c85-119">例如，以下架構片段指定同一級別的 **"訂單"** 和"**訂單詳細資訊"** 元素（未嵌套）。</span><span class="sxs-lookup"><span data-stu-id="09c85-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="09c85-120">架構指定**msdata：關係**注釋，它指定這兩個元素之間的父子關係。</span><span class="sxs-lookup"><span data-stu-id="09c85-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="09c85-121">在這種情況下，必須使用**msdata：關係**注釋指定顯式關係。</span><span class="sxs-lookup"><span data-stu-id="09c85-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="09c85-122">映射過程使用 **"關係"** 元素在 **"訂單**"表中的**OrderNumber**列和**DataSet**中的 **"訂單詳細資訊**"表中的 **"訂單無"** 列之間創建父子關係。</span><span class="sxs-lookup"><span data-stu-id="09c85-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="09c85-123">對應處理只會指定關係，而不會像關聯式資料庫的主索引鍵/外部索引鍵條件約束一樣，自動為這些資料行的值指定任何條件約束。</span><span class="sxs-lookup"><span data-stu-id="09c85-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="09c85-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="09c85-124">In This Section</span></span>  
 [<span data-ttu-id="09c85-125">在巢狀結構描述項目之間進行隱含關聯對應</span><span class="sxs-lookup"><span data-stu-id="09c85-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="09c85-126">描述在 XML 架構中遇到嵌套元素時在**DataSet**中隱式創建的約束和關係。</span><span class="sxs-lookup"><span data-stu-id="09c85-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="09c85-127">針對巢狀項目指定的關聯進行對應</span><span class="sxs-lookup"><span data-stu-id="09c85-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="09c85-128">描述如何在 XML 架構中為嵌套元素在**DataSet**中顯式設置關係。</span><span class="sxs-lookup"><span data-stu-id="09c85-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="09c85-129">指定未巢狀放置之項目間的關聯</span><span class="sxs-lookup"><span data-stu-id="09c85-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="09c85-130">描述如何在未嵌套的 XML 架構元素之間的**DataSet**中創建關係。</span><span class="sxs-lookup"><span data-stu-id="09c85-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="09c85-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="09c85-131">Related Sections</span></span>  
 [<span data-ttu-id="09c85-132">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="09c85-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="09c85-133">描述從 XML 架構定義語言 （XSD） 架構創建的**DataSet**的關聯式結構或架構。</span><span class="sxs-lookup"><span data-stu-id="09c85-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="09c85-134">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="09c85-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="09c85-135">描述用於在**DataSet**中創建唯一和外鍵約束的 XML 架構元素。</span><span class="sxs-lookup"><span data-stu-id="09c85-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c85-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09c85-136">See also</span></span>

- <span data-ttu-id="09c85-137">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="09c85-137">[ADO.NET Overview](../ado-net-overview.md)</span></span>
