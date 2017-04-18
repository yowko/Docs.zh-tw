---
title: "編輯 XML 結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# 編輯 XML 結構描述
編輯 XML 結構描述是結構描述物件模型 \(SOM\) 的其中一項最重要功能。  SOM 的所有前結構描述編譯屬性都可用於變更 XML 結構描述中的現有值。  然後可重新編譯該 XML 結構描述以反映這些變更。  
  
 編輯載入 SOM 中之結構描述的第一步是往返結構描述。  在嘗試編輯結構描述之前，您應該熟悉如何使用 SOM API 往返結構描述。  您也應該熟悉後結構描述編譯資訊集 \(PSCI\) 的前結構描述編譯屬性及後結構描述編譯屬性。  
  
## 編輯 XML 結構描述  
 在此區段中會提供兩個程式碼範例，它們都會編輯在 [建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md) 主題中建立的客戶結構描述。  第一個程式碼範例會將新 `PhoneNumber` 項目加入至 `Customer` 項目，第二個程式碼範例會將新 `Title` 屬性加入至 `FirstName` 項目。  第一個範例還會使用後結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=fullName> 集合，做為當第二個程式碼範例使用前結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=fullName> 集合時周遊客戶結構描述的方式。  
  
### PhoneNumber 項目範例  
 此第一個程式碼範例將新 `PhoneNumber` 項目加入至客戶結構描述的 `Customer` 項目。  該程式碼範例會使用下列步驟編輯客戶結構描述。  
  
1.  將客戶結構描述加入至新 <xref:System.Xml.Schema.XmlSchemaSet> 物件，然後編譯它。  讀取或編譯結構描述時遇到的任何結構描述驗證警告及錯誤，都會由 <xref:System.Xml.Schema.ValidationEventHandler> 委派處理。  
  
2.  藉由重複處理 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性，從 <xref:System.Xml.Schema.XmlSchemaSet> 擷取已編譯的 <xref:System.Xml.Schema.XmlSchema> 物件。  因為已編譯結構描述，因此可存取後結構描述編譯資訊集 \(PSCI\) 屬性。  
  
3.  使用 <xref:System.Xml.Schema.XmlSchemaElement> 類別建立 `PhoneNumber` 項目，使用 <xref:System.Xml.Schema.XmlSchemaSimpleType> 及 <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> 類別建立 `xs:string` 簡單型別限制，將模式 Facet 加入至該限制的 <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> 屬性，並將該限制加入至簡單型別的 <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> 屬性，再將該簡單型別加入至 `PhoneNumber` 項目的 <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A>。  
  
4.  在後結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=fullName> 集合的 <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> 集合中，重複處理每個 <xref:System.Xml.Schema.XmlSchemaElement>。  
  
5.  如果項目的 <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> 是 `"Customer"`，則使用 <xref:System.Xml.Schema.XmlSchemaComplexType> 類別取得 `Customer` 項目的複雜型別，並使用 <xref:System.Xml.Schema.XmlSchemaSequence> 類別取得該複雜型別的順序物件。  
  
6.  使用包含現有 `FirstName` 及 `LastName` 項目之序列的前結構描述編譯 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> 集合，將新 `PhoneNumber` 項目加入該序列。  
  
7.  最後，使用 <xref:System.Xml.Schema.XmlSchemaSet> 類別的 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法，重新處理及編譯修改的 <xref:System.Xml.Schema.XmlSchema> 物件，並將它寫入主控台。  
  
 下列是完整的程式碼範例。  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 下列是在 [建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md) 主題中建立之已修改的客戶結構描述。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
        <xs:element name="PhoneNumber">  
          <xs:simpleType>  
            <xs:restriction base="xs:string">  
              <xs:pattern value="\d{3}-\d{3}-\d(4)" />  
            </xs:restriction>  
          </xs:simpleType>  
        </xs:element>  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
### 標題屬性範例  
 此第二個程式碼範例將新 `Title` 屬性加入至客戶結構描述的 `FirstName` 項目。  在第一個程式碼範例中，`FirstName` 項目的型別是 `xs:string`。  若要讓 `FirstName` 項目具有屬性及字串內容，必須將其型別變為具有簡單內容延伸程式內容模型的複雜型別。  
  
 該程式碼範例會使用下列步驟編輯客戶結構描述。  
  
1.  將客戶結構描述加入至新 <xref:System.Xml.Schema.XmlSchemaSet> 物件，然後編譯它。  讀取或編譯結構描述時遇到的任何結構描述驗證警告及錯誤，都會由 <xref:System.Xml.Schema.ValidationEventHandler> 委派處理。  
  
2.  藉由重複處理 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性，從 <xref:System.Xml.Schema.XmlSchemaSet> 擷取已編譯的 <xref:System.Xml.Schema.XmlSchema> 物件。  因為已編譯結構描述，因此可存取後結構描述編譯資訊集 \(PSCI\) 屬性。  
  
3.  使用 <xref:System.Xml.Schema.XmlSchemaComplexType> 類別，建立 `FirstName` 項目的新複雜型別。  
  
4.  使用 <xref:System.Xml.Schema.XmlSchemaSimpleContent> 及 <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> 類別，建立基底型別為 `xs:string` 的新簡單內容延伸程式。  
  
5.  使用 <xref:System.Xml.Schema.XmlSchemaAttribute> 類別，建立 <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> 為 `xs:string` 的新 `Title` 屬性，並將該屬性加入至簡單內容延伸程式。  
  
6.  將簡單內容的內容模型設為簡單內容延伸程式，並將複雜型別的內容模型設為簡單內容。  
  
7.  將新的複雜型別加入至前結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=fullName> 集合。  
  
8.  重複處理前結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=fullName> 集合中的每個 <xref:System.Xml.Schema.XmlSchemaObject>。  
  
> [!NOTE]
>  因為 `FirstName` 項目不是結構描述中的全域項目，所以它不可用在 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=fullName> 或 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=fullName> 集合中。  程式碼範例會藉由先尋找 `Customer` 項目，以尋找 `FirstName` 項目。  
>   
>  第一個程式碼範例會使用後結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=fullName> 集合，以往返結構描述。  在此範例中，前結構描述編譯 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=fullName> 集合用於往返結構描述。  當兩個集合都提供對結構描述中全域項目的存取權時，重複處理 <xref:System.Xml.Schema.XmlSchema.Items%2A> 集合會浪費更多時間，因為您必須重複處理結構描述中的所有全域項目，且其不具有任何 PSCI 屬性。  PSCI 集合 \(<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=fullName>、<xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=fullName>、<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=fullName> 等\) 可提供其全域項目、屬性、型別及其 PSCI 屬性的直接存取權。  
  
1.  如果 <xref:System.Xml.Schema.XmlSchemaObject> 項目的 <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> 為 `"Customer"`，則使用 <xref:System.Xml.Schema.XmlSchemaComplexType> 類別取得 `Customer` 項目的複雜型別，並使用 <xref:System.Xml.Schema.XmlSchemaSequence> 類別取得該複雜型別的順序物件。  
  
2.  重複處理前結構描述編譯 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=fullName> 集合中的每個 <xref:System.Xml.Schema.XmlSchemaParticle>。  
  
3.  如果 <xref:System.Xml.Schema.XmlSchemaParticle> 項目的 <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> 為 `"FirstName"`，則將 `FirstName` 項目的 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 設為新的 `FirstName` 複雜型別。  
  
4.  最後，使用 <xref:System.Xml.Schema.XmlSchemaSet> 類別的 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法，重新處理及編譯修改的 <xref:System.Xml.Schema.XmlSchema> 物件，並將它寫入主控台。  
  
 下列是完整的程式碼範例。  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 下列是在 [建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md) 主題中建立之已修改的客戶結構描述。  
  
```  
<?xml version="1.0" encoding=" utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:complexType name="FirstNameComplexType">  
    <xs:simpleContent>  
      <xs:extension base="xs:string">  
        <xs:attribute name="Title" type="xs:string" />  
      </xs:extension>  
    </xs:simpleContent>  
  </xs:complexType>  
</xs:schema>  
```  
  
## 請參閱  
 [XML 結構描述物件模型概觀](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)   
 [讀取及寫入 XML 結構描述](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)   
 [建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)   
 [周遊 XML 結構描述](../../../../docs/standard/data/xml/traversing-xml-schemas.md)   
 [併入或匯入 XML 結構描述](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)   
 [用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)   
 [後結構描述編譯資訊集](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)