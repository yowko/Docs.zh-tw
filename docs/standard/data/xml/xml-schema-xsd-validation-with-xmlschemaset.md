---
title: "使用 XmlSchemaSet 驗證 XML 結構描述 (XSD) | Microsoft Docs"
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
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 使用 XmlSchemaSet 驗證 XML 結構描述 (XSD)
可以根據 <xref:System.Xml.Schema.XmlSchemaSet> 中的 XML 結構描述定義語言 \(XSD\) 結構描述來驗證 XML 文件。  
  
## 驗證 XML 文件  
 XML 文件是透過 <xref:System.Xml.XmlReader> 類別的 <xref:System.Xml.XmlReader.Create%2A> 方法來驗證的。  若要驗證 XML 文件，請建構 <xref:System.Xml.XmlReaderSettings> 物件，該物件包含可用於驗證 XML 文件的 XML 結構描述定義語言 \(XSD\) 結構描述。  
  
> [!NOTE]
>  <xref:System.Xml.Schema> 命名空間包含的擴充方法可在使用 [LINQ to XML](../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md) 時，輕鬆地針對 XML 檔案驗證 XML 樹狀結構。  如需使用 LINQ to XML 驗證 XML 文件的詳細資訊，請參閱[HOW TO：使用 XSD 進行驗證](../Topic/How%20to:%20Validate%20Using%20XSD%20\(LINQ%20to%20XML\).md)。  
  
 可以將個別結構描述或一組結構描述 \(當做 <xref:System.Xml.Schema.XmlSchemaSet>\) 加入至 <xref:System.Xml.Schema.XmlSchemaSet>，其方式是將其中一個當做參數傳遞給 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法。  請注意在驗證文件時，此文件的目標命名空間必須符合結構描述集內結構描述的目標命名空間。  
  
 下列是範例 XML 文件。  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 下列是驗證範例 XML 文件的結構描述。  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 在下面的程式碼範例中，會將以上結構描述加入至 <xref:System.Xml.XmlReaderSettings> 物件的 <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> 屬性。  將 <xref:System.Xml.XmlReaderSettings> 物件當做參數，傳遞至驗證以上 XML 文件之 <xref:System.Xml.XmlReader> 物件的 <xref:System.Xml.XmlReader.Create%2A> 方法。  
  
 <xref:System.Xml.XmlReaderSettings> 物件的 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> 屬性會設為 `Schema`，以透過 <xref:System.Xml.XmlReader> 物件的 <xref:System.Xml.XmlReader.Create%2A> 方法，來強制驗證 XML 文件。  將 <xref:System.Xml.Schema.ValidationEventHandler> 加入至 <xref:System.Xml.XmlReaderSettings> 物件，以處理在驗證 XML 文件及結構描述期間找到的錯誤所引發的任意 <xref:System.Xml.Schema.XmlSeverityType> 或 <xref:System.Xml.Schema.XmlSeverityType> 事件。  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## 請參閱  
 [用於結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)   
 [使用 XML 結構描述](../../../../docs/standard/data/xml/working-with-xml-schemas.md)