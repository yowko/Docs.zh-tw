---
title: 從 XML 結構描述 (XSD) 產生資料集關聯
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: fd32d024acca393dcc8241f047a305e763682866
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204853"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>從 XML 結構描述 (XSD) 產生資料集關聯
您可以在 <xref:System.Data.DataSet> 內建立父子關係，以建立兩個或多個資料行之間的關聯。 有三種方式可以表示 XML 架構定義語言 (XSD) 架構中的**資料集**關聯性:  
  
- 指定巢狀複雜類型。  
  
- 使用**msdata: Relationship**注釋。  
  
- 指定不含**msdata: ConstraintOnly**注釋的**xs: keyref** 。  
  
## <a name="nested-complex-types"></a>巢狀複雜類型  
 結構描述中的巢狀複雜類型定義表示項目的父子關係。 下列 XML 架構片段顯示**OrderDetail**是**Order**元素的子項目。  
  
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
  
 XML 架構對應進程會在**DataSet**中建立對應至架構中之嵌套複雜類型的資料表。 它也會建立額外的資料行, 做 **-** 為所產生資料表的父子資料行使用。 請注意, 這些 **-** 父子式資料行指定了關聯性, 這與指定 primary key/foreign key 條件約束不同。  
  
## <a name="msdatarelationship-annotation"></a>msdata:Relationship 註釋  
 **Msdata: Relationship**注釋可讓您明確指定架構中未嵌套之元素之間的父子關聯性。 下列範例顯示**Relationship**元素的結構。  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 **Msdata: Relationship**注釋的屬性會識別與父子式關聯性相關的元素, 以及與關聯性相關的**parentkey**和**childkey**元素和屬性。 對應程式會使用這項資訊來產生**資料集中**的資料表, 並建立這些資料表之間的主鍵/外鍵關聯性。  
  
 例如, 下列架構片段會指定位於相同層級的**Order**和**OrderDetail**專案 (非 nested)。 架構會指定**msdata: Relationship**注釋, 以指定這兩個專案之間的父子式關聯性。 在此情況下, 必須使用**msdata: relationship**注釋來指定明確的關聯性。  
  
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
  
 對應程式會使用**Relationship**元素, 在**Order**資料表中的**OrderNumber**資料行和**資料集中** **OrderDetail**資料表的**OrderNo**資料行之間建立父子式關聯性。 對應處理只會指定關係，而不會像關聯式資料庫的主索引鍵/外部索引鍵條件約束一樣，自動為這些資料行的值指定任何條件約束。  
  
### <a name="in-this-section"></a>本節內容  
 [在巢狀結構描述項目之間進行隱含關聯對應](map-implicit-relations-between-nested-schema-elements.md)  
 描述當 XML 架構中遇到嵌套元素時, 在**DataSet**中隱含建立的條件約束和關聯性。  
  
 [針對巢狀項目指定的關聯進行對應](map-relations-specified-for-nested-elements.md)  
 描述如何在 XML 架構中, 針對嵌套元素的**資料集**明確設定關聯性。  
  
 [指定未巢狀放置之項目間的關聯](specify-relations-between-elements-with-no-nesting.md)  
 描述如何在**資料集**內, 建立未嵌套之 XML 架構元素之間的關聯性。  
  
### <a name="related-sections"></a>相關章節  
 [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 描述從 XML 架構定義語言 (XSD) 架構所建立之**資料集**的關聯式結構 (或架構)。  
  
 [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用來在**資料集中**建立 unique 和 foreign key 條件約束的 XML 架構專案。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
