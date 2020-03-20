---
title: 將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 5ebf333b065157fa9497cc1471a45698663638e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150931"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="c91ab-102">將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="c91ab-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="c91ab-103">在架構中，可以使用**鍵**元素對元素或屬性指定鍵約束。</span><span class="sxs-lookup"><span data-stu-id="c91ab-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="c91ab-104">具有指定索引鍵條件約束的項目或屬性，在任何結構描述執行個體中都必須具有唯一的值，且不可具有 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c91ab-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="c91ab-105">索引鍵條件約束類似唯一的條件約束，唯一的不同處定義索引鍵條件約束的資料行不能有 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c91ab-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="c91ab-106">下表概述了可在**鍵**元素中指定的**msdata**屬性。</span><span class="sxs-lookup"><span data-stu-id="c91ab-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="c91ab-107">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="c91ab-107">Attribute name</span></span>|<span data-ttu-id="c91ab-108">描述</span><span class="sxs-lookup"><span data-stu-id="c91ab-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c91ab-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="c91ab-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="c91ab-110">如果指定這個屬性，則它的值會被當成條件約束名稱使用。</span><span class="sxs-lookup"><span data-stu-id="c91ab-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="c91ab-111">否則，**名稱**屬性提供約束名稱的值。</span><span class="sxs-lookup"><span data-stu-id="c91ab-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="c91ab-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="c91ab-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="c91ab-113">如果存在`PrimaryKey="true"`**，IsPrimaryKey**約束屬性設置為**true，** 從而使其成為主鍵。</span><span class="sxs-lookup"><span data-stu-id="c91ab-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="c91ab-114">**AllowDBNull**列屬性設置為**false，** 因為主鍵不能具有 null 值。</span><span class="sxs-lookup"><span data-stu-id="c91ab-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="c91ab-115">在轉換指定鍵約束的架構時，映射過程在表上創建一個唯一約束，其中**AllowDBNull**列屬性設置為約束中每列**false。**</span><span class="sxs-lookup"><span data-stu-id="c91ab-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="c91ab-116">除非在**鍵**元素上指定`msdata:PrimaryKey="true"`，否則唯一約束的**IsPrimaryKey**屬性也設置為**false。**</span><span class="sxs-lookup"><span data-stu-id="c91ab-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="c91ab-117">它與結構描述 (其中 `PrimaryKey="true"`) 中唯一的條件約束相同。</span><span class="sxs-lookup"><span data-stu-id="c91ab-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="c91ab-118">在下面的架構示例中，**鍵**元素指定**CustomerID**元素的鍵約束。</span><span class="sxs-lookup"><span data-stu-id="c91ab-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
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
  
 <span data-ttu-id="c91ab-119">**鍵**元素指定**客戶**元素**的 CustomerID**子項目的值必須具有唯一值，並且不能具有 null 值。</span><span class="sxs-lookup"><span data-stu-id="c91ab-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="c91ab-120">轉譯 XML 結構描述定義語言 (XSD) 結構描述的過程中，對應處理序會建立下表：</span><span class="sxs-lookup"><span data-stu-id="c91ab-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="c91ab-121">XML 架構映射還會在**CustomerID**列上創建**唯一約束**，如下所示。 <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="c91ab-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c91ab-122">(為了便於了解，此處僅顯示相關屬性)。</span><span class="sxs-lookup"><span data-stu-id="c91ab-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
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
  
 <span data-ttu-id="c91ab-123">在生成的**DataSet**中，**唯一約束**的**IsPrimaryKey**屬性設置為**true，** 因為架構在`msdata:PrimaryKey="true"`**鍵**元素中指定。</span><span class="sxs-lookup"><span data-stu-id="c91ab-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="c91ab-124">**DataSet**中**唯一約束**屬性**的約束名稱**屬性的值是架構中**鍵**元素中指定的**msdata：約束名稱**屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c91ab-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91ab-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c91ab-125">See also</span></span>

- [<span data-ttu-id="c91ab-126">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="c91ab-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="c91ab-127">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="c91ab-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- <span data-ttu-id="c91ab-128">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="c91ab-128">[ADO.NET Overview](../ado-net-overview.md)</span></span>
