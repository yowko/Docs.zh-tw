---
title: 從 XML 結構描述 (XSD) 產生資料集關聯
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: d00f07ee3338941b7de1bb890f71cd3c2d120246
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784639"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="a507c-102">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="a507c-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="a507c-103">您可以在 <xref:System.Data.DataSet> 內建立父子關係，以建立兩個或多個資料行之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="a507c-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="a507c-104">有三種方式可以表示 XML 架構定義語言（XSD）架構中的**資料集**關聯性：</span><span class="sxs-lookup"><span data-stu-id="a507c-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="a507c-105">指定巢狀複雜類型。</span><span class="sxs-lookup"><span data-stu-id="a507c-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="a507c-106">使用**msdata： Relationship**注釋。</span><span class="sxs-lookup"><span data-stu-id="a507c-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="a507c-107">指定不含**msdata： ConstraintOnly**注釋的**xs： keyref** 。</span><span class="sxs-lookup"><span data-stu-id="a507c-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="a507c-108">巢狀複雜類型</span><span class="sxs-lookup"><span data-stu-id="a507c-108">Nested Complex Types</span></span>  
 <span data-ttu-id="a507c-109">結構描述中的巢狀複雜類型定義表示項目的父子關係。</span><span class="sxs-lookup"><span data-stu-id="a507c-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="a507c-110">下列 XML 架構片段顯示**OrderDetail**是**Order**元素的子項目。</span><span class="sxs-lookup"><span data-stu-id="a507c-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="a507c-111">XML 架構對應進程會在**DataSet**中建立對應至架構中之嵌套複雜類型的資料表。</span><span class="sxs-lookup"><span data-stu-id="a507c-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="a507c-112">它也會建立額外的資料行，做 **-** 為所產生資料表的父子資料行使用。</span><span class="sxs-lookup"><span data-stu-id="a507c-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="a507c-113">請注意，這些 **-** 父子式資料行指定了關聯性，這與指定 primary key/foreign key 條件約束不同。</span><span class="sxs-lookup"><span data-stu-id="a507c-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="a507c-114">msdata:Relationship 註釋</span><span class="sxs-lookup"><span data-stu-id="a507c-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="a507c-115">**Msdata： Relationship**注釋可讓您明確指定架構中未嵌套之元素之間的父子關聯性。</span><span class="sxs-lookup"><span data-stu-id="a507c-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="a507c-116">下列範例顯示**Relationship**元素的結構。</span><span class="sxs-lookup"><span data-stu-id="a507c-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="a507c-117">**Msdata： Relationship**注釋的屬性會識別與父子式關聯性相關的元素，以及與關聯性相關的**parentkey**和**childkey**元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="a507c-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="a507c-118">對應程式會使用這項資訊來產生**資料集中**的資料表，並建立這些資料表之間的主鍵/外鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="a507c-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="a507c-119">例如，下列架構片段會指定位於相同層級的**Order**和**OrderDetail**專案（非 nested）。</span><span class="sxs-lookup"><span data-stu-id="a507c-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="a507c-120">架構會指定**msdata： Relationship**注釋，以指定這兩個專案之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="a507c-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="a507c-121">在此情況下，必須使用**msdata： relationship**注釋來指定明確的關聯性。</span><span class="sxs-lookup"><span data-stu-id="a507c-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="a507c-122">對應程式會使用**Relationship**元素，在**Order**資料表中的**OrderNumber**資料行和**資料集中** **OrderDetail**資料表的**OrderNo**資料行之間建立父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="a507c-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="a507c-123">對應處理只會指定關係，而不會像關聯式資料庫的主索引鍵/外部索引鍵條件約束一樣，自動為這些資料行的值指定任何條件約束。</span><span class="sxs-lookup"><span data-stu-id="a507c-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="a507c-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="a507c-124">In This Section</span></span>  
 [<span data-ttu-id="a507c-125">在巢狀結構描述項目之間進行隱含關聯對應</span><span class="sxs-lookup"><span data-stu-id="a507c-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="a507c-126">描述當 XML 架構中遇到嵌套元素時，在**DataSet**中隱含建立的條件約束和關聯性。</span><span class="sxs-lookup"><span data-stu-id="a507c-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="a507c-127">針對巢狀項目指定的關聯進行對應</span><span class="sxs-lookup"><span data-stu-id="a507c-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="a507c-128">描述如何在 XML 架構中，針對嵌套元素的**資料集**明確設定關聯性。</span><span class="sxs-lookup"><span data-stu-id="a507c-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="a507c-129">指定未巢狀放置之項目間的關聯</span><span class="sxs-lookup"><span data-stu-id="a507c-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="a507c-130">描述如何在**資料集**內，建立未嵌套之 XML 架構元素之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="a507c-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="a507c-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="a507c-131">Related Sections</span></span>  
 [<span data-ttu-id="a507c-132">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="a507c-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="a507c-133">描述從 XML 架構定義語言（XSD）架構所建立之**資料集**的關聯式結構（或架構）。</span><span class="sxs-lookup"><span data-stu-id="a507c-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="a507c-134">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="a507c-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="a507c-135">描述用來在**資料集中**建立 unique 和 foreign key 條件約束的 XML 架構專案。</span><span class="sxs-lookup"><span data-stu-id="a507c-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a507c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a507c-136">See also</span></span>

- [<span data-ttu-id="a507c-137">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="a507c-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
