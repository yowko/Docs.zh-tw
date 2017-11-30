---
title: "XML 和 SOAP 序列化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 809f1418d7ee0939c7e31124fbda7ef5fd8e2e5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="xml-and-soap-serialization"></a>XML 和 SOAP 序列化
XML 序列化會將物件的公用 (Public) 欄位和屬性，或是方法的參數和傳回值，轉換 (序列化) 為與特定 XML 結構描述 (Schema) 定義語言 (XSD) 文件相符的 XML 資料流。 XML 序列化會產生強型別 (Strongly Typed) 類別，其中包含的公用屬性和欄位都轉換為序列格式 (此例為 XML) 以進行儲存或傳輸。  
  
 因為 XML 為開放標準，無論是何種平台，XML 資料流都可依需要由任何應用程式處理。 例如，使用 ASP.NET 建立的 XML Web 服務以 <xref:System.Xml.Serialization.XmlSerializer> 類別建立 XML 資料流，在網際網路或內部網路的 XML Web 服務應用程式之間傳遞資料。 相反地，還原序列化採用這樣的 XML 資料流並重建物件。  
  
 XML 序列化也可用來將物件序列化為與 SOAP 規格相符的 XML 資料流。 SOAP 是以 XML 為基礎的通訊協定，特別設計來傳輸使用 XML 的程序呼叫。  
  
 若要序列化或還原序列化物件，請使用 <xref:System.Xml.Serialization.XmlSerializer> 類別。 若要建立要序列化的類別，請使用 XML 結構描述定義工具。  
  
## <a name="in-this-section"></a>本章節內容  
 [XML 序列化簡介](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 提供序列化的一般定義，特別是 XML 序列化。  
  
 [如何：序列化物件](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 提供序列化物件的逐步指示。  
  
 [如何：還原序列化物件](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 提供還原序列化物件的逐步指示。  
  
 [XML 序列化範例](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 提供範例示範 XML 序列化的基本概念。  
  
 [XML 結構描述定義工具和 XML 序列化](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 說明如何使用 XML 結構描述定義工具，建立遵循特定 XML 結構描述定義語言 (XSD) 結構描述的類別，或是從 .dll 檔案產生 XML 結構描述。  
  
 [使用屬性控制 XML 序列化](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 說明如何使用屬性控制序列化。  
  
 [可控制 XML 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 列出用來控制 XML 序列化的屬性。  
  
 [如何：指定 XML 資料流的替代元素名稱](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 提供進階案例展示如何藉由覆寫序列化產生多個 XML 資料流。  
  
 [如何：控制衍生類別的序列化](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 提供如何控制衍生類別序列化的範例。  
  
 [如何：限定 XML 元素和 XML 屬性名稱](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 說明如何定義並控制 XML 命名空間在 XML 資料流中使用的方式。  
  
 [以 XML Web 服務進行 XML 序列化](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 說明 XML 序列化如何用於 XML Web 服務當中。  
  
 [如何：將物件序列化為 SOAP 編碼的 XML 資料流](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 說明如何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別建立編碼 SOAP XML 資料流，這些資料流符合全球資訊網協會 (www.w3.org) 文件＜Simple Object Access Protocol (SOAP) 1.1＞的第 5 節。  
  
 [如何：覆寫已編碼的 SOAP XML 序列化](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 說明將物件的 XML 序列化覆寫為 SOAP 訊息的程序。  
  
 [可控制編碼 SOAP 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 列出用來控制 SOAP 編碼序列化的屬性。  
  
 [\<system.xml.serialization> 項目](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 用來控制 XML 序列化的最上層組態項目。  
  
 [\<dateTimeSerialization> 元素](../../../docs/standard/serialization/datetimeserialization-element.md)  
 控制 <xref:System.DateTime> 物件的序列化模式。  
  
 [\<schemaImporterExtensions>元素](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 類別使用的類型。  
  
 [\<xmlSchemaImporterExtensions> 的 \<add> 元素](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 類別使用的類型。  
  
## <a name="related-sections"></a>相關章節  
 [進階開發技術](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 提供與 .NET Framework 中精密的開發工作和技巧有關的詳細資訊之連結。  
  
 [使用 ASP.NET 和 XML Web Service 用戶端建立的 XML Web Service](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 提供一個主題，說明並解釋如何設計使用 ASP.NET 的 XML Web 服務。  
  
## <a name="see-also"></a>另請參閱  
 [二進位序列化](../../../docs/standard/serialization/binary-serialization.md)
