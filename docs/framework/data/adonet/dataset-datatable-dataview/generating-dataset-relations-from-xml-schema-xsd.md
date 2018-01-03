---
title: "從 XML 結構描述 (XSD) 產生資料集關聯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 916b9ad24c2ae2334635760a520116b4c19df314
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>從 XML 結構描述 (XSD) 產生資料集關聯
您可以在 <xref:System.Data.DataSet> 內建立父子關係，以建立兩個或多個資料行之間的關聯。 有三種方式來代表**資料集**XML 結構描述定義語言 (XSD) 結構描述內的關聯性：  
  
-   指定巢狀複雜類型。  
  
-   使用**msdata: relationship**註解。  
  
-   指定**xs: keyref**沒有**msdata: constraintonly**註解。  
  
## <a name="nested-complex-types"></a>巢狀複雜類型  
 結構描述中的巢狀複雜類型定義表示項目的父子關係。 下列 XML 結構描述片段顯示**OrderDetail**是子元素的**順序**項目。  
  
```xml  
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
  
 XML 結構描述對應處理序會建立資料表中的**資料集**，對應至結構描述中的巢狀複雜類型。 它也會建立額外的資料行做為父**-**所產生之資料表的子資料行。 請注意，這些父子**-**子資料行指定關聯性，這不是指定主索引鍵/外部索引鍵條件約束相同。  
  
## <a name="msdatarelationship-annotation"></a>msdata:Relationship 註釋  
 **Msdata: relationship**註釋可讓您明確指定結構描述中無巢狀的項目之間的父子式關聯性。 下列範例顯示的結構**關聯性**項目。  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 屬性的**msdata: relationship**註解中識別的項目中的父子式關聯性，以及做為**parentkey**和**childkey**項目和屬性關聯性中。 對應處理會使用這項資訊產生資料表中的**資料集**並建立這些資料表之間主索引鍵/外部索引鍵的關係。  
  
 例如，下列結構描述片段指定**順序**和**OrderDetail**相同層級的項目 （無巢狀）。 結構描述指定**msdata: relationship**註釋，用於指定兩個元素之間的父子式關聯性。 在此情況下，明確的關聯性必須指定使用**msdata: relationship**註解。  
  
```xml  
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
  
 對應處理會使用**關聯性**項目來建立之間的父子式關聯性**OrderNumber**中的資料行**順序**資料表和**OrderNo**中的資料行**OrderDetail**資料表中**資料集**。 對應處理只會指定關係，而不會像關聯式資料庫的主索引鍵/外部索引鍵條件約束一樣，自動為這些資料行的值指定任何條件約束。  
  
### <a name="in-this-section"></a>本節內容  
 [在巢狀結構描述項目之間進行隱含關聯對應](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 描述條件約束和關聯性中隱含建立**資料集**發生 XML 結構描述中巢狀項目時。  
  
 [針對巢狀項目指定的關聯進行對應](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 描述如何在中明確設定關聯**資料集**的 XML 結構描述中的巢狀項目。  
  
 [指定未巢狀放置之項目間的關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 描述如何建立關聯性中的**資料集**無巢狀的 XML 結構描述項目之間。  
  
### <a name="related-sections"></a>相關章節  
 [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 描述關聯式結構描述的**資料集**從 XML 結構描述定義語言 (XSD) 結構描述中建立的。  
  
 [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 說明用來建立唯一外部索引鍵條件約束中的 XML 結構描述項目**資料集**。  
  
## <a name="see-also"></a>請參閱  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
