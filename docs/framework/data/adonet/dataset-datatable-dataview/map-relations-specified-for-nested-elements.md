---
title: 針對巢狀項目指定的關聯進行對應
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: e8cdf73b6277abdaab1256ca87e615a5e25e7336
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786093"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="61ebe-102">針對巢狀項目指定的關聯進行對應</span><span class="sxs-lookup"><span data-stu-id="61ebe-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="61ebe-103">架構可以包含**msdata： Relationship**注釋，以明確指定架構中任何兩個元素之間的對應。</span><span class="sxs-lookup"><span data-stu-id="61ebe-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="61ebe-104">**Msdata： Relationship**中指定的兩個元素可以嵌套在架構中，但不一定要是。</span><span class="sxs-lookup"><span data-stu-id="61ebe-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="61ebe-105">對應進程會在架構中使用**msdata： Relationship** ，以產生兩個數據行之間的主鍵/外鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="61ebe-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="61ebe-106">下列範例顯示 XML 架構，其中**OrderDetail**元素是**Order**的子專案。</span><span class="sxs-lookup"><span data-stu-id="61ebe-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="61ebe-107">**Msdata： Relationship**會識別此父子式關聯性，並指定產生之**Order**資料表的**OrderNumber**資料行與產生的**OrderDetail**資料表的**OrderNo**資料行相關聯。</span><span class="sxs-lookup"><span data-stu-id="61ebe-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
       <xs:element name="OrderNumber" type="xs:string" />  
       <xs:element name="EmpNumber" type="xs:string" />  
       <xs:element name="OrderDetail">  
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"   
                                msdata:parent="Order"   
                                msdata:child="OrderDetail"   
                                msdata:parentkey="OrderNumber"   
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
          <xs:complexType>  
            <xs:sequence>  
             <xs:element name="OrderNo" type="xs:string" />  
             <xs:element name="ItemNo" type="xs:string" />  
            </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:sequence>  
    </xs:complexType>  
   </xs:element>  
  </xs:choice>  
 </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="61ebe-108">XML 結構描述對應處理序會在 <xref:System.Data.DataSet> 內建立下列各項：</span><span class="sxs-lookup"><span data-stu-id="61ebe-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="61ebe-109">**Order**和**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="61ebe-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="61ebe-110">**Order**和**OrderDetail**資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="61ebe-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="61ebe-111">此關聯性的**Nested**屬性會設定為**True** ，因為**Order**和**OrderDetail**專案會嵌套在架構中。</span><span class="sxs-lookup"><span data-stu-id="61ebe-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="61ebe-112">對應處理序未建立任何條件約束。</span><span class="sxs-lookup"><span data-stu-id="61ebe-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ebe-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61ebe-113">See also</span></span>

- [<span data-ttu-id="61ebe-114">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="61ebe-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="61ebe-115">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="61ebe-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="61ebe-116">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="61ebe-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
