---
title: "從 XML 結構描述 (XSD) 衍生資料集關聯式結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eb4f6e3a63c901ec69ca5572a6f79d2f0ac4adfc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>從 XML 結構描述 (XSD) 衍生資料集關聯式結構
這個章節提供如何從 XML 結構描述定義語言 (XSD) 結構描述文件來建置 `DataSet` 關聯式結構描述的概觀。 一般情況下，每個`complexType`結構描述元素的子元素，在中，所產生的資料表`DataSet`。 資料表結構由複雜型別的定義來決定。 資料表會建立在`DataSet`結構描述中的最上層項目。 不過，會僅針對建立資料表的最上層`complexType`項目時`complexType`內的另一個巢狀項目`complexType`中的項目大小寫的巢狀`complexType`元素會對應至`DataTable`內`DataSet`。  
  
 如需 XSD 的詳細資訊，請參閱全球資訊網協會 (W3C) XML 結構描述第 0： 入門建議事項，XML 結構描述第 1 部分： 結構建議和 XML 結構描述第 2 部分： datatypes > 建議，位於[http://www.w3.org/](http://www.w3.org/TR/)。  
  
 下列範例會示範 XML 結構描述位置`customers`是元素的子元素`MyDataSet`項目，這是**資料集**項目。  
  
```xml  
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
  
 上述範例中，`customers` 項目為複雜型別項目。 因此，複雜型別定義會經過剖析，而對應處理序則會產生下列表格。  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 資料表內每個資料行的資料型別都衍生自對應項目的 XML 結構描述型別或指定屬性。  
  
> [!NOTE]
>  如果項目`customers`是簡單的 XML 結構描述資料類型例如**整數**，不會產生資料表。 因為資料表僅會針對複雜型別的最上層項目產生。  
  
 在下列的 XML 結構描述，**結構描述**項目具有兩個項目子系，`InStateCustomers`和`OutOfStateCustomers`。  
  
```xml  
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
  
 `InStateCustomers` 和 `OutOfStateCustomers` 子項目均為複雜型別項目 (`customerType`)。 因此，對應處理序會產生下列兩個相同資料表中的`DataSet`。  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>本節內容  
 [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 說明用來建立唯一外部索引鍵條件約束中的 XML 結構描述項目`DataSet`。  
  
 [從 XML 結構描述 (XSD) 產生資料集關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 說明用來在資料表資料行間建立關聯的 XML 結構描述項目`DataSet`。  
  
 [XML 結構描述條件約束和關聯性](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 描述如何隱含建立關聯時建立條件約束中的使用 XML 結構描述項目`DataSet`。  
  
## <a name="related-sections"></a>相關章節  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 描述如何載入及保存資料與關聯式結構`DataSet`為 XML 資料。  
  
## <a name="see-also"></a>請參閱  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
