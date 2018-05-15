---
title: 將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: ad39fd75a3f8872ed2c24a65481209e3c772a638
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="176b4-102">將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="176b4-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="176b4-103">在結構描述中，您可以指定的項目上的索引鍵條件約束，或屬性使用**金鑰**項目。</span><span class="sxs-lookup"><span data-stu-id="176b4-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="176b4-104">具有指定索引鍵條件約束的項目或屬性，在任何結構描述執行個體中都必須具有唯一的值，且不可具有 Null 值。</span><span class="sxs-lookup"><span data-stu-id="176b4-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="176b4-105">索引鍵條件約束類似唯一的條件約束，唯一的不同處定義索引鍵條件約束的資料行不能有 Null 值。</span><span class="sxs-lookup"><span data-stu-id="176b4-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="176b4-106">下表概述**msdata**屬性中，您可以指定**金鑰**項目。</span><span class="sxs-lookup"><span data-stu-id="176b4-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="176b4-107">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="176b4-107">Attribute name</span></span>|<span data-ttu-id="176b4-108">描述</span><span class="sxs-lookup"><span data-stu-id="176b4-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="176b4-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="176b4-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="176b4-110">如果指定這個屬性，則它的值會被當成條件約束名稱使用。</span><span class="sxs-lookup"><span data-stu-id="176b4-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="176b4-111">否則，**名稱**屬性提供條件約束名稱的值。</span><span class="sxs-lookup"><span data-stu-id="176b4-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="176b4-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="176b4-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="176b4-113">如果`PrimaryKey="true"`沒有、 **IsPrimaryKey**條件約束屬性設定為**true**，因此讓它成為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="176b4-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="176b4-114">**AllowDBNull**資料行屬性設定為**false**，因為主索引鍵不能有 null 值。</span><span class="sxs-lookup"><span data-stu-id="176b4-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="176b4-115">在轉換結構描述在指定索引鍵條件約束時，對應處理序會建立唯一條件約束的資料表上**AllowDBNull** column 屬性設定為**false**中每個資料行條件約束。</span><span class="sxs-lookup"><span data-stu-id="176b4-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="176b4-116">**IsPrimaryKey**唯一條件約束的屬性也會設為**false**除非您已指定`msdata:PrimaryKey="true"`上**金鑰**項目。</span><span class="sxs-lookup"><span data-stu-id="176b4-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="176b4-117">它與結構描述 (其中 `PrimaryKey="true"`) 中唯一的條件約束相同。</span><span class="sxs-lookup"><span data-stu-id="176b4-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="176b4-118">在下列結構描述範例中，**金鑰**元素上指定索引鍵條件約束**CustomerID**項目。</span><span class="sxs-lookup"><span data-stu-id="176b4-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>   
```  
  
 <span data-ttu-id="176b4-119">**金鑰**項目指定的值**CustomerID**子項目**客戶**項目必須具有唯一值，並不能有 null 值。</span><span class="sxs-lookup"><span data-stu-id="176b4-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="176b4-120">轉譯 XML 結構描述定義語言 (XSD) 結構描述的過程中，對應處理序會建立下表：</span><span class="sxs-lookup"><span data-stu-id="176b4-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="176b4-121">XML 結構描述對應也會建立**UniqueConstraint**上**CustomerID**資料行，如下所示<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="176b4-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="176b4-122">(為了便於了解，此處僅顯示相關屬性)。</span><span class="sxs-lookup"><span data-stu-id="176b4-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID   
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="176b4-123">在**資料集**所產生， **IsPrimaryKey**屬性**UniqueConstraint**設**true**因為結構描述指定`msdata:PrimaryKey="true"`中**金鑰**項目。</span><span class="sxs-lookup"><span data-stu-id="176b4-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="176b4-124">值**ConstraintName**屬性**UniqueConstraint**中**資料集**值**即**屬性中指定**金鑰**結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="176b4-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176b4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="176b4-125">See Also</span></span>  
 [<span data-ttu-id="176b4-126">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="176b4-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="176b4-127">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="176b4-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="176b4-128">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="176b4-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
