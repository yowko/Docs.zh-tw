---
title: "對應針對巢狀項目所指定的關聯 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 對應針對巢狀項目所指定的關聯
結構描述可包含 **msdata:Relationship** 註釋，以明確指定結構描述內任何兩個項目間的對應。  **msdata:Relationship** 中指定的兩個項目可以 \(但非必要\) 在結構描述內進行巢狀化。  對應處理序在結構描述中使用 **msdata:Relationship**，以在兩個資料行間產生主索引鍵\/外部索引鍵關係。  
  
 下列範例顯示的 XML 結構描述中，**OrderDetail** 項目為 **Order** 的項目子系。  **msdata:Relationship** 識別了這個父子關係，並指定在產生的 **Order** 資料表的 **OrderNumber** 資料行與產生的 **OrderDetail** 資料表的 **OrderNo** 資料行之間有關聯。  
  
```  
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
  
-   **Order** 和 **OrderDetail** 資料表。  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   **Order** 和 **OrderDetail** 資料表間的關聯性。  這項關聯性的 **Nested** 屬性設定為 **True**，因為 **Order** 和 **OrderDetail** 元素會巢狀化至結構描述內。  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 對應處理序未建立任何條件約束。  
  
## 請參閱  
 [從 XML 結構描述 \(XSD\) 產生 DataSet 關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [將 XML 結構描述 \(XSD\) 條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)