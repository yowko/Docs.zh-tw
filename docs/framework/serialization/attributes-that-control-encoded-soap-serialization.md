---
title: "控制編碼 SOAP 序列化的屬性 | Microsoft Docs"
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
  - "屬性 [.NET Framework], XML 序列化"
  - "序列化, 屬性"
  - "SOAP, XML 序列化"
  - "XML 序列化, 屬性"
  - "XML 序列化, SOAP"
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 控制編碼 SOAP 序列化的屬性
全球資訊網協會 \(www.w3.org\) 文件＜Simple Object Access Protocol \(SOAP\) 1.1＞，其中包含描述 SOAP 參數如何編碼的選擇性章節 \(第 5 節\)。若要遵循第 5 節的規格，您必須使用在 [System.Xml.Serialization](frlrfSystemXmlSerialization) 命名空間裡的特殊屬性組。套用適合類別與類別成員的那些屬性，然後使用 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) 序列化類別的執行個體。  
  
 下表顯示屬性、其可套用位置及作用。如需使用這些屬性控制 XML 序列化的詳細資訊，請參閱 [HOW TO：將物件序列化為 SOAP 編碼的 XML 資料流](../../../docs/framework/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)和 [HOW TO：覆寫已編碼的 SOAP XML 序列化](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)。  
  
 如需屬性的詳細資訊，請參閱[屬性](../../../docs/standard/attributes/index.md)。  
  
|屬性|適用於|指定|  
|--------|---------|--------|  
|[SoapAttributeAttribute](frlrfSystemXmlSerializationSoapAttributeAttributeClassTopic)|公用欄位、屬性、參數或傳回值。|類別成員將會序列化成 XML 屬性。|  
|[SoapElementAttribute](frlrfSystemXmlSerializationSoapElementAttributeClassTopic)|公用欄位、屬性、參數或傳回值。|類別將會序列化成 XML 項目。|  
|[SoapEnumAttribute](frlrfSystemXmlSerializationSoapEnumAttributeClassTopic)|為列舉識別項的公用欄位。|列舉成員的項目名稱。|  
|[SoapIgnoreAttribute](frlrfSystemXmlSerializationSoapIgnoreAttributeClassTopic)|公用屬性與欄位。|所屬類別序列化時，略過屬性或欄位。|  
|[SoapIncludeAttribute](frlrfSystemXmlSerializationSoapIncludeAttributeClassTopic)|公用衍生類別宣告以及 Web 服務描述語言 \(WSDL\) 文件的公用方法。|當產生結構描述時應包含型別 \(在序列化時辨認\)。|  
|[SoapTypeAttribute](frlrfSystemXmlSerializationSoapTypeAttributeClassTopic)|公用類別宣告|類別應序列化成 XML 型別。|  
  
## 請參閱  
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [HOW TO：將物件序列化為 SOAP 編碼的 XML 資料流](../../../docs/framework/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)   
 [HOW TO：覆寫已編碼的 SOAP XML 序列化](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)   
 [屬性](../../../docs/standard/attributes/index.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [HOW TO：序列化物件](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [HOW TO：還原序列化物件](../../../docs/framework/serialization/how-to-deserialize-an-object.md)