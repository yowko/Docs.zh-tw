---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 61b23957c56bad81598dd65b0dd68f7b44d329e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146792"
---
# <a name="mtommessageencoding"></a>\<mtomMessageEncoding>
指定編碼和訊息版本處理，用於 SOAP 訊息傳輸最佳化機制 (Message Transmission Optimization Mechanism，MTOM) 的訊息。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<mtomMessageEncoding>  
  
## <a name="syntax"></a>語法  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|maxBufferSize|整數，指定可使用的緩衝區大小上限。|  
|maxReadPoolSize|整數，指定可以同時讀取而不需配置新讀取器的訊息數。 較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。 預設值為 64。|  
|maxWritePoolSize|整數，指定可以同時傳送而不需配置新寫入器的訊息數。 較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。 預設值為 16。|  
|messageVersion|指定使用這個繫結所傳送訊息的 SOAP 版本。 有效值為<br /><br /> -   Soap11Addressing1<br />-   Soap12Addressing10<br /><br /> 預設為 Soap12Addressing10。 此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。|  
|writeEncoding|指定要在繫結上發出訊息時使用的字元集編碼方式。 有效值為<br /><br /> -UnicodeFffeTextEncoding:Unicode BigEndian 編碼方式<br />-Utf16textencoding:unicodeUnicode 編碼<br />-Utf8TextEncoding:8 位元編碼<br /><br /> 預設為 Utf8TextEncoding。 此屬性的型別為 <xref:System.Text.Encoding>。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。 此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 編碼是將訊息轉換成位元組序列的處理序， 解碼則是相反的處理序。 Windows Communication Foundation (WCF) 包含三種類型的 SOAP 訊息的編碼方式：文字、 二進位和訊息傳輸最佳化機制 (MTOM)。  
  
 `MtomMessageEncoding` 項目會為使用訊息傳輸最佳化機制 (MTOM) 編碼的訊息，指定使用的字元編碼、訊息版本控制以及其他設定。 MTOM 是在 WCF 訊息中傳輸二進位資料的有效技術。 MTOM 編碼器會嘗試在效率和互通性之間建立平衡。 MTOM 編碼會以文字格式傳輸大部分的 XML，但是在傳輸大型區塊的二進位資料時，會依照原狀來傳送 (不轉換成其 base64 編碼格式)，好讓這些資料最佳化。  
  
## <a name="example"></a>範例  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [訊息編碼](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [選擇訊息編碼器](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
