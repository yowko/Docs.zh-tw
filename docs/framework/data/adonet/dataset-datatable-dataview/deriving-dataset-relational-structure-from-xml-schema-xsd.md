---
title: "從 XML 結構描述 (XSD) 衍生 DataSet 關聯式結構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 從 XML 結構描述 (XSD) 衍生 DataSet 關聯式結構
這個章節提供如何從 XML 結構描述定義語言 \(XSD\) 結構描述文件來建置 <xref:System.Data.DataSet> 關聯式結構描述的概觀。  一般而言，**DataSet** 中有針對結構描述項目的每個 **complexType** 項目子系所產生的資料表。  資料表結構由複雜型別的定義來決定。  **DataSet** 中有針對結構描述內的最上層項目所建立的資料表。  但是，當 **complexType** 項目巢狀化至其他 **complexType** 項目內時，只會針對最上層的 **complexType** 項目建立資料表，也就是說，巢狀 **complexType** 項目會對應至 **DataSet** 內的 <xref:System.Data.DataTable>。  
  
 如需 XSD 的詳細資訊，請參閱全球資訊網協會 \(W3C\) 的＜XML 結構描述第零部：入門建議事項＞、＜XML 結構描述第一部：結構建議事項＞及＜XML 結構描述第二部：資料類型建議事項＞，網址：[http:\/\/www.w3.org\/](http://www.w3.org/TR/)。  
  
 下列範例會示範 XML 結構描述，其中 `customers` 是 `MyDataSet` 項目 \(這個項目是 **DataSet** 項目\) 的子項目。  
  
```  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 上述範例中，`customers` 項目為複雜型別項目。  因此，複雜型別定義會經過剖析，而對應處理序則會產生下列表格。  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 資料表內每個資料行的資料型別都衍生自對應項目的 XML 結構描述型別或指定屬性。  
  
> [!NOTE]
>  如果 `customers` 項目為簡單 XML 結構描述資料型別 \(例如 **integer**\)，則不會產生資料表。  因為資料表僅會針對複雜型別的最上層項目產生。  
  
 在下列 XML 結構描述中，**Schema** 項目具有兩個項目子系：`InStateCustomers` 和 `OutOfStateCustomers`。  
  
```  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 `InStateCustomers` 和 `OutOfStateCustomers` 子項目均為複雜型別項目 \(`customerType`\)。  所以，對應處理會在 **DataSet** 內產生下列兩個相同的表格。  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## 在本節中  
 [將 XML 結構描述 \(XSD\) 條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 說明用來在 **DataSet** 中建立唯一外部索引鍵條件約束的 XML 結構描述元素。  
  
 [從 XML 結構描述 \(XSD\) 產生 DataSet 關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 說明用來在 **DataSet** 內的資料表資料行間建立關聯的 XML 結構描述項目。  
  
 [XML 結構描述條件約束和關聯性](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 說明使用 XML 結構描述項目在 **DataSet** 內建立條件約束時，如何隱含建立關聯。  
  
## 相關章節  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 說明如何在 **DataSet** 內將關聯式結構載入和保存為 XML 資料。  
  
## 請參閱  
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)