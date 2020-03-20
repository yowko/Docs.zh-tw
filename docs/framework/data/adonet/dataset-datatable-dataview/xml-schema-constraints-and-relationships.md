---
title: XML 結構描述條件約束和關聯性
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150710"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="98c36-102">XML 結構描述條件約束和關聯性</span><span class="sxs-lookup"><span data-stu-id="98c36-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="98c36-103">在 XML 架構定義語言 （XSD） 架構中，您可以指定約束（唯一、鍵和鍵ref約束）和關係（使用**msdata：關係**注釋）。</span><span class="sxs-lookup"><span data-stu-id="98c36-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="98c36-104">這個主題會說明 XML 結構描述中指定的條件約束和關聯性如何經過解譯以產生 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="98c36-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="98c36-105">通常，在 XML 架構中，如果只想在**DataSet**中生成關係，請指定**msdata：關係**注釋。</span><span class="sxs-lookup"><span data-stu-id="98c36-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="98c36-106">有關詳細資訊，請參閱從[XML 架構 （XSD） 生成資料集關係](generating-dataset-relations-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="98c36-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="98c36-107">如果要在**DataSet**中生成約束，請指定約束（唯一、鍵和鍵ref）。</span><span class="sxs-lookup"><span data-stu-id="98c36-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="98c36-108">請注意，索引鍵條件約束和 keyref 條件約束也用於產生關聯性，詳情請見這個主題的後續說明。</span><span class="sxs-lookup"><span data-stu-id="98c36-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="98c36-109">從索引鍵條件約束和 keyref 條件約束產生關聯性</span><span class="sxs-lookup"><span data-stu-id="98c36-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="98c36-110">您可以指定鍵和鍵ref約束，這些約束在 XML 架構映射過程中不僅用於生成約束，而且生成**DataSet**中的關係，而不是指定**msdata：關係**注釋。</span><span class="sxs-lookup"><span data-stu-id="98c36-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="98c36-111">但是，如果在`msdata:ConstraintOnly="true"`**keyref**元素中指定 **，DataSet**將僅包含約束，並且不包括關係。</span><span class="sxs-lookup"><span data-stu-id="98c36-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="98c36-112">下面的示例顯示了一個 XML 架構，該架構包括**未嵌套的訂單**和**訂單詳細資訊**元素。</span><span class="sxs-lookup"><span data-stu-id="98c36-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="98c36-113">結構描述也指定索引鍵條件約束和 keyref 條件約束。</span><span class="sxs-lookup"><span data-stu-id="98c36-113">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="98c36-114">在 XML 架構映射過程中生成的**資料集**包括**訂單**和**訂單詳細資訊**表。</span><span class="sxs-lookup"><span data-stu-id="98c36-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="98c36-115">此外，**資料集**還包括關係和約束。</span><span class="sxs-lookup"><span data-stu-id="98c36-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="98c36-116">下列範例會顯示這些關聯性和條件約束。</span><span class="sxs-lookup"><span data-stu-id="98c36-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="98c36-117">請注意，架構未指定**msdata：關係**注釋;相反，鍵和鍵ref約束用於生成關係。</span><span class="sxs-lookup"><span data-stu-id="98c36-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```text
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 <span data-ttu-id="98c36-118">在前面的架構示例中，**順序**和**訂單詳細資訊**元素不嵌套。</span><span class="sxs-lookup"><span data-stu-id="98c36-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="98c36-119">下列的結構描述範例中，這些項目則為巢狀化。</span><span class="sxs-lookup"><span data-stu-id="98c36-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="98c36-120">但是，未指定**msdata：關係**注釋指定;因此，假定了隱式關係。</span><span class="sxs-lookup"><span data-stu-id="98c36-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="98c36-121">有關詳細資訊，請參閱[嵌套架構元素之間的映射隱式關係](map-implicit-relations-between-nested-schema-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="98c36-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="98c36-122">結構描述也指定索引鍵條件約束和 keyref 條件約束。</span><span class="sxs-lookup"><span data-stu-id="98c36-122">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="98c36-123">XML 架構映射過程產生的**資料集**包括兩個表：</span><span class="sxs-lookup"><span data-stu-id="98c36-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="98c36-124">**DataSet**還包括兩個關係（一個基於**msdata：關係**注釋，另一個基於鍵和鍵ref約束）和各種約束。</span><span class="sxs-lookup"><span data-stu-id="98c36-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="98c36-125">下列範例顯示關聯和條件約束。</span><span class="sxs-lookup"><span data-stu-id="98c36-125">The following example shows the relations and constraints.</span></span>  
  
```text
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 <span data-ttu-id="98c36-126">如果引用巢狀表格的 keyref 約束包含**msdata：IsNested_"true"** 注釋 **，DataSet**將創建基於 keyref 約束和相關唯一/鍵約束的單個嵌套關係。</span><span class="sxs-lookup"><span data-stu-id="98c36-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c36-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98c36-127">See also</span></span>

- [<span data-ttu-id="98c36-128">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="98c36-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- <span data-ttu-id="98c36-129">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="98c36-129">[ADO.NET Overview](../ado-net-overview.md)</span></span>
