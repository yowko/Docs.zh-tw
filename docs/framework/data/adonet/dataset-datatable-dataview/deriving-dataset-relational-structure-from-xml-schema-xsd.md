---
title: 從 XML 結構描述 (XSD) 衍生資料集關聯式結構
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 549579fca0179994191987097c12b6085ee91756
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119687"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>從 XML 結構描述 (XSD) 衍生資料集關聯式結構
這個章節提供如何從 XML 結構描述定義語言 (XSD) 結構描述文件來建置 `DataSet` 關聯式結構描述的概觀。 一般情況下，每個`complexType`結構描述元素的子項目，在中，所產生的資料表`DataSet`。 資料表結構由複雜型別的定義來決定。 資料表會建立在`DataSet`結構描述中的最上層項目。 不過，如果資料表僅建立最上層`complexType`項目時`complexType`項目放到另一個巢狀`complexType`項目，在這種情況下巢狀`complexType`元素會對應到`DataTable`內`DataSet`。  
  
 如需有關 XSD 的詳細資訊，請參閱 World Wide Web Consortium (W3C) [XML 結構描述第 0:入門建議事項](https://www.w3.org/TR/xmlschema-0/)，則[XML 結構描述第 1 部分：結構建議事項](https://www.w3.org/TR/xmlschema-1/)，而[XML Schema Part 2:資料型別建議](https://www.w3.org/TR/xmlschema-2/)。  
  
 下列範例示範 XML 結構描述所在`customers`是子元素`MyDataSet`項目，也就是**資料集**項目。  
  
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
>  如果項目`customers`這類是簡單的 XML 結構描述資料型別的**整數**，不會產生資料表。 因為資料表僅會針對複雜型別的最上層項目產生。  
  
 下列 XML 結構描述**結構描述**項目有兩個項目子系`InStateCustomers`和`OutOfStateCustomers`。  
  
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
 描述用來建立唯一外部索引鍵條件約束中的 XML 結構描述項目`DataSet`。  
  
 [從 XML 結構描述 (XSD) 產生資料集關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 描述用來建立資料表中的資料行之間的關聯性的 XML 結構描述項目`DataSet`。  
  
 [XML 結構描述條件約束和關聯性](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 描述如何隱含建立關聯時建立條件約束中的使用 XML 結構描述項目`DataSet`。  
  
## <a name="related-sections"></a>相關章節  
 [在資料集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 描述如何載入及保存資料與關聯式結構`DataSet`為 XML 資料。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
