---
title: 將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150879"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="59c4e-102">將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="59c4e-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="59c4e-103">**keyref**元素允許您在文檔中的元素之間建立連結。</span><span class="sxs-lookup"><span data-stu-id="59c4e-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="59c4e-104">這與關聯式資料庫中的外部索引鍵關聯性很類似。</span><span class="sxs-lookup"><span data-stu-id="59c4e-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="59c4e-105">如果架構指定**keyref**元素，則在架構映射過程中將元素轉換為 對<xref:System.Data.DataSet>表中的列的相應外鍵約束。</span><span class="sxs-lookup"><span data-stu-id="59c4e-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="59c4e-106">預設情況下 **，keyref**元素還會生成一個關係，該關係在關係上指定了**父表**、**子表**、**父列**和**子列**屬性。</span><span class="sxs-lookup"><span data-stu-id="59c4e-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="59c4e-107">下表概述了可在**keyref**元素中指定的**msdata**屬性。</span><span class="sxs-lookup"><span data-stu-id="59c4e-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="59c4e-108">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="59c4e-108">Attribute name</span></span>|<span data-ttu-id="59c4e-109">描述</span><span class="sxs-lookup"><span data-stu-id="59c4e-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="59c4e-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="59c4e-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="59c4e-111">如果在架構中的**keyref**元素上指定了 **"約束唯一""true"，** 則將創建約束，但不創建任何關係。</span><span class="sxs-lookup"><span data-stu-id="59c4e-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="59c4e-112">如果未指定此屬性（或設置為**False），** 則約束和關係都在**DataSet 中**創建。</span><span class="sxs-lookup"><span data-stu-id="59c4e-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="59c4e-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="59c4e-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="59c4e-114">如果指定了 **"約束名稱"** 屬性，則其值將用作約束的名稱。</span><span class="sxs-lookup"><span data-stu-id="59c4e-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="59c4e-115">否則，架構中**keyref**元素**的名稱**屬性在**DataSet**中提供約束名稱。</span><span class="sxs-lookup"><span data-stu-id="59c4e-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="59c4e-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="59c4e-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="59c4e-117">如果在架構中的**keyref**元素中指定**了 UpdateRule**屬性，則其值將分配給**DataSet**中的**UpdateRule**約束屬性。</span><span class="sxs-lookup"><span data-stu-id="59c4e-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="59c4e-118">否則 **，UpdateRule**屬性將設置為**級聯**。</span><span class="sxs-lookup"><span data-stu-id="59c4e-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="59c4e-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="59c4e-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="59c4e-120">如果在架構中的**keyref**元素中指定**了 DeleteRule**屬性，則其值將分配給**DataSet**中的**DeleteRule**約束屬性。</span><span class="sxs-lookup"><span data-stu-id="59c4e-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="59c4e-121">否則 **，DeleteRule**屬性將設置為**級聯**。</span><span class="sxs-lookup"><span data-stu-id="59c4e-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="59c4e-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="59c4e-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="59c4e-123">如果在架構中的**keyref**元素中指定了**AcceptRejectRule 屬性**，則其值將分配給**DataSet**中的**AcceptRejectRule**約束屬性。</span><span class="sxs-lookup"><span data-stu-id="59c4e-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="59c4e-124">否則，"**接受拒絕規則"** 屬性將設置為 **"無**"。</span><span class="sxs-lookup"><span data-stu-id="59c4e-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="59c4e-125">下面的示例包含一個架構，該架構指定**Order**元素的**OrderNumber**子項目和**OrderDetail**元素的**OrderNo**子項目之間的**鍵**和**鍵 ref**關係。</span><span class="sxs-lookup"><span data-stu-id="59c4e-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="59c4e-126">在此示例中，"**訂單詳細資訊"** 元素的**OrderNumber**子項目引用**訂單**元素的 **"訂單無**"鍵子項目。</span><span class="sxs-lookup"><span data-stu-id="59c4e-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="59c4e-127">XML 架構定義語言 （XSD） 架構映射過程生成具有兩個表的以下**DataSet：**</span><span class="sxs-lookup"><span data-stu-id="59c4e-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="59c4e-128">此外，**資料集**定義以下約束：</span><span class="sxs-lookup"><span data-stu-id="59c4e-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="59c4e-129">**訂單**表上的唯一約束。</span><span class="sxs-lookup"><span data-stu-id="59c4e-129">A unique constraint on the **Order** table.</span></span>  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="59c4e-130">**訂單**和**訂單詳細資訊**表之間的關係。</span><span class="sxs-lookup"><span data-stu-id="59c4e-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="59c4e-131">**嵌套**屬性設置為**False，** 因為兩個元素未嵌套在架構中。</span><span class="sxs-lookup"><span data-stu-id="59c4e-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="59c4e-132">**"訂單詳細資訊**"表上的外鍵約束。</span><span class="sxs-lookup"><span data-stu-id="59c4e-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a><span data-ttu-id="59c4e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59c4e-133">See also</span></span>

- [<span data-ttu-id="59c4e-134">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="59c4e-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="59c4e-135">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="59c4e-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- <span data-ttu-id="59c4e-136">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="59c4e-136">[ADO.NET Overview](../ado-net-overview.md)</span></span>
