---
title: 從 XML 結構描述 (XSD) 衍生資料集關聯式結構
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 878e39af575328fb0abba096c327d36203a52231
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164801"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>從 XML 結構描述 (XSD) 衍生資料集關聯式結構

這個章節提供如何從 XML 結構描述定義語言 (XSD) 結構描述文件來建置 `DataSet` 關聯式結構描述的概觀。 一般情況下，會針對架構專案的每個 `complexType` 子項目，在中產生資料表 `DataSet` 。 資料表結構由複雜型別的定義來決定。 資料表會建立在架構中的 `DataSet` 最上層元素。 不過，當元素是在另一個專案中嵌套時，只會為最上層元素建立資料表 `complexType` `complexType` ，在此情況下，會將嵌套專案 `complexType` `complexType` 對應到 `DataTable` 內的 `DataSet` 。  
  
 如需有關 XSD 的詳細資訊，請參閱全球資訊網協會 (W3C) [XML Schema part 0：入門建議](https://www.w3.org/TR/xmlschema-0/)、 [xml 架構第1部分：結構建議](https://www.w3.org/TR/xmlschema-1/)和 [xml 架構第2部分：資料類型建議](https://www.w3.org/TR/xmlschema-2/)。  
  
 下列範例示範 XML 架構，其中是專案的 `customers` 子專案，也 `MyDataSet` 就是 **資料集** 元素。  
  
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
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 資料表內每個資料行的資料型別都衍生自對應項目的 XML 結構描述型別或指定屬性。  
  
> [!NOTE]
> 如果元素 `customers` 是簡單 XML 架構資料類型（例如 **整數**），則不會產生任何資料表。 因為資料表僅會針對複雜型別的最上層項目產生。  
  
 在下列 XML 架構中， **Schema** 元素有兩個專案子系 `InStateCustomers` 和 `OutOfStateCustomers` 。  
  
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
  
 `InStateCustomers` 和 `OutOfStateCustomers` 子項目均為複雜型別項目 (`customerType`)。 因此，對應進程會在中產生下列兩個相同的資料表 `DataSet` 。  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>本節內容  

 [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用來在中建立 unique 和 foreign key 條件約束的 XML 架構元素 `DataSet` 。  
  
 [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)  
 描述用來在中建立資料表資料行之間關聯性的 XML 架構元素 `DataSet` 。  
  
 [XML 結構描述條件約束和關聯性](xml-schema-constraints-and-relationships.md)  
 描述在中使用 XML 架構元素建立條件約束時，如何以隱含方式建立關聯性 `DataSet` 。  
  
## <a name="related-sections"></a>相關章節  

 [在資料集中使用 XML](using-xml-in-a-dataset.md)  
 描述如何將關聯式結構和資料載入並保存 `DataSet` 為 XML 資料。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
