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
# <a name="map-relations-specified-for-nested-elements"></a>針對巢狀項目指定的關聯進行對應
架構可以包含**msdata： Relationship**注釋，以明確指定架構中任何兩個元素之間的對應。 **Msdata： Relationship**中指定的兩個元素可以嵌套在架構中，但不一定要是。 對應進程會在架構中使用**msdata： Relationship** ，以產生兩個數據行之間的主鍵/外鍵關聯性。  
  
 下列範例顯示 XML 架構，其中**OrderDetail**元素是**Order**的子專案。 **Msdata： Relationship**會識別此父子式關聯性，並指定產生之**Order**資料表的**OrderNumber**資料行與產生的**OrderDetail**資料表的**OrderNo**資料行相關聯。  
  
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
  
 XML 結構描述對應處理序會在 <xref:System.Data.DataSet> 內建立下列各項：  
  
- **Order**和**OrderDetail**資料表。  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- **Order**和**OrderDetail**資料表之間的關聯性。 此關聯性的**Nested**屬性會設定為**True** ，因為**Order**和**OrderDetail**專案會嵌套在架構中。  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 對應處理序未建立任何條件約束。  
  
## <a name="see-also"></a>另請參閱

- [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)
- [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET 概觀](../ado-net-overview.md)
