---
title: 從 XML 結構描述 (XSD) 產生資料集關聯
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151126"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>從 XML 結構描述 (XSD) 產生資料集關聯
您可以在 <xref:System.Data.DataSet> 內建立父子關係，以建立兩個或多個資料行之間的關聯。 在 XML 架構定義語言 （XSD） 架構中，有三種方法可以表示**DataSet**關係：  
  
- 指定巢狀複雜類型。  
  
- 使用**msdata：關係**注釋。  
  
- 指定一個沒有 msdata**的 xs：keyref：****僅約束**注釋。  
  
## <a name="nested-complex-types"></a>巢狀複雜類型  
 結構描述中的巢狀複雜類型定義表示項目的父子關係。 以下 XML 架構片段顯示**OrderDetail**是**Order**元素的子項目。  
  
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
  
 XML 架構映射過程在**DataSet**中創建對應于架構中嵌套複雜類型的表。 它還創建其他列，這些列用作生成的表**-** 的父子列。 請注意，這些父**-** 子列指定關係，這與指定主鍵/外鍵約束不同。  
  
## <a name="msdatarelationship-annotation"></a>msdata:Relationship 註釋  
 **msdata：關係**注釋允許您顯式指定架構中未嵌套的元素之間的父子關係。 下面的示例顯示了**關係**元素的結構。  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 **msdata：關係**注釋的屬性標識父子關係中涉及的元素，以及關係中涉及的**父鍵**和**子鍵**元素和屬性。 映射過程使用此資訊在**DataSet**中生成表，並在這些表之間創建主鍵/外鍵關係。  
  
 例如，以下架構片段指定同一級別的 **"訂單"** 和"**訂單詳細資訊"** 元素（未嵌套）。 架構指定**msdata：關係**注釋，它指定這兩個元素之間的父子關係。 在這種情況下，必須使用**msdata：關係**注釋指定顯式關係。  
  
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
  
 映射過程使用 **"關係"** 元素在 **"訂單**"表中的**OrderNumber**列和**DataSet**中的 **"訂單詳細資訊**"表中的 **"訂單無"** 列之間創建父子關係。 對應處理只會指定關係，而不會像關聯式資料庫的主索引鍵/外部索引鍵條件約束一樣，自動為這些資料行的值指定任何條件約束。  
  
### <a name="in-this-section"></a>本節內容  
 [在巢狀結構描述項目之間進行隱含關聯對應](map-implicit-relations-between-nested-schema-elements.md)  
 描述在 XML 架構中遇到嵌套元素時在**DataSet**中隱式創建的約束和關係。  
  
 [針對巢狀項目指定的關聯進行對應](map-relations-specified-for-nested-elements.md)  
 描述如何在 XML 架構中為嵌套元素在**DataSet**中顯式設置關係。  
  
 [指定未巢狀放置之項目間的關聯](specify-relations-between-elements-with-no-nesting.md)  
 描述如何在未嵌套的 XML 架構元素之間的**DataSet**中創建關係。  
  
### <a name="related-sections"></a>相關章節  
 [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 描述從 XML 架構定義語言 （XSD） 架構創建的**DataSet**的關聯式結構或架構。  
  
 [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用於在**DataSet**中創建唯一和外鍵約束的 XML 架構元素。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
