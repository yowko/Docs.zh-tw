---
title: "HOW TO：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件 | Microsoft Docs"
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
  - "使用 XML 結構描述定義工具產生 XML 類別"
  - "使用 XML 結構描述定義工具產生 XML 結構描述文件"
  - "XML 結構描述定義工具, 用來產生符合特定結構描述的類別"
  - "XML 結構描述定義工具, 用來產生 XML 結構描述文件"
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# HOW TO：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件
XML 結構描述定義工具 \(Xsd.exe\) 讓您產生說明類別的 XML 結構描述或產生由 XML 結構描述定義的類別。下列程序將說明如何執行這些作業。  
  
### 產生符合特定結構描述的類別  
  
1.  開啟命令提示字元。  
  
2.  將 XML 結構描述當成引數傳遞至 XML 結構描述定義工具，以建立一組類別精確地符合 XML 結構描述，例如：  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     此工具只能處理參考 2001 年 3 月 16 日全球資訊網協會 XML 規格的結構描述。換句話說，XML 結構描述的命名空間必須為 "http:\/\/www.w3.org\/2001\/XMLSchema"，如下列範例所示。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  視需要，使用方法、屬性或欄位來變更類別。如需使用屬性修改類別的詳細資訊，請參閱[使用屬性控制 XML 序列化](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)和[控制編碼 SOAP 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)。  
  
 檢查在序列化一個類別 \(或多個類別\) 時產生的 XML 資料流結構描述，通常很有用。例如，您可發佈結構描述供其他人使用，或是將它與一個您想要達到符合性的結構描述比較。  
  
#### 從一組類別產生 XML 結構描述文件  
  
1.  將類別編譯為 DLL。  
  
2.  開啟命令提示字元。  
  
3.  將 DLL 當成引數傳遞給 Xsd.exe，例如：  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     將寫入結構描述，以 "schema0.xsd" 名稱開始。  
  
## 請參閱  
 [XML 結構描述定義工具和 XML 序列化](../../../docs/framework/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)   
 [XML 序列化簡介](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [DataSet](frlrfSystemDataDataSetClassTopic)   
 [XML 結構描述定義工具 \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [HOW TO：序列化物件](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [HOW TO：還原序列化物件](../../../docs/framework/serialization/how-to-deserialize-an-object.md)