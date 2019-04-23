---
title: 將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 650cd6b8b8149529f115f22a11d19178fbd6d302
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108221"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="aafa7-102">將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="aafa7-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="aafa7-103">中的 XML 結構描述定義語言 (XSD) 結構描述**唯一**項目會指定元素或屬性的唯一性條件約束。</span><span class="sxs-lookup"><span data-stu-id="aafa7-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="aafa7-104">在將 XML 結構描述轉譯到關聯式結構描述的處理序中，會將 XML 結構描述內項目或屬性上指定的唯一的條件約束 (Constraint)，對應到所產生的對應 <xref:System.Data.DataTable> 內 <xref:System.Data.DataSet> 的唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="aafa7-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="aafa7-105">下表列出**msdata**您可以在指定的屬性**唯一**項目。</span><span class="sxs-lookup"><span data-stu-id="aafa7-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="aafa7-106">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="aafa7-106">Attribute name</span></span>|<span data-ttu-id="aafa7-107">描述</span><span class="sxs-lookup"><span data-stu-id="aafa7-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="aafa7-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="aafa7-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="aafa7-109">如果指定這個屬性，則它的值會被當成條件約束名稱使用。</span><span class="sxs-lookup"><span data-stu-id="aafa7-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="aafa7-110">否則，請**名稱**屬性提供值的條件約束名稱。</span><span class="sxs-lookup"><span data-stu-id="aafa7-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="aafa7-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="aafa7-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="aafa7-112">如果`PrimaryKey="true"`存在於**唯一**項目，唯一的條件約束會建立具有**IsPrimaryKey**屬性設為**true**。</span><span class="sxs-lookup"><span data-stu-id="aafa7-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="aafa7-113">下列範例示範使用 XML 結構描述**唯一**項目指定唯一性條件約束。</span><span class="sxs-lookup"><span data-stu-id="aafa7-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="aafa7-114">**唯一**結構描述中的項目指定所有**客戶**文件中的項目執行個體的值**CustomerID**必須是唯一的子元素。</span><span class="sxs-lookup"><span data-stu-id="aafa7-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="aafa7-115">在建置**資料集**，對應處理序讀取這個結構描述，並產生下表：</span><span class="sxs-lookup"><span data-stu-id="aafa7-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="aafa7-116">對應處理序也上建立 unique 條件約束**CustomerID**資料行，如下所示**DataSet**。</span><span class="sxs-lookup"><span data-stu-id="aafa7-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="aafa7-117">(為了便於了解，此處僅顯示相關屬性)。</span><span class="sxs-lookup"><span data-stu-id="aafa7-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="aafa7-118">在 **資料集**產生， **IsPrimaryKey**屬性設定為**False**唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="aafa7-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="aafa7-119">**唯一**資料行上的屬性是指出**CustomerID**資料行的值必須是唯一 (但可以是 null 參考，必須按照**AllowDBNull**屬性的資料行）。</span><span class="sxs-lookup"><span data-stu-id="aafa7-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="aafa7-120">如果您修改結構描述，並將選用**msdata**屬性值來 **，則為 True**，資料表上建立 unique 條件約束。</span><span class="sxs-lookup"><span data-stu-id="aafa7-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="aafa7-121">**AllowDBNull**資料行屬性設定為**False**，而**IsPrimaryKey**屬性設定為條件約束**True**，即可使**CustomerID**資料行主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="aafa7-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="aafa7-122">您可以在 XML 結構描述中，將唯一的條件約束指定給合併的項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="aafa7-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="aafa7-123">下列範例示範如何指定，多種**CustomerID**並**CompanyName**的值必須是唯一的所有**客戶**在任何情況下，由新增另一個**customers**結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="aafa7-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="aafa7-124">這是建立在產生的條件約束**資料集**。</span><span class="sxs-lookup"><span data-stu-id="aafa7-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="aafa7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aafa7-125">See also</span></span>

- [<span data-ttu-id="aafa7-126">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="aafa7-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="aafa7-127">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="aafa7-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="aafa7-128">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="aafa7-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
