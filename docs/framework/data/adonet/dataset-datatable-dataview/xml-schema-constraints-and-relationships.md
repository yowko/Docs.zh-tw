---
title: XML 結構描述條件約束和關聯性
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: bcb6e257a40040701612b73768a98e056bccd6c5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785608"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="1b6ac-102">XML 結構描述條件約束和關聯性</span><span class="sxs-lookup"><span data-stu-id="1b6ac-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="1b6ac-103">中的 XML 結構描述定義語言 (XSD) 結構描述中，您可以指定條件約束 (唯一的索引鍵和 keyref 條件約束) 和關聯性 (使用**msdata: relationship**註釋)。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="1b6ac-104">這個主題會說明 XML 結構描述中指定的條件約束和關聯性如何經過解譯以產生 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="1b6ac-105">一般情況下，在 XML 結構描述中，您可以指定**msdata: relationship**如果您想要只產生關聯性中的註釋**DataSet**。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="1b6ac-106">如需詳細資訊，請參閱 <<c0> [ 產生從 XML 結構描述 (XSD) 的資料集關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="1b6ac-107">指定條件約束 (唯一的索引鍵和 keyref) 如果您想要產生的條件約束**資料集**。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="1b6ac-108">請注意，索引鍵條件約束和 keyref 條件約束也用於產生關聯性，詳情請見這個主題的後續說明。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="1b6ac-109">從索引鍵條件約束和 keyref 條件約束產生關聯性</span><span class="sxs-lookup"><span data-stu-id="1b6ac-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="1b6ac-110">而不是指定**msdata: relationship**註解，您可以指定索引鍵和 keyref XML 結構描述對應處理序時使用，以產生中的條件約束不僅關聯性的條件約束**資料集**。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="1b6ac-111">不過，如果您指定`msdata:ConstraintOnly="true"`中**keyref**項目**DataSet**會包含條件約束，而不會包含關聯性。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="1b6ac-112">下列範例顯示 XML 結構描述，其中包含**順序**並**OrderDetail**無巢狀項目。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="1b6ac-113">結構描述也指定索引鍵條件約束和 keyref 條件約束。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="1b6ac-114">**資料集**XML 結構描述對應處理程序包括期間產生**順序**並**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="1b6ac-115">颾魤 ㄛ**資料集**包含關聯性和條件約束。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="1b6ac-116">下列範例會顯示這些關聯性和條件約束。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="1b6ac-117">請注意，未指定結構描述**msdata: relationship**註釋，相反地，將索引鍵和 keyref 條件約束用來產生關聯。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
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
  
 <span data-ttu-id="1b6ac-118">在先前的結構描述範例中，**順序**並**OrderDetail**無巢狀項目。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="1b6ac-119">下列的結構描述範例中，這些項目則為巢狀化。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="1b6ac-120">不過，沒有**msdata: relationship**註解會指定; 因此，假設隱含關聯。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="1b6ac-121">如需詳細資訊，請參閱 <<c0> [ 地圖隱含關聯之間巢狀結構描述元素](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="1b6ac-122">結構描述也指定索引鍵條件約束和 keyref 條件約束。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="1b6ac-123">**資料集**所產生的 XML 結構描述對應處理序包含兩個資料表：</span><span class="sxs-lookup"><span data-stu-id="1b6ac-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="1b6ac-124">**資料集**也包含兩個關聯性 (一個是根據**msdata: relationship**註解和其他為基礎的索引鍵和 keyref 條件約束) 和各種條件約束。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="1b6ac-125">下列範例顯示關聯和條件約束。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-125">The following example shows the relations and constraints.</span></span>  
  
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
  
 <span data-ttu-id="1b6ac-126">如果 keyref 條件約束參考巢狀資料表包含**msdata: isnested ="true"** 註解**資料集**會建立單一的巢狀關聯性為基礎的 keyref 條件約束，相關的唯一的/索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="1b6ac-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b6ac-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b6ac-127">See Also</span></span>  
 [<span data-ttu-id="1b6ac-128">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="1b6ac-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="1b6ac-129">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="1b6ac-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
