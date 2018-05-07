---
title: 控制編碼 SOAP 序列化的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: b7f0d8bf7c7c1013937f7ce0a87c326b707fbc6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>控制編碼 SOAP 序列化的屬性 
全球資訊網協會 (www.w3.org) 的文件《Simple Object Access Protocol (SOAP) 1.1》，其中包含描述 SOAP 參數如何編碼的選擇性章節 (第 5 節)。 若要遵循第 5 節的規格，您必須使用在 <xref:System.Xml.Serialization> 命名空間中的特殊屬性集。 套用適合類別與類別成員的那些屬性，然後使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化類別的執行個體。  
  
 下表顯示屬性、其可套用位置及作用。 如需使用這些屬性來控制 XML 序列化的詳細資訊，請參閱[如何：將物件序列化為 SOAP 編碼的 XML 資料流](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)和[如何：覆寫編碼的 SOAP XML 序列化](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)。  
  
 如需屬性的詳細資訊，請參閱[屬性](../../../docs/standard/attributes/index.md)。  
  
|屬性|適用於|指定|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|公用欄位、屬性、參數或傳回值。|類別成員將會序列化成 XML 屬性。|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|公用欄位、屬性、參數或傳回值。|類別將會序列化成 XML 項目。|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|為列舉識別項的公用欄位。|列舉成員的項目名稱。|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|公用屬性與欄位。|所屬類別序列化時，略過屬性或欄位。|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|公用衍生類別宣告以及 Web 服務描述語言 (WSDL) 文件的公用方法。|當產生結構描述時應包含型別 (在序列化時辨認)。|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|公用類別宣告|類別應序列化成 XML 型別。|  
  
## <a name="see-also"></a>另請參閱  
 [XML 和 SOAP 序列化](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [如何：將物件序列化為 SOAP 編碼的 XML 資料流](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [如何：覆寫已編碼的 SOAP XML 序列化](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [屬性](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [如何：序列化物件](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [如何：還原序列化物件](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
