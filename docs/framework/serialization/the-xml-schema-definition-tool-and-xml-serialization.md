---
title: "XML 結構描述定義工具和 XML 序列化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Xsd.exe"
  - "XML 序列化，XML 結構描述定義工具"
  - "XML 結構描述定義工具"
  - "序列化，XML 結構描述定義工具"
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# XML 結構描述定義工具和 XML 序列化
XML 結構描述定義工具 \([XML 結構描述定義工具 \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md)\) 會隨 .NET Framework 工具當做 Windows® 軟體開發套件 \(SDK\) 的一部分安裝。 該工具的設計主要有兩個目的：  
  
-   產生符合特定 XML 結構描述定義語言 \(XSD\) 結構描述的 C\# 或 Visual Basic 類別檔。 此工具以 XML 結構描述做為引數並輸出包含各種類別的檔案，在以 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) 序列化時，符合結構描述。 如需如何使用此工具以產生符合特定結構描述之類別的相關資訊，請參閱[HOW TO：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/framework/serialization/xml-schema-def-tool-gen.md)。  
  
-   從 .dll 檔或 .exe 檔產生 XML 結構描述文件。 若要檢視您所建立或已修改其中屬性之檔案集的結構描述，請將 DLL 或 EXE 當成引數傳遞至工具以產生 XML 結構描述。 如需如何使用工具從類別集產生 XML 結構描述文件的相關資訊，請參閱[HOW TO：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/framework/serialization/xml-schema-def-tool-gen.md)。  
  
 如需這項工具和其他工具的詳細資訊，請參閱 [Tools](../../../docs/framework/tools/index.md)。 如需工具選項的相關資訊，請參閱 [XML 結構描述定義工具 \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md)。  
  
## 請參閱  
 [XML 序列化簡介](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [DataSet](frlrfSystemDataDataSetClassTopic)   
 [XML 結構描述定義工具 \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [HOW TO：序列化物件](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [HOW TO：還原序列化物件](../../../docs/framework/serialization/how-to-deserialize-an-object.md)   
 [HOW TO：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/framework/serialization/xml-schema-def-tool-gen.md)   
 [.NET Framework 中的 XML 結構描述繫結支援](http://msdn.microsoft.com/zh-tw/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)