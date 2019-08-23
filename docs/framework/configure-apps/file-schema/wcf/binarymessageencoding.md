---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 9b6b74200c807e6523ed3f7250945040bd12658d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919800"
---
# <a name="binarymessageencoding"></a>\<binaryMessageEncoding>
定義二進位訊息編碼器，以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<系結 >  
\<binaryMessageEncoding>  
  
## <a name="syntax"></a>語法  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|maxReadPoolSize|定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。 較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。 預設值為 64。|  
|maxSessionSize|正整數，設定用於編碼的緩衝區大小 (以位元組為單位)。 較大的緩衝區會增加編碼速度，但是會犧牲工作集的大小。 預設值為 2048。|  
|maxWritePoolSize|定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。 較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。 預設值為 16。|  
|messageVersion|指定已使用或必須使用的 SOAP 訊息和 WS-Addressing 版本。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。 此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 編碼是將訊息轉換成位元組序列的處理序， 解碼則是相反的處理序。 Windows Communication Foundation (WCF) 包含 SOAP 訊息的三種編碼類型:文字、二進位和訊息傳輸優化機制 (MTOM)。  
  
 `binaryMessageEncoding` 項目會指定 XML 的 .NET 二進位格式，並且提供指定字元編碼以及要使用之 SOAP 和 WS-Addressing 版本的選項。 二進位訊息編碼器會以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。 雖然這個編碼會讓訊息傳輸速度非常快，但是會失去以 WS-* 標準為基礎的互通性 (Interoperability)。  
  
## <a name="example"></a>範例  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [訊息編碼](message-encoding.md)
- [選擇訊息編碼器](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
