---
title: 從 XML 結構描述 (XSD) 衍生資料集關聯式結構
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d15aa02b41b9a34b00298aeb32d2e3998de8feba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786330"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>從 XML 結構描述 (XSD) 衍生資料集關聯式結構
這個章節提供如何從 XML 結構描述定義語言 (XSD) 結構描述文件來建置 `DataSet` 關聯式結構描述的概觀。 一般而言，針對架構專案`complexType`的每個子項目，會`DataSet`在中產生資料表。 資料表結構由複雜型別的定義來決定。 資料表會在架構中`DataSet`的最上層元素中建立。 不過，只有`complexType`當元素在另一個`complexType`專案中嵌套時`complexType` ，才會針對最上層元素建立資料表，在此`DataTable`情況下， `complexType` `DataSet`嵌套專案會對應至內的。  
  
 如需有關 XSD 的詳細資訊，請參閱全球資訊網協會（W3C [） XML 架構第0部分：入門建議](https://www.w3.org/TR/xmlschema-0/) [，XML 架構第一部：結構建議](https://www.w3.org/TR/xmlschema-1/) [和 XML 架構第二部分：Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) (XML 結構描述第 2 部分：資料類型建議)。  
  
 下列範例示範 XML 架構，其中`customers`是專案的子`MyDataSet`專案，也就是**DataSet**元素。  
  
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
> 如果元素`customers`是簡單的 XML 架構資料類型（例如**整數**），則不會產生任何資料表。 因為資料表僅會針對複雜型別的最上層項目產生。  
  
 在下列 XML 架構中，**架構**元素有兩個專案子系`InStateCustomers` ， `OutOfStateCustomers`和。  
  
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
  
 `InStateCustomers` 和 `OutOfStateCustomers` 子項目均為複雜型別項目 (`customerType`)。 因此，對應進程會在中`DataSet`產生下列兩個相同的資料表。  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>本節內容  
 [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用來在中`DataSet`建立唯一和外鍵條件約束的 XML 架構專案。  
  
 [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)  
 描述用來在的`DataSet`資料表資料行之間建立關聯的 XML 架構元素。  
  
 [XML 結構描述條件約束和關聯性](xml-schema-constraints-and-relationships.md)  
 描述在中`DataSet`使用 XML 架構專案來建立條件約束時，如何隱含建立關聯性。  
  
## <a name="related-sections"></a>相關章節  
 [在 DataSet 中使用 XML](using-xml-in-a-dataset.md)  
 描述如何在中`DataSet`將關聯式結構和資料載入和保存為 XML 資料。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../ado-net-overview.md)
