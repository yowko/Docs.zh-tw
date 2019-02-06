---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: e13f23d6894083c8b507bdb73bea897c4845300f
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759636"
---
# <a name="webmessageencoding"></a>\<webMessageEncoding>
啟用在用於 Windows Communication Foundation (WCF) 繫結時，要讀取與寫入的純文字 XML、JavaScript Object Notation (JSON) 訊息編碼和「未經處理」二進位內容。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<webMessageEncoding>  
  
## <a name="syntax"></a>語法  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`maxReadPoolSize`|可以同時讀取，而不需配置新讀取器的訊息數。 較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。 每個內部編碼器 (text、JSON 與 "raw") 都預設有 64 個讀取器。<br /><br /> 增加這個數字會增加記憶體消耗量，但是可讓編碼器做好處理傳入訊息量突然暴增的準備，因為編碼器可以使用集區中已經建立的讀取器，而不必建立新的讀取器。|  
|`maxWritePoolSize`|可以同時傳送，而不需配置新寫入器的訊息數。 較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。 每個內部編碼器 (text、JSON 與 "raw") 都預設有 16 個寫入器。<br /><br /> 增加這個數字會增加記憶體消耗量，但是可讓編碼器做好處理傳出訊息量突然暴增的準備，因為編碼器可以使用集區中已經建立的寫入器，而不必建立新的寫入器。|  
|`writeEncoding`|指定要在繫結上發出訊息時使用的字元集編碼方式。 有效值為：<br /><br /> -UnicodeFffeTextEncoding:Unicode Bigendian 編碼方式。<br />-Utf16textencoding:unicodeUnicode 編碼方式。<br />-Utf8TextEncoding:8 位元編碼方式。<br /><br /> 預設為 Utf8TextEncoding。 此屬性的型別為 <xref:System.Text.Encoding>。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。 此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 編碼是將訊息轉換成位元組序列的處理序， 解碼則是相反的處理序。 這些處理序需要字元編碼的規格。  
  
 `webMessageEncoding` 項目的運作方式是委派給一系列的內部編碼器，以處理純文字 XML 和 JSON 編碼以及「原始」二進位資料。 這項委派是由複合訊息編碼器所完成。  
  
 在不使用 `webHttpBinding` 項目使用之 SOAP 傳訊的案例中，會使用這個繫結項目及其複合編碼器來控制其編碼方式。 這些案例包括 "Plain Old XML" (POX)、代表性狀態傳輸 (Representational State Transfer，REST)、Really Simple Syndication (RSS) 和 Atom 新聞訂閱，以及 Asynchronous JavaScript 與 XML (AJAX)。 複合訊息編碼器不支援 SOAP 或 WS-Addressing。  
  
 此繫結項目可藉由 `writeEncoding` 屬性，透過寫入字元編碼的方式進行設定。 提供的 <xref:System.Text.Encoding> 值會指定 JSON 和 Textual XML 案例在寫入時的行為。 在讀取時，任何有效的訊息編碼和文字編碼都是可解讀的。  
  
 `maxReadPoolSize` 和 `maxWritePoolSize` 也可以用來設定要分別配置之讀取器和寫入器的最大數目。 根據預設，將配置 64 個讀取器和 16 個寫入器。  
  
 預設複雜度條件約束也會設定使用[ \<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))項目，以防止阻絕服務 (DOS) 類別攻擊試圖使用訊息複雜性困住端點處理資源。  
  
## <a name="example"></a>範例  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [訊息編碼](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [選擇訊息編碼器](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
