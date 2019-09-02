---
title: 將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 231f23ccf47f60b902fdd5c66b63fe1a750445f9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203412"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束
在 XML 架構定義語言 (XSD) 架構中, **unique**專案會指定元素或屬性的唯一性條件約束。 在將 XML 結構描述轉譯到關聯式結構描述的處理序中，會將 XML 結構描述內項目或屬性上指定的唯一的條件約束 (Constraint)，對應到所產生的對應 <xref:System.Data.DataTable> 內 <xref:System.Data.DataSet> 的唯一的條件約束。  
  
 下表列出您可以在**unique**元素中指定的**msdata**屬性。  
  
|屬性名稱|描述|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|如果指定這個屬性，則它的值會被當成條件約束名稱使用。 否則, **name**屬性會提供條件約束名稱的值。|  
|**msdata:PrimaryKey**|如果`PrimaryKey="true"` **unique**元素中有, 則會建立 unique 條件約束, 並將**IsPrimaryKey**屬性設定為**true**。|  
  
 下列範例顯示使用**unique**專案指定唯一性條件約束的 XML 架構。  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 架構中的**unique**元素會針對檔實例中的所有**Customers**元素指定, **CustomerID**子項目的值必須是唯一的。 在建立**資料集**時, 對應進程會讀取此架構, 並產生下列資料表:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 對應進程也會在**CustomerID**資料行上建立 unique 條件約束, 如下列**資料集**所示。 (為了便於了解，此處僅顯示相關屬性)。  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 在產生的**資料集中**, unique 條件約束的**IsPrimaryKey**屬性會設定為**False** 。 資料行上的**unique**屬性工作表示**CustomerID**資料行值必須是唯一的 (但它們可以是 null 參考, 如資料行的**AllowDBNull**屬性所指定)。  
  
 如果您修改架構, 並將選擇性的**msdata: PrimaryKey**屬性值設定為**True**, 則會在資料表上建立 unique 條件約束。 **AllowDBNull**資料行屬性設定為**False**, 而條件約束的**IsPrimaryKey**屬性設定為**True**, 因此**CustomerID**資料行是主鍵資料行。  
  
 您可以在 XML 結構描述中，將唯一的條件約束指定給合併的項目或屬性。 下列範例示範如何在架構中加入另一個**xs: field**元素, 以指定在任何實例中, 所有**客戶**的**CustomerID**和**名稱**值的組合都必須是唯一的。  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 這是在產生的**資料集中**建立的條件約束。  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>另請參閱

- [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
