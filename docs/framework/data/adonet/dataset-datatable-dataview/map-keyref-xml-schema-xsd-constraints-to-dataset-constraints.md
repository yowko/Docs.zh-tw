---
title: 將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 86bc1961fb23b0b2f98a2849eaabd4eecd65cd64
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777544"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="e1457-102">將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="e1457-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="e1457-103">**Keyref**元素可讓您建立文件內的項目之間的連結。</span><span class="sxs-lookup"><span data-stu-id="e1457-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="e1457-104">這與關聯式資料庫中的外部索引鍵關聯性很類似。</span><span class="sxs-lookup"><span data-stu-id="e1457-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="e1457-105">如果指定了結構描述**keyref**項目，項目會轉換至對應外部索引鍵條件約束的資料表中的資料行的結構描述對應程序<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="e1457-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e1457-106">根據預設， **keyref**項目也會產生關聯，以**ParentTable**， **ChildTable**， **ParentColumn**，以及**ChildColumn**在關聯上指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1457-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="e1457-107">下表列出**msdata**您可以在指定的屬性**keyref**項目。</span><span class="sxs-lookup"><span data-stu-id="e1457-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="e1457-108">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="e1457-108">Attribute name</span></span>|<span data-ttu-id="e1457-109">描述</span><span class="sxs-lookup"><span data-stu-id="e1457-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e1457-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="e1457-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="e1457-111">如果**ConstraintOnly ="true"** 上指定**keyref**結構描述中的項目，建立條件約束，但不會建立關聯。</span><span class="sxs-lookup"><span data-stu-id="e1457-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="e1457-112">如果未指定此屬性 (或設為**假**)，條件約束和關聯性會建立於**資料集**。</span><span class="sxs-lookup"><span data-stu-id="e1457-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="e1457-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="e1457-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="e1457-114">如果**ConstraintName**指定屬性，則會使用該值做為條件約束的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1457-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="e1457-115">否則，請**名稱**屬性**keyref**結構描述中的項目提供中的條件約束名稱**資料集**。</span><span class="sxs-lookup"><span data-stu-id="e1457-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="e1457-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="e1457-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="e1457-117">如果**UpdateRule**屬性中指定**keyref**結構描述中的項目，其值指派給**UpdateRule**中的條件約束屬性**資料集**。</span><span class="sxs-lookup"><span data-stu-id="e1457-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="e1457-118">否則**UpdateRule**屬性設定為**Cascade**。</span><span class="sxs-lookup"><span data-stu-id="e1457-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="e1457-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="e1457-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="e1457-120">如果**DeleteRule**屬性中指定**keyref**結構描述中的項目，其值指派給**DeleteRule**中的條件約束屬性**資料集**。</span><span class="sxs-lookup"><span data-stu-id="e1457-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="e1457-121">否則**DeleteRule**屬性設定為**Cascade**。</span><span class="sxs-lookup"><span data-stu-id="e1457-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="e1457-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="e1457-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="e1457-123">如果**AcceptRejectRule**屬性中指定**keyref**結構描述中的項目，其值指派給**AcceptRejectRule** 中的條件約束屬性**資料集**。</span><span class="sxs-lookup"><span data-stu-id="e1457-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="e1457-124">否則**AcceptRejectRule**屬性設定為**無**。</span><span class="sxs-lookup"><span data-stu-id="e1457-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="e1457-125">下列範例包含指定的結構描述**金鑰**並**keyref**之間的關聯性**OrderNumber**子項目**順序**項目和**OrderNo**子項目**OrderDetail**項目。</span><span class="sxs-lookup"><span data-stu-id="e1457-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="e1457-126">在範例中， **OrderNumber**子項目**OrderDetail**項目是指**OrderNo**的索引鍵的子項目**順序**項目。</span><span class="sxs-lookup"><span data-stu-id="e1457-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="e1457-127">XML 結構描述定義語言 (XSD) 結構描述對應處理會產生下列**資料集**具有兩個資料表：</span><span class="sxs-lookup"><span data-stu-id="e1457-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="e1457-128">颾魤 ㄛ**資料集**定義下列條件約束：</span><span class="sxs-lookup"><span data-stu-id="e1457-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
-   <span data-ttu-id="e1457-129">Unique 條件約束**順序**資料表。</span><span class="sxs-lookup"><span data-stu-id="e1457-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   <span data-ttu-id="e1457-130">之間的關聯性**順序**並**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="e1457-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="e1457-131">**巢狀**屬性設定為**False**因為兩個項目無巢狀結構描述中。</span><span class="sxs-lookup"><span data-stu-id="e1457-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   <span data-ttu-id="e1457-132">上的外部索引鍵條件約束**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="e1457-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e1457-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1457-133">See Also</span></span>  
 [<span data-ttu-id="e1457-134">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="e1457-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="e1457-135">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="e1457-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="e1457-136">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e1457-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
