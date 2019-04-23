---
title: 針對巢狀項目指定的關聯進行對應
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 9772f077991c758be65bbb44b9474f1ad341371f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203141"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="2dda7-102">針對巢狀項目指定的關聯進行對應</span><span class="sxs-lookup"><span data-stu-id="2dda7-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="2dda7-103">結構描述可以包含**msdata: relationship**註釋，明確指定結構描述中任何兩個項目之間的對應。</span><span class="sxs-lookup"><span data-stu-id="2dda7-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="2dda7-104">中指定的兩個元素**msdata: relationship**可以巢狀方式置於結構描述，但並不需要。</span><span class="sxs-lookup"><span data-stu-id="2dda7-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="2dda7-105">對應處理會使用**msdata: relationship**結構描述產生主索引鍵/外部索引鍵關聯性之間的兩個資料行中。</span><span class="sxs-lookup"><span data-stu-id="2dda7-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="2dda7-106">下列範例顯示 XML 結構描述所在**OrderDetail**項目是子元素**順序**。</span><span class="sxs-lookup"><span data-stu-id="2dda7-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="2dda7-107">**Msdata: relationship**識別此父子式關聯性，並指定**OrderNumber**產生的資料行**順序**相關資料表**OrderNo**產生的資料行**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="2dda7-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="2dda7-108">XML 結構描述對應處理序會在 <xref:System.Data.DataSet> 內建立下列各項：</span><span class="sxs-lookup"><span data-stu-id="2dda7-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="2dda7-109">**順序**並**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="2dda7-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="2dda7-110">之間的關聯性**順序**並**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="2dda7-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="2dda7-111">**巢狀**此關聯性的屬性設定為 **，則為 True**因為**Order**並**OrderDetail**元素的巢狀結構描述中.</span><span class="sxs-lookup"><span data-stu-id="2dda7-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="2dda7-112">對應處理序未建立任何條件約束。</span><span class="sxs-lookup"><span data-stu-id="2dda7-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dda7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dda7-113">See also</span></span>

- [<span data-ttu-id="2dda7-114">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="2dda7-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="2dda7-115">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="2dda7-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="2dda7-116">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="2dda7-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
