---
title: "併入或匯入 XML 結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a8c9b513f47fcb07f987b1e17f0b7f485cef3143
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="including-or-importing-xml-schemas"></a>併入或匯入 XML 結構描述
XML 結構描述可包含 `<xs:import />`, `<xs:include />` 及 `<xs:redefine />` 項目。 這些結構描述項目會參考其他 XML 結構描述，其可用於補充併入或匯入它們之結構描述的結構。 <xref:System.Xml.Schema.XmlSchemaImport>、<xref:System.Xml.Schema.XmlSchemaInclude> 及 <xref:System.Xml.Schema.XmlSchemaRedefine> 類別會對應至結構描述物件模型 (SOM) API 中的這些項目。  
  
## <a name="including-or-importing-an-xml-schema"></a>併入或匯入 XML 結構描述  
 下列程式碼範例會為[建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)主題中建立的客戶結構描述補充位址結構描述。 為客戶結構描述補充位址結構描述，可讓位址型別在客戶結構描述中使用。  
  
 您可使用 `<xs:include />` 或 `<xs:import />` 項目加入位址結構描述，以按原樣使用位址結構描述的元件，或使用 `<xs:redefine />` 項目，修改其中任何元件以滿足客戶結構描述需要。 因為位址結構描述與客戶結構描述的 `targetNamespace` 不同，所以會使用 `<xs:import />` 項目及匯入語意。  
  
 程式碼範例使用下列步驟併入位址結構描述。  
  
1.  將客戶結構描述及位址結構描述加入至新的 <xref:System.Xml.Schema.XmlSchemaSet> 物件，然後對它們進行編譯。 讀取或編譯結構描述時遇到的任何結構描述驗證警告及錯誤，都會由 <xref:System.Xml.Schema.ValidationEventHandler> 委派處理。  
  
2.  透過重複處理 <xref:System.Xml.Schema.XmlSchema> 屬性，從 <xref:System.Xml.Schema.XmlSchemaSet> 中為客戶及位址結構描述擷取已編譯的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 物件。 因為已編譯結構描述，因此可存取後結構描述編譯資訊集 (PSCI) 屬性。  
  
3.  建立 <xref:System.Xml.Schema.XmlSchemaImport> 物件、將 import 的 <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> 屬性設為位址結構描述的命名空間、將 import 的 <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> 屬性設為位址結構描述的 <xref:System.Xml.Schema.XmlSchema> 物件，並將 import 加入客戶結構描述的 <xref:System.Xml.Schema.XmlSchema.Includes%2A> 屬性中。  
  
4.  使用 <xref:System.Xml.Schema.XmlSchema> 類別的 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法，重新處理並編譯客戶結構描述之已修改的 <xref:System.Xml.Schema.XmlSchemaSet> 物件，並將其寫入主控台。  
  
5.  最後，使用客戶結構描述的 <xref:System.Xml.Schema.XmlSchema.Includes%2A> 屬性，將匯入至客戶結構描述的所有結構描述遞迴寫入主控台。 <xref:System.Xml.Schema.XmlSchema.Includes%2A> 屬性對所有加入至結構描述的 include、import 或 redefine 提供存取權。  
  
 下列是完整程式碼範例及寫入主控台的客戶與位址結構描述。  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
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
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 如需 `<xs:import />`、`<xs:include />` 及 `<xs:redefine />` 項目與 <xref:System.Xml.Schema.XmlSchemaImport>、<xref:System.Xml.Schema.XmlSchemaInclude> 和 <xref:System.Xml.Schema.XmlSchemaRedefine> 類別的詳細資訊，請參閱 [W3C XML 結構描述](http://www.w3.org/XML/Schema) (英文) 及 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間類別參考文件。  
  
## <a name="see-also"></a>請參閱  
 [XML 結構描述物件模型概觀](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [讀取和寫入 XML 結構描述](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [建置 XML 結構描述](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [周遊 XML 結構描述](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [編輯 XML 結構描述](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
