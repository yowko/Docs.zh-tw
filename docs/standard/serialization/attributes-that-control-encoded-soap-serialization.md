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
ms.openlocfilehash: 2961d9abc6c32e78b5a61e8f2bbea5cfcf6677bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794936"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>控制編碼 SOAP 序列化的屬性

名為 World Wide Web Consortium (W3C) 文件[簡易物件存取通訊協定 (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)包含描述 SOAP 參數如何編碼的選擇性章節 （第 5 節）。 若要遵循第 5 節的規格，您必須使用在 <xref:System.Xml.Serialization> 命名空間中的特殊屬性集。 套用適合類別與類別成員的那些屬性，然後使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化類別的執行個體。

下表顯示屬性、其可套用位置及作用。 如需使用這些屬性控制 XML 序列化的詳細資訊，請參閱[How to:物件序列化為 SOAP 編碼的 XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)和[How to:覆寫編碼的 SOAP XML 序列化](how-to-override-encoded-soap-xml-serialization.md)。

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

- [XML 和 SOAP 序列化](xml-and-soap-serialization.md)
- [如何：將物件序列化為 SOAP 編碼的 XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [如何：覆寫編碼的 SOAP XML 序列化](how-to-override-encoded-soap-xml-serialization.md)
- [屬性](../../../docs/standard/attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [如何：將物件序列化](how-to-serialize-an-object.md)
- [如何：還原序列化物件](how-to-deserialize-an-object.md)
