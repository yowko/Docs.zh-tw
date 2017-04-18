---
title: "控制 XML 序列化的屬性 | Microsoft Docs"
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
  - "類別, 序列化"
  - "序列化, 屬性"
  - "XML 結構描述, 序列化"
  - "XML 序列化, 屬性"
  - "XmlSerializer 類別, 序列化"
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 控制 XML 序列化的屬性
您可以將下表中的屬性套用到類別和類別成員，以便控制 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) 序列化或還原序列化類別之執行個體的方式。若要了解這些屬性如何控制 XML 序列化，請參閱[使用屬性控制 XML 序列化](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)。  
  
 這些屬性也可用來控制 XML Web Service 產生的常值樣式 SOAP 訊息。如需關於套用這些屬性至 XML Web Service 方法的詳細資訊，請參閱 [以 XML Web 服務進行 XML 序列化](../../../docs/framework/serialization/xml-serialization-with-xml-web-services.md)。  
  
 如需屬性的詳細資訊，請參閱[屬性](../../../docs/standard/attributes/index.md)。  
  
|屬性|適用於|指定|  
|--------|---------|--------|  
|[XmlAnyAttributeAttribute](frlrfSystemXmlSerializationXmlAnyAttributeAttributeClassTopic)|公用欄位、屬性、參數或傳回 [XmlAttribute](frlrfSystemXmlXmlAttributeClassTopic) 物件陣列的傳回值。|當還原序列化時，陣列將填入代表所有結構描述未知之 XML 屬性的 [XmlAttribute](frlrfSystemXmlXmlAttributeClassTopic) 物件。|  
|[XmlAnyElementAttribute](frlrfSystemXmlSerializationXmlAnyElementAttributeClassTopic)|公用欄位、屬性、參數或傳回 [XmlElement](frlrfSystemXmlXmlElementClassTopic) 物件陣列的傳回值。|當還原序列化時，陣列將填入代表所有結構描述未知之 XML 項目的 [XmlElement](frlrfSystemXmlXmlElementClassTopic) 物件。|  
|[XmlArrayAttribute](frlrfSystemXmlSerializationXmlArrayAttributeClassTopic)|公用欄位、屬性、參數或傳回複雜物件陣列的傳回值。|陣列的成員將產生為 XML 陣列的成員。|  
|[XmlArrayItemAttribute](frlrfSystemXmlSerializationXmlArrayItemAttributeClassTopic)|公用欄位、屬性、參數或傳回複雜物件陣列的傳回值。|可插入陣列的衍生型別。通常與 [XmlArrayAttribute](frlrfSystemXmlSerializationXmlArrayAttributeClassTopic) 一起套用。|  
|[XmlAttributeAttribute](frlrfSystemXmlSerializationXmlAttributeAttributeClassTopic)|公用欄位、屬性、參數或傳回值。|成員將會序列化成 XML 屬性。|  
|[XmlChoiceIdentifierAttribute](frlrfSystemXmlSerializationXmlChoiceIdentifierAttributeClassTopic)|公用欄位、屬性、參數或傳回值。|使用列舉型別可進一步明確識別成員。|  
|[XmlElementAttribute](frlrfSystemXmlSerializationXmlElementAttributeClassTopic)|公用欄位、屬性、參數或傳回值。|欄位或屬性將序列化成 XML 項目。|  
|[XmlEnumAttribute](frlrfSystemXmlSerializationXmlEnumAttributeClassTopic)|為列舉識別項的公用欄位。|列舉成員的項目名稱。|  
|[XmlIgnoreAttribute](frlrfSystemXmlSerializationXmlIgnoreAttributeClassTopic)|公用屬性與欄位。|所屬類別序列化時，略過屬性或欄位。|  
|[XmlIncludeAttribute](frlrfSystemXmlSerializationXmlIncludeAttributeClassTopic)|公用衍生類別宣告以及 Web 服務描述語言 \(WSDL\) 文件的公用方法傳回值。|當產生結構描述時應包含類別 \(在序列化時辨認\)。|  
|[XmlRootAttribute](frlrfSystemXmlSerializationXmlRootAttributeClassTopic)|公用類別宣告|控制做為 XML 根項目之屬性目標的 XML 序列化。請使用屬性更進一步指定命名空間與項目名稱。|  
|[XmlTextAttribute](frlrfSystemXmlSerializationXmlTextAttributeClassTopic)|公用屬性與欄位。|屬性或欄位應序列化成 XML 文字。|  
|[XmlTypeAttribute](frlrfSystemXmlSerializationXmlTypeAttributeClassTopic)|公用類別宣告|XML 型別的名稱與命名空間。|  
  
 除了這些在 [System.Xml.Serialization](frlrfSystemxmlserialization) 命名空間都找得到的屬性之外，您也可以對欄位套用 [System.ComponentModel.DefaultValueAttribute](frlrfSystemComponentModelDefaultValueAttributeClassTopic) 屬性。如果未指定任何值，**DefaultValueAttribute** 會設定將自動指派給成員的值。  
  
 若要控制編碼 SOAP XML 序列化，請參閱[控制編碼 SOAP 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)。  
  
## 請參閱  
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [使用屬性控制 XML 序列化](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)   
 [HOW TO：指定 XML 資料流的替代項目名稱](../../../docs/framework/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)   
 [HOW TO：序列化物件](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [HOW TO：還原序列化物件](../../../docs/framework/serialization/how-to-deserialize-an-object.md)