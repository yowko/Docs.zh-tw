---
title: 將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 4aa94dfaf088a2a934c8901e2720f166d3a38dae
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784416"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="607ce-102">將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="607ce-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="607ce-103">在 XML 架構定義語言（XSD）架構中， **unique**專案會指定元素或屬性的唯一性條件約束。</span><span class="sxs-lookup"><span data-stu-id="607ce-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="607ce-104">在將 XML 結構描述轉譯到關聯式結構描述的處理序中，會將 XML 結構描述內項目或屬性上指定的唯一的條件約束 (Constraint)，對應到所產生的對應 <xref:System.Data.DataTable> 內 <xref:System.Data.DataSet> 的唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="607ce-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="607ce-105">下表列出您可以在**unique**元素中指定的**msdata**屬性。</span><span class="sxs-lookup"><span data-stu-id="607ce-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="607ce-106">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="607ce-106">Attribute name</span></span>|<span data-ttu-id="607ce-107">描述</span><span class="sxs-lookup"><span data-stu-id="607ce-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="607ce-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="607ce-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="607ce-109">如果指定這個屬性，則它的值會被當成條件約束名稱使用。</span><span class="sxs-lookup"><span data-stu-id="607ce-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="607ce-110">否則， **name**屬性會提供條件約束名稱的值。</span><span class="sxs-lookup"><span data-stu-id="607ce-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="607ce-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="607ce-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="607ce-112">如果`PrimaryKey="true"` **unique**元素中有，則會建立 unique 條件約束，並將**IsPrimaryKey**屬性設定為**true**。</span><span class="sxs-lookup"><span data-stu-id="607ce-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="607ce-113">下列範例顯示使用**unique**專案指定唯一性條件約束的 XML 架構。</span><span class="sxs-lookup"><span data-stu-id="607ce-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="607ce-114">架構中的**unique**元素會針對檔實例中的所有**Customers**元素指定， **CustomerID**子項目的值必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="607ce-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="607ce-115">在建立**資料集**時，對應進程會讀取此架構，並產生下列資料表：</span><span class="sxs-lookup"><span data-stu-id="607ce-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="607ce-116">對應進程也會在**CustomerID**資料行上建立 unique 條件約束，如下列**資料集**所示。</span><span class="sxs-lookup"><span data-stu-id="607ce-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="607ce-117">(為了便於了解，此處僅顯示相關屬性)。</span><span class="sxs-lookup"><span data-stu-id="607ce-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
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
  
 <span data-ttu-id="607ce-118">在產生的**資料集中**，unique 條件約束的**IsPrimaryKey**屬性會設定為**False** 。</span><span class="sxs-lookup"><span data-stu-id="607ce-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="607ce-119">資料行上的**unique**屬性工作表示**CustomerID**資料行值必須是唯一的（但它們可以是 null 參考，如資料行的**AllowDBNull**屬性所指定）。</span><span class="sxs-lookup"><span data-stu-id="607ce-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="607ce-120">如果您修改架構，並將選擇性的**msdata： PrimaryKey**屬性值設定為**True**，則會在資料表上建立 unique 條件約束。</span><span class="sxs-lookup"><span data-stu-id="607ce-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="607ce-121">**AllowDBNull**資料行屬性設定為**False**，而條件約束的**IsPrimaryKey**屬性設定為**True**，因此**CustomerID**資料行是主鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="607ce-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="607ce-122">您可以在 XML 結構描述中，將唯一的條件約束指定給合併的項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="607ce-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="607ce-123">下列範例示範如何在架構中加入另一個**xs： field**元素，以指定在任何實例中，所有**客戶**的**CustomerID**和**名稱**值的組合都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="607ce-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="607ce-124">這是在產生的**資料集中**建立的條件約束。</span><span class="sxs-lookup"><span data-stu-id="607ce-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="607ce-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="607ce-125">See also</span></span>

- [<span data-ttu-id="607ce-126">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="607ce-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="607ce-127">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="607ce-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="607ce-128">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="607ce-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
