---
title: "從 XML 結構描述 (XSD) 產生資料集關聯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bda9ff0052c6dc2462f007e3febb3cbf9ca7d5ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="d2132-102">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="d2132-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="d2132-103">您可以在 <xref:System.Data.DataSet> 內建立父子關係，以建立兩個或多個資料行之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="d2132-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="d2132-104">有三種方式來代表**資料集**XML 結構描述定義語言 (XSD) 結構描述內的關聯性：</span><span class="sxs-lookup"><span data-stu-id="d2132-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
-   <span data-ttu-id="d2132-105">指定巢狀複雜類型。</span><span class="sxs-lookup"><span data-stu-id="d2132-105">Specify nested complex types.</span></span>  
  
-   <span data-ttu-id="d2132-106">使用**msdata: relationship**註解。</span><span class="sxs-lookup"><span data-stu-id="d2132-106">Use the **msdata:Relationship** annotation.</span></span>  
  
-   <span data-ttu-id="d2132-107">指定**xs: keyref**沒有**msdata: constraintonly**註解。</span><span class="sxs-lookup"><span data-stu-id="d2132-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="d2132-108">巢狀複雜類型</span><span class="sxs-lookup"><span data-stu-id="d2132-108">Nested Complex Types</span></span>  
 <span data-ttu-id="d2132-109">結構描述中的巢狀複雜類型定義表示項目的父子關係。</span><span class="sxs-lookup"><span data-stu-id="d2132-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="d2132-110">下列 XML 結構描述片段顯示**OrderDetail**是子元素的**順序**項目。</span><span class="sxs-lookup"><span data-stu-id="d2132-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="d2132-111">XML 結構描述對應處理序會建立資料表中的**資料集**，對應至結構描述中的巢狀複雜類型。</span><span class="sxs-lookup"><span data-stu-id="d2132-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="d2132-112">它也會建立額外的資料行做為父**-**所產生之資料表的子資料行。</span><span class="sxs-lookup"><span data-stu-id="d2132-112">It also creates additional columns that are used as parent**-**child columns for the generated tables.</span></span> <span data-ttu-id="d2132-113">請注意，這些父子**-**子資料行指定關聯性，這不是指定主索引鍵/外部索引鍵條件約束相同。</span><span class="sxs-lookup"><span data-stu-id="d2132-113">Note that these parent**-**child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="d2132-114">msdata:Relationship 註釋</span><span class="sxs-lookup"><span data-stu-id="d2132-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="d2132-115">**Msdata: relationship**註釋可讓您明確指定結構描述中無巢狀的項目之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="d2132-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="d2132-116">下列範例顯示的結構**關聯性**項目。</span><span class="sxs-lookup"><span data-stu-id="d2132-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="d2132-117">屬性的**msdata: relationship**註解中識別的項目中的父子式關聯性，以及做為**parentkey**和**childkey**項目和屬性關聯性中。</span><span class="sxs-lookup"><span data-stu-id="d2132-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="d2132-118">對應處理會使用這項資訊產生資料表中的**資料集**並建立這些資料表之間主索引鍵/外部索引鍵的關係。</span><span class="sxs-lookup"><span data-stu-id="d2132-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="d2132-119">例如，下列結構描述片段指定**順序**和**OrderDetail**相同層級的項目 （無巢狀）。</span><span class="sxs-lookup"><span data-stu-id="d2132-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="d2132-120">結構描述指定**msdata: relationship**註釋，用於指定兩個元素之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="d2132-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="d2132-121">在此情況下，明確的關聯性必須指定使用**msdata: relationship**註解。</span><span class="sxs-lookup"><span data-stu-id="d2132-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="d2132-122">對應處理會使用**關聯性**項目來建立之間的父子式關聯性**OrderNumber**中的資料行**順序**資料表和**OrderNo**中的資料行**OrderDetail**資料表中**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d2132-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="d2132-123">對應處理只會指定關係，而不會像關聯式資料庫的主索引鍵/外部索引鍵條件約束一樣，自動為這些資料行的值指定任何條件約束。</span><span class="sxs-lookup"><span data-stu-id="d2132-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="d2132-124">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d2132-124">In This Section</span></span>  
 [<span data-ttu-id="d2132-125">巢狀結構描述元素之間進行隱含關聯對應</span><span class="sxs-lookup"><span data-stu-id="d2132-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="d2132-126">描述條件約束和關聯性中隱含建立**資料集**發生 XML 結構描述中巢狀項目時。</span><span class="sxs-lookup"><span data-stu-id="d2132-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="d2132-127">對應指定之巢狀元素的關聯</span><span class="sxs-lookup"><span data-stu-id="d2132-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="d2132-128">描述如何在中明確設定關聯**資料集**的 XML 結構描述中的巢狀項目。</span><span class="sxs-lookup"><span data-stu-id="d2132-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="d2132-129">指定無巢狀項目之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="d2132-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="d2132-130">描述如何建立關聯性中的**資料集**無巢狀的 XML 結構描述項目之間。</span><span class="sxs-lookup"><span data-stu-id="d2132-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="d2132-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="d2132-131">Related Sections</span></span>  
 [<span data-ttu-id="d2132-132">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="d2132-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="d2132-133">描述關聯式結構描述的**資料集**從 XML 結構描述定義語言 (XSD) 結構描述中建立的。</span><span class="sxs-lookup"><span data-stu-id="d2132-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="d2132-134">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="d2132-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d2132-135">說明用來建立唯一外部索引鍵條件約束中的 XML 結構描述項目**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d2132-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2132-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2132-136">See Also</span></span>  
 [<span data-ttu-id="d2132-137">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d2132-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
