---
title: 從 XML 結構描述 (XSD) 衍生資料集關聯式結構
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151165"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>從 XML 結構描述 (XSD) 衍生資料集關聯式結構
這個章節提供如何從 XML 結構描述定義語言 (XSD) 結構描述文件來建置 `DataSet` 關聯式結構描述的概觀。 通常，對於架構元素`complexType`的每個子項目，在 中生成表`DataSet`。 資料表結構由複雜型別的定義來決定。 表在 架構中`DataSet`的頂級元素中創建。 但是，僅當`complexType``complexType``complexType`元素嵌套在另一個元素中時，才為頂級元素創建表，在這種情況下，嵌套`complexType`元素映射到 中的 。 `DataTable` `DataSet`  
  
 有關 XSD 的詳細資訊，請參閱萬維網聯盟 （W3C） [XML 架構第 0 部分：引物建議](https://www.w3.org/TR/xmlschema-0/)[、XML 架構第 1 部分：結構建議](https://www.w3.org/TR/xmlschema-1/)和[XML 架構第 2 部分：資料類型建議](https://www.w3.org/TR/xmlschema-2/)。  
  
 下面的示例演示了 XML 架構`customers`，其中元素的`MyDataSet`子項目是**DataSet**元素。  
  
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
> 如果元素`customers`是簡單的 XML 架構資料類型（如**整數**），則不生成任何表。 因為資料表僅會針對複雜型別的最上層項目產生。  
  
 在以下 XML 架構中，**架構**元素有兩個元素`InStateCustomers`子`OutOfStateCustomers`元素和 。  
  
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
  
 `InStateCustomers` 和 `OutOfStateCustomers` 子項目均為複雜型別項目 (`customerType`)。 因此，映射過程在 中生成以下兩個相同的表`DataSet`。  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>本節內容  
 [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用於在 中創建唯一`DataSet`和外鍵約束的 XML 架構元素。  
  
 [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)  
 描述用於在 中的表列之間創建關係的 XML 架構`DataSet`元素。  
  
 [XML 結構描述條件約束和關聯性](xml-schema-constraints-and-relationships.md)  
 描述在 中使用 XML 架構元素在 中創建約束時如何`DataSet`隱式創建關係。  
  
## <a name="related-sections"></a>相關章節  
 [在資料集中使用 XML](using-xml-in-a-dataset.md)  
 描述如何將關聯式結構和資料`DataSet`載入和持久化為 XML 資料。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
