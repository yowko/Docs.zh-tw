---
title: 將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: d6fcdae77c2f2ac07ea5cd16baf07cd5de36d25b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203472"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束
在架構中, 您可以使用**key**元素, 在專案或屬性上指定索引鍵條件約束。 具有指定索引鍵條件約束的項目或屬性，在任何結構描述執行個體中都必須具有唯一的值，且不可具有 Null 值。  
  
 索引鍵條件約束類似唯一的條件約束，唯一的不同處定義索引鍵條件約束的資料行不能有 Null 值。  
  
 下表列出您可以在**key**元素中指定的**msdata**屬性。  
  
|屬性名稱|說明|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|如果指定這個屬性，則它的值會被當成條件約束名稱使用。 否則, **name**屬性會提供條件約束名稱的值。|  
|**msdata:PrimaryKey**|如果`PrimaryKey="true"`存在, 則**IsPrimaryKey**條件約束屬性會設定為**true**, 因此使其成為主要索引鍵。 **AllowDBNull**資料行屬性設定為**false**, 因為主鍵不能有 null 值。|  
  
 在轉換已指定索引鍵條件約束的架構中, 對應進程會在資料表上建立 unique 條件約束, 並針對條件約束中的每個資料行, 將**AllowDBNull**資料行屬性設定為**false** 。 Unique 條件約束的**IsPrimaryKey**屬性也會設定為**false** , 除非您已在`msdata:PrimaryKey="true"` **key**元素上指定。 它與結構描述 (其中 `PrimaryKey="true"`) 中唯一的條件約束相同。  
  
 在下列架構範例中, **key**元素會指定**CustomerID**元素的索引鍵條件約束。  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>   
```  
  
 **Key**元素指定**Customers**元素的**CustomerID**子項目值必須有唯一的值, 而且不能有 null 值。 轉譯 XML 結構描述定義語言 (XSD) 結構描述的過程中，對應處理序會建立下表：  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 XML 架構對應也會在**CustomerID**資料行上建立<xref:System.Data.DataSet> **UniqueConstraint** , 如下所示。 (為了便於了解，此處僅顯示相關屬性)。  
  
```  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID   
      IsPrimaryKey: True  
```  
  
 在產生的**資料集**內, **UniqueConstraint**的**IsPrimaryKey**屬性會設定為**true** , 因為架構會在`msdata:PrimaryKey="true"` **key**元素中指定。  
  
 **DataSet**中**UniqueConstraint**的**ConstraintName**屬性值是在架構的**Key**元素中指定的**msdata: ConstraintName**屬性的值。  
  
## <a name="see-also"></a>另請參閱

- [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
