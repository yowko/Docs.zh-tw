---
title: "推斷結構描述節點型別與結構的規則 | Microsoft Docs"
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
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# 推斷結構描述節點型別與結構的規則
本主題說明結構描述推斷程序如何將 XML 文件中所發現的節點型別轉譯為 XML 結構描述定義語言 \(XSD\) 結構。  
  
## 項目推斷規則  
 本節將說明項目宣告的推斷規則。  有八種項目宣告的結構會進行推斷：  
  
1.  簡單型別項目  
  
2.  空白項目  
  
3.  具有屬性的空白項目  
  
4.  具有屬性與簡單內容的項目  
  
5.  具有項目子系序列的項目  
  
6.  具有項目子系與屬性序列的項目  
  
7.  具有項目子系選擇序列的項目  
  
8.  具有項目子系與屬性選擇序列的項目  
  
> [!NOTE]
>  所有 `complexType` 宣告都會被推斷為匿名型別。  唯一會進行推斷的全域項目為根項目；其他項目都是區域項目。  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
### 簡單型別項目  
 下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。  粗體的項目表示針對簡單型別項目所推斷的結構描述。  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
|XML|結構描述|  
|---------|----------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root" type="xs:string" />`<br /><br /> `\</xs:schema>`|  
  
### 空元素  
 下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。  粗體的項目表示針對空白項目所推斷的結構描述。  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
|XML|結構描述|  
|---------|----------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="empty" />`<br /><br /> `\</xs:schema>`|  
  
### 具有屬性的空白項目  
 下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。  粗體的項目表示針對具有屬性的空白項目所推斷的結構描述。  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
|XML|結構描述|  
|---------|----------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="empty">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 具有屬性與簡單內容的項目  
 下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。  粗體的項目表示針對具有屬性與簡單內容的項目所推斷的結構描述。  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
|XML|結構描述|  
|---------|----------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:simpleContent>`<br /><br /> `\<xs:extension base="xs:string">`<br /><br /> `\<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `\</xs:extension>`<br /><br /> `\</xs:simpleContent>`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 具有項目子系序列的項目  
 下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。  粗體的項目表示針對具有項目子系序列的項目所推斷的結構描述。  
  
> [!NOTE]
>  即使某個項目只有一個項目子系，仍會被視為序列。  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
|XML|結構描述|  
|---------|----------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:sequence>`<br /><br /> `\<xs:element name="subElement" />`<br /><br /> `\</xs:sequence>`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 具有項目子系與屬性序列的項目  
 下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。  粗體的項目表示針對具有項目子系與屬性序列的項目所推斷的結構描述。  
  
> [!NOTE]
>  即使某個項目只有一個項目子系，仍會被視為序列。  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
|XML|結構描述|  
|---------|----------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:sequence>`<br /><br /> `\<xs:element name="subElement1" />`<br /><br /> `\<xs:element name="subElement2" />`<br /><br /> `\</xs:sequence>`<br /><br /> `\<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 具有項目子系選擇序列的項目  
 下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。  粗體的項目表示針對具有項目子系選擇序列的項目所推斷的結構描述。  
  
> [!NOTE]
>  在推斷的結構描述中，`xs:choice` 項目的 `maxOccurs` 屬性會設為 `"unbounded"`。  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
|XML|結構描述|  
|---------|----------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:sequence>`<br /><br /> `\<xs:choice maxOccurs="unbounded">`<br /><br /> `\<xs:element name="subElement1" />`<br /><br /> `\<xs:element name="subElement2" />`<br /><br /> `\</xs:choice>`<br /><br /> `\</xs:sequence>`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 具有項目子系與屬性之序列與選擇的項目  
 下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。  粗體的項目表示針對具有項目子系與屬性之序列與選擇的項目所推斷的結構描述。  
  
> [!NOTE]
>  在推斷的結構描述中，`xs:choice` 項目的 `maxOccurs` 屬性會設為 `"unbounded"`。  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
|XML|結構描述|  
|---------|----------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:sequence>`<br /><br /> `\<xs:choice maxOccurs="unbounded">`<br /><br /> `\<xs:element name="subElement1" />`<br /><br /> `\<xs:element name="subElement2" />`<br /><br /> `\</xs:choice>`<br /><br /> `\</xs:sequence>`<br /><br /> `\<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 屬性處理  
 每當在節點中發現新的屬性時，該屬性就會以 `use="required"` 加入節點的推斷定義中。  下次在執行個體中發現相同的節點時，推斷程序就會比較目前執行個體的屬性與已推斷的屬性。  若執行個體中缺少某些已推斷的屬性，`use="optional"` 就會加入屬性定義中。  新屬性會以 `use="optional"` 加入現有的宣告中。  
  
### 出現條件約束  
 在結構描述推斷程序中，會針對結構描述的推斷元件產生 `minOccurs` 和 `maxOccurs` 屬性，其值為 `"0"` 或 `"1"`，以及 `"1"` 或 `"unbounded"`。  `"1"` 和 `"unbounded"` 這兩個值，必須在 `"0"` 與 `"1"` 這兩個值無法驗證 XML 文件時，才會使用 \(例如，若 `MinOccurs="0"` 無法精確說明某個項目，才會使用 `minOccurs="1"`\)。  
  
### 混合內容  
 若項目中含有混合內容 \(例如文字與項目相互穿插\)，則會針對已推斷的複雜型別定義產生 `mixed="true"` 屬性。  
  
## 其他節點型別推斷規則  
 下表所說明的推斷規則，可用來處理指示、註解、實體參考、CDATA、文件型別與命名空間節點。  
  
|節點類型|轉譯|  
|----------|--------|  
|處理指示|忽略。|  
|註解|忽略。|  
|實體參考|<xref:System.Xml.Schema.XmlSchemaInference> 類別不處理實體參考。  若 XML 文件中含有實體參考，您必須使用可擴充實體的讀取器。  例如，您可以將 <xref:System.Xml.XmlTextReader> 傳遞為參數，並將其 <xref:System.Xml.XmlTextReader.EntityHandling%2A> 屬性設定為 <xref:System.Xml.EntityHandling>。  若發現實體參考，但讀取器並未擴充實體，則會擲回例外狀況。|  
|CDATA|XML 文件中的任何 `<![CDATA[   ]]` 區段都會被推斷為 `xs:string`。|  
|文件型別|忽略。|  
|命名空間|忽略。|  
  
 如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。  
  
## 請參閱  
 <xref:System.Xml.Schema.XmlSchemaInference>   
 [XML 結構描述物件模型 \(SOM\)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)   
 [推斷 XML 結構描述](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)   
 [從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)   
 [推斷簡單型別的規則](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)