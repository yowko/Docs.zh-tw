---
title: 針對巢狀項目指定的關聯進行對應
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cd652f51f01dcfa16a8b707f35c658043c20670d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150892"
---
# <a name="map-relations-specified-for-nested-elements"></a>針對巢狀項目指定的關聯進行對應
架構可以包括**msdata：關係**注釋，以顯式指定架構中任意兩個元素之間的映射。 msdata 中指定的兩個元素 **：關係**可以在架構中嵌套，但不必嵌套。 映射過程使用**msdata：** 架構中的關係來生成兩列之間的主鍵/外鍵關係。  
  
 下面的示例顯示了一個 XML 架構，其中**OrderDetail**元素是**order**的子項目。 **msdata：關係**標識此父子關係，並指定結果**訂單**表的**OrderNumber**列與生成的**訂單詳細資訊**表的 **"訂單無**"列相關。  
  
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
  
- **訂單**和**訂單詳細資訊**表。  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- **訂單**和**訂單詳細資訊**表之間的關係。 此關係的**嵌套**屬性設置為**True，** 因為 **"訂單"** 和"**訂單詳細資訊"** 元素嵌套在架構中。  
  
    ```text  
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
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
