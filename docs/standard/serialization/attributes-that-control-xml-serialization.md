---
title: 控制 XML 序列化的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
ms.openlocfilehash: 4acc17db83817d5aa78c9a91bfdac4e775de3743
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076536"
---
# <a name="attributes-that-control-xml-serialization"></a>控制 XML 序列化的屬性
您可以將下表中的屬性套用到類別和類別成員，以便控制 <xref:System.Xml.Serialization.XmlSerializer> 序列化或還原序列化類別之執行個體的方式。 若要了解這些屬性如何控制 XML 序列化，請參閱[使用屬性控制 XML 序列化](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)。  
  
 這些屬性也可用來控制 XML Web Service 產生的常值樣式 SOAP 訊息。 如需將這些屬性套用至 XML Web Service 方法的詳細資訊，請參閱[以 XML Web Service 進行 XML 序列化](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)。  
  
 如需屬性的詳細資訊，請參閱[屬性](../../../docs/standard/attributes/index.md)。  
  
|屬性|適用於|指定|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|公用欄位、屬性、參數或傳回 <xref:System.Xml.XmlAttribute> 物件陣列的傳回值。|當還原序列化時，陣列將填入代表所有結構描述未知之 XML 屬性的 <xref:System.Xml.XmlAttribute> 物件。|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|公用欄位、屬性、參數或傳回 <xref:System.Xml.XmlElement> 物件陣列的傳回值。|當還原序列化時，陣列將填入代表所有結構描述未知之 XML 項目的 <xref:System.Xml.XmlElement> 物件。|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|公用欄位、屬性、參數或傳回複雜物件陣列的傳回值。|陣列的成員將產生為 XML 陣列的成員。|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|公用欄位、屬性、參數或傳回複雜物件陣列的傳回值。|可插入陣列的衍生型別。 通常與 <xref:System.Xml.Serialization.XmlArrayAttribute> 一起套用。|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|公用欄位、屬性、參數或傳回值。|成員將會序列化成 XML 屬性。|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|公用欄位、屬性、參數或傳回值。|使用列舉型別可進一步明確識別成員。|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|公用欄位、屬性、參數或傳回值。|欄位或屬性將序列化成 XML 項目。|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|為列舉識別項的公用欄位。|列舉成員的項目名稱。|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|公用屬性與欄位。|所屬類別序列化時，略過屬性或欄位。|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|公用衍生類別宣告以及 Web 服務描述語言 (WSDL) 文件的公用方法傳回值。|當產生結構描述時應包含類別 (在序列化時辨認)。|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|公用類別宣告|控制做為 XML 根項目之屬性目標的 XML 序列化。 請使用屬性更進一步指定命名空間與項目名稱。|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|公用屬性與欄位。|屬性或欄位應序列化成 XML 文字。|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|公用類別宣告|XML 型別的名稱與命名空間。|  
  
 除了這些在 <xref:System.Xml.Serialization> 命名空間都找得到的屬性之外，您也可以對欄位套用 <xref:System.ComponentModel.DefaultValueAttribute> 屬性。 如果未指定任何值，**DefaultValueAttribute** 會設定將自動指派給成員的值。  
  
 若要控制編碼的 SOAP XML 序列化，請參閱[控制編碼 SOAP 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)。  
  
## <a name="see-also"></a>另請參閱

- [XML 和 SOAP 序列化](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- <xref:System.Xml.Serialization.XmlSerializer>  
- [使用屬性控制 XML 序列化](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
- [如何：指定 XML 資料流的替代元素名稱](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
- [如何：序列化物件](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [如何：還原序列化物件](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
