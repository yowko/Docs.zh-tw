---
title: 建置 XML 結構描述
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10b2471d13d410826cec3404725117649442297b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46579884"
---
# <a name="building-xml-schemas"></a>建置 XML 結構描述
<xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的類別會對應至全球資訊網協會 (W3C) XML 結構描述建議事項中定義的結構，並可用於建置記憶體中的 XML 結構描述。  
  
## <a name="building-an-xml-schema"></a>建置 XML 結構描述  
 在下面的程式碼範例中，會使用 SOM API 建置記憶體中的客戶 XML 結構描述。  
  
### <a name="creating-element-and-attributes"></a>建立項目及屬性  
 程式碼範例會從下往上建置客戶結構描述，首先建立項目子系、屬性及其對應的型別，然後再建立最上層項目。  
  
 在下列程式碼範例中，會使用 SOM 的 `FirstName` 及 `LastName` 類別，建立 `CustomerId` 及 <xref:System.Xml.Schema.XmlSchemaElement> 項目，以及客戶結構描述的 <xref:System.Xml.Schema.XmlSchemaAttribute> 屬性。 除了 <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> 及 <xref:System.Xml.Schema.XmlSchemaElement> 類別的 <xref:System.Xml.Schema.XmlSchemaAttribute> 屬性 (其對應至 XML 結構描述中 `<xs:element />` 及 `<xs:attribute />` 項目的 name 屬性 (Attribute))，結構描述所允許的所有其他屬性 (`defaultValue`、`fixedValue` 及 `form` 等)，在 <xref:System.Xml.Schema.XmlSchemaElement> 及 <xref:System.Xml.Schema.XmlSchemaAttribute> 類別中都有對應的屬性 (Property)。  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>建立結構描述型別  
 項目及屬性的內容是由其型別來定義。 若要建立其型別為其中一個內建結構描述型別的項目及屬性 (Attribute)，請使用 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 類別，以內建型別之對應的限定名稱設定 <xref:System.Xml.Schema.XmlSchemaElement> 或 <xref:System.Xml.Schema.XmlSchemaAttribute> 類別的 <xref:System.Xml.XmlQualifiedName> 屬性 (Property)。 若要建立項目及屬性的使用者定義型別，請使用 <xref:System.Xml.Schema.XmlSchemaSimpleType> 或 <xref:System.Xml.Schema.XmlSchemaComplexType> 類別，建立新的簡單或複雜型別。  
  
> [!NOTE]
>  若要建立做為項目或屬性 (Attribute) 之匿名子系的未命名簡單或複雜型別 (僅簡單型別適用於屬性 (Attribute))，請將 <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> 或 <xref:System.Xml.Schema.XmlSchemaElement> 類別的 <xref:System.Xml.Schema.XmlSchemaAttribute> 屬性設為未命名的簡單或複雜型別，而不是 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 或 <xref:System.Xml.Schema.XmlSchemaElement> 類別的 <xref:System.Xml.Schema.XmlSchemaAttribute> 屬性 (Property)。  
  
 XML 結構描述允許匿名及具名簡單型別，利用限制其他簡單型別 (內建的或使用者定義的) 衍生，或建構為其他簡單型別的清單或聯集。 <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> 類別可用於藉由限制內建 `xs:string` 型別，來建立簡單型別。 您也可以使用 <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> 或 <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> 類別，建立清單或聯集型別。 <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> 屬性可表示它是簡單型別限制、清單還是聯集。  
  
 在下列程式碼範例中，`FirstName` 項目的型別為內建型別 `xs:string`，`LastName` 項目的型別為限制內建型別 `xs:string` 的具名簡單型別 (`MaxLength` Facet 值為 20)，而 `CustomerId` 屬性的型別為內建型別 `xs:positiveInteger`。 `Customer` 項目為匿名的複雜型別，其物件是 `FirstName` 及 `LastName` 項目的序列，而且其屬性包含 `CustomerId` 屬性。  
  
> [!NOTE]
>  您也可以將 <xref:System.Xml.Schema.XmlSchemaChoice> 或 <xref:System.Xml.Schema.XmlSchemaAll> 類別做為複雜型別的物件，以複寫 `<xs:choice />` 或 `<xs:all />` 語意。  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>建立及編譯結構描述  
 此時，已使用 SOM API 在記憶體中建立項目子系及屬性、其對應的型別，以及最上層 `Customer` 項目。 在下列程式碼範例中，會使用 <xref:System.Xml.Schema.XmlSchema> 類別建立結構描述項目，使用 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 屬性將最上層項目及型別加入其中，並使用 <xref:System.Xml.Schema.XmlSchemaSet> 類別編譯完整的結構描述，然後寫入主控台。  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> 方法會根據 XML 結構描述的規則，驗證客戶結構描述，並使 Post-Schema-Compilation 屬性可用。  
  
> [!NOTE]
>  SOM API 中的所有 Post-Schema-Compilation 屬性都與 Post-Schema-Validation-Infoset 不同。  
  
 加入 <xref:System.Xml.Schema.ValidationEventHandler> 的 <xref:System.Xml.Schema.XmlSchemaSet> 是一種委派屬性，它會呼叫回呼方法 `ValidationCallback`，以處理結構描述驗證警告及錯誤。  
  
 以下是完整的程式碼範例，以及寫入主控台的客戶結構描述。  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
            <xs:element name="LastName" type="tns:LastNameType" />  
         </xs:sequence>  
         <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="LastNameType">  
      <xs:restriction base="xs:string">  
         <xs:maxLength value="20" />  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>另請參閱

- [XML 結構描述物件模型概觀](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [讀取和寫入 XML 結構描述](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [周遊 XML 結構描述](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [編輯 XML 結構描述](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [併入或匯入 XML 結構描述](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
- [用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [後結構描述編譯資訊集](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
