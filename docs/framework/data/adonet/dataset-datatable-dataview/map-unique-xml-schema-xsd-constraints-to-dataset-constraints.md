---
title: 將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150840"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="3eb1c-102">將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="3eb1c-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="3eb1c-103">在 XML 架構定義語言 （XSD） 架構中，**唯一**元素指定元素或屬性的唯一性約束。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="3eb1c-104">在將 XML 結構描述轉譯到關聯式結構描述的處理序中，會將 XML 結構描述內項目或屬性上指定的唯一的條件約束 (Constraint)，對應到所產生的對應 <xref:System.Data.DataTable> 內 <xref:System.Data.DataSet> 的唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="3eb1c-105">下表概述了可以在**唯一**元素中指定的**msdata**屬性。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="3eb1c-106">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="3eb1c-106">Attribute name</span></span>|<span data-ttu-id="3eb1c-107">描述</span><span class="sxs-lookup"><span data-stu-id="3eb1c-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="3eb1c-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="3eb1c-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="3eb1c-109">如果指定這個屬性，則它的值會被當成條件約束名稱使用。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="3eb1c-110">否則，**名稱**屬性提供約束名稱的值。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="3eb1c-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="3eb1c-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="3eb1c-112">如果`PrimaryKey="true"`存在**唯**一元素中，則使用**IsPrimaryKey**屬性設置為**true**時將創建唯一約束。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="3eb1c-113">下面的示例顯示了使用**唯**一元素指定唯一性約束的 XML 架構。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
```xml  
<xs:schema id="SampleDataSet"
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="3eb1c-114">架構中**的唯一**元素指定，對於文檔實例中的所有**客戶**元素 **，CustomerID**子項目的值必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="3eb1c-115">在構建**DataSet**時，映射過程讀取此架構並生成下表：</span><span class="sxs-lookup"><span data-stu-id="3eb1c-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="3eb1c-116">映射過程還會在**CustomerID**列上創建唯一的約束，如下**DataSet**所示。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="3eb1c-117">(為了便於了解，此處僅顯示相關屬性)。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID
      IsPrimaryKey: False  
```  
  
 <span data-ttu-id="3eb1c-118">在生成的**DataSet**中 **，IsPrimaryKey**屬性設置為唯一約束的**False。**</span><span class="sxs-lookup"><span data-stu-id="3eb1c-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="3eb1c-119">列上**的唯**一屬性指示**CustomerID**列值必須是唯一的（但它們可以是空引用，由列的**AllowDBNull**屬性指定）。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="3eb1c-120">如果修改架構並將可選**msdata：主鍵**屬性值設置為**True，** 則在表上創建唯一約束。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="3eb1c-121">**AllowDBNull**列屬性設置為**False**，約束的**IsPrimaryKey**屬性設置為**True，** 從而使**CustomerID**列成為主鍵列。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="3eb1c-122">您可以在 XML 結構描述中，將唯一的條件約束指定給合併的項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="3eb1c-123">下面的示例演示如何通過在架構中添加另一個**xs：field**元素來指定**客戶 ID** **和公司名稱**值的組合在任何情況下對所有**客戶**都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 <span data-ttu-id="3eb1c-124">這是在生成的**DataSet**中創建的約束。</span><span class="sxs-lookup"><span data-stu-id="3eb1c-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="3eb1c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eb1c-125">See also</span></span>

- [<span data-ttu-id="3eb1c-126">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="3eb1c-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="3eb1c-127">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="3eb1c-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- <span data-ttu-id="3eb1c-128">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="3eb1c-128">[ADO.NET Overview](../ado-net-overview.md)</span></span>
