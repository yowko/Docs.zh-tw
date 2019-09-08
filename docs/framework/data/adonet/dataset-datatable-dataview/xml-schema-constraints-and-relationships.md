---
title: XML 結構描述條件約束和關聯性
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 76af1c2e9d85d18a68b8c0a947dfba3b3291326c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784196"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="5bd52-102">XML 結構描述條件約束和關聯性</span><span class="sxs-lookup"><span data-stu-id="5bd52-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="5bd52-103">在 XML 架構定義語言（XSD）架構中，您可以指定條件約束（unique、key 和 keyref 條件約束）和關聯性（使用**msdata： Relationship**注釋）。</span><span class="sxs-lookup"><span data-stu-id="5bd52-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="5bd52-104">這個主題會說明 XML 結構描述中指定的條件約束和關聯性如何經過解譯以產生 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="5bd52-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="5bd52-105">一般來說，在 XML 架構中，如果您只想要在**資料集中**產生關聯性，您可以指定**msdata： Relationship**注釋。</span><span class="sxs-lookup"><span data-stu-id="5bd52-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="5bd52-106">如需詳細資訊，請參閱[從 XML 架構（XSD）產生資料集](generating-dataset-relations-from-xml-schema-xsd.md)關聯。</span><span class="sxs-lookup"><span data-stu-id="5bd52-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="5bd52-107">如果您想要在**資料集中**產生條件約束，您可以指定條件約束（unique、key 和 keyref）。</span><span class="sxs-lookup"><span data-stu-id="5bd52-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="5bd52-108">請注意，索引鍵條件約束和 keyref 條件約束也用於產生關聯性，詳情請見這個主題的後續說明。</span><span class="sxs-lookup"><span data-stu-id="5bd52-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="5bd52-109">從索引鍵條件約束和 keyref 條件約束產生關聯性</span><span class="sxs-lookup"><span data-stu-id="5bd52-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="5bd52-110">您可以指定**msdata： Relationship**注釋，而不是指定 [索引鍵] 和 [keyref 條件約束]，而在 XML 架構對應進程期間，它不僅會產生條件約束，也會產生**資料集**內的關聯性。</span><span class="sxs-lookup"><span data-stu-id="5bd52-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="5bd52-111">不過，如果您在`msdata:ConstraintOnly="true"` **keyref**專案中指定，**資料集**只會包含條件約束，而且不會包含關聯性。</span><span class="sxs-lookup"><span data-stu-id="5bd52-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="5bd52-112">下列範例顯示的 XML 架構包含不是嵌套的**Order**和**OrderDetail**元素。</span><span class="sxs-lookup"><span data-stu-id="5bd52-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="5bd52-113">結構描述也指定索引鍵條件約束和 keyref 條件約束。</span><span class="sxs-lookup"><span data-stu-id="5bd52-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="5bd52-114">XML 架構對應進程期間所產生的**資料集**包含**Order**和**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="5bd52-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="5bd52-115">此外，**資料集**還包含關聯性和條件約束。</span><span class="sxs-lookup"><span data-stu-id="5bd52-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="5bd52-116">下列範例會顯示這些關聯性和條件約束。</span><span class="sxs-lookup"><span data-stu-id="5bd52-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="5bd52-117">請注意，此架構不會指定**msdata： Relationship**注釋;相反地，key 和 keyref 條件約束是用來產生關聯。</span><span class="sxs-lookup"><span data-stu-id="5bd52-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```  
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
  
 <span data-ttu-id="5bd52-118">在先前的架構範例中， **Order**和**OrderDetail**元素不是嵌套的。</span><span class="sxs-lookup"><span data-stu-id="5bd52-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="5bd52-119">下列的結構描述範例中，這些項目則為巢狀化。</span><span class="sxs-lookup"><span data-stu-id="5bd52-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="5bd52-120">不過，未指定**msdata： Relationship**注釋;因此，會假設使用隱含關聯。</span><span class="sxs-lookup"><span data-stu-id="5bd52-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="5bd52-121">如需詳細資訊，請參閱[對應嵌套架構元素之間的隱含](map-implicit-relations-between-nested-schema-elements.md)關聯。</span><span class="sxs-lookup"><span data-stu-id="5bd52-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="5bd52-122">結構描述也指定索引鍵條件約束和 keyref 條件約束。</span><span class="sxs-lookup"><span data-stu-id="5bd52-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="5bd52-123">XML 架構對應進程所產生的**資料集**包含兩個數據表：</span><span class="sxs-lookup"><span data-stu-id="5bd52-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="5bd52-124">**DataSet**也包含兩個關聯性（一個以**msdata： relationship**注釋為基礎，另一個依據索引鍵和 keyref 條件約束）和各種條件約束。</span><span class="sxs-lookup"><span data-stu-id="5bd52-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="5bd52-125">下列範例顯示關聯和條件約束。</span><span class="sxs-lookup"><span data-stu-id="5bd52-125">The following example shows the relations and constraints.</span></span>  
  
```  
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
  
 <span data-ttu-id="5bd52-126">如果參考嵌套資料表的 keyref 條件約束包含**msdata： IsNested = "true"** 注釋，**資料集**將會建立以 keyref 條件約束和相關 unique/key 條件約束為基礎的單一嵌套關聯性。</span><span class="sxs-lookup"><span data-stu-id="5bd52-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd52-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bd52-127">See also</span></span>

- [<span data-ttu-id="5bd52-128">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="5bd52-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="5bd52-129">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="5bd52-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
