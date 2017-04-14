---
title: "從 XML 結構描述 (XSD) 產生 DataSet 關聯 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 從 XML 結構描述 (XSD) 產生 DataSet 關聯
您可以在 <xref:System.Data.DataSet> 內建立父子關係，以建立兩個或多個資料行之間的關聯。  有三種方法可表示 XML 結構描述定義語言 \(XSD\) 結構描述內的 **DataSet** 關聯：  
  
-   指定巢狀複雜類型。  
  
-   使用 **msdata:Relationship** 註釋。  
  
-   指定 **xs:keyref** 且不使用 **msdata:ConstraintOnly** 註釋。  
  
## 巢狀複雜類型  
 結構描述中的巢狀複雜類型定義表示項目的父子關係。  下列 XML 結構描述片段顯示 **OrderDetail** 是 **Order** 項目的項目子系。  
  
```  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 XML 結構描述對應處理會在 **DataSet** 內建立的資料表，該資料表對應至結構描述中的巢狀複雜類型。  它也會建立其他資料行，做為所產生之資料表的父子資料行。  請注意，這些父子資料行可指定關聯性，這與指定主索引鍵\/外部索引鍵條件約束不同。  
  
## msdata:Relationship 註釋  
 **msdata:Relationship** 註釋可讓您在結構描述中無巢狀的項目間，明確地指定父子關係。  下列範例會顯示 **Relationship** 項目的結構。  
  
```  
  
  <msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 **msdata:Relationship** 註釋的屬性會識別父子關係包含的項目，以及關係中所牽涉的 **parentkey** 和 **childkey** 項目與屬性。  對應處理會使用這項資訊在 **DataSet** 中產生資料表，並在這些資料表間建立主索引鍵\/外部索引鍵關係。  
  
 例如，下列結構描述片段中指定同一層級的 **Order** 和 **OrderDetail** 項目 \(無巢狀結構\)。  結構描述指定了 **msdata:Relationship** 註釋，用於指定這兩個項目間的父子關係。  在此情況下，即需使用 **msdata:Relationship** 註釋以明確地指定關係。  
  
```  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
  
```  
  
 對應處理會使用 **Relationship** 項目，於 **DataSet** 中 **Order** 資料表的 **OrderNumber** 資料行，以及 **OrderDetail** 資料表的 **OrderNo** 資料行間建立父子關係。  對應處理只會指定關係，而不會像關聯式資料庫的主索引鍵\/外部索引鍵條件約束一樣，自動為這些資料行的值指定任何條件約束。  
  
### 本章節內容  
 [對應巢狀結構描述項目間的隱含關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 說明當 XML 結構描述中發現巢狀項目時，在 **DataSet** 中隱含建立的條件約束和關聯。  
  
 [對應針對巢狀項目所指定的關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 說明如何在 **DataSet** 中為 XML 結構描述的巢狀項目明確設定關聯。  
  
 [指定無巢狀項目間的關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 說明如何在 **DataSet** 中，建立無巢狀的 XML 結構描述項目間的關聯。  
  
### 相關章節  
 [從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 說明 XML 結構描述定義語言 \(XSD\) 的結構描述所建立的 **DataSet** 關聯式結構 \(或結構描述\)。  
  
 [將 XML 結構描述 \(XSD\) 條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 說明用來在 **DataSet** 中建立唯一外部索引鍵條件約束的 XML 結構描述元素。  
  
## 請參閱  
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)