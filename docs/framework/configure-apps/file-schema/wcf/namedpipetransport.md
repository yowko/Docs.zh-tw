---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: e5f1d49e0e3bb5f52c5e18577d556d25539434a9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400169"
---
# <a name="namedpipetransport"></a>\<namedPipeTransport>
定義傳輸，這個傳輸會使通道在包含於自訂繫結時使用具名管道來傳輸訊息。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namedPipeTransport >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|ChannelInitializationTimeout|取得或設定<xref:System.TimeSpan> ，這個值會決定通道在中斷連接之前，可以處於初始化狀態的最長時間。|  
|ConnectionBufferSize|取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。|  
|hostNameComparisonMode|取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。|  
|manualAddressing|取得或設定值，這個值會指出是否需要訊息的手動定址。|  
|maxBufferPoolSize|取得或設定傳輸所使用之任何緩衝集區的大小上限（以位元組為單位）。|  
|maxBufferSize|取得或設定要使用之緩衝區的大小上限。 對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。|  
|maxOutputDelay|取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。|  
|maxPendingAccepts|取得或設定服務可等待接聽程式來處理服務之連入連線的通道數目上限。|  
|maxPendingConnections|取得或設定服務上等待分派之連線的數目上限。|  
|maxReceivedMessageSize|取得並設定可接收的訊息大小上限（以位元組為單位）。|  
|transferMode|取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。|  
|[\<namedPipeTransport > 的\<connectionPoolSettings >](connectionpoolsettings.md)|為具名管道繫結指定其他連線集區設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
這個傳輸會使用以下格式的 URI "net.pipe://hostname/path"。 其他 URI 元件是選擇性的。  
  
`namedPipeTransport` 項目建立自訂繫結時的起點，此繫結會實作具名管道傳輸通訊協定。 這個傳輸是用於電腦的 Windows Communication Foundation (WCF) 至 WCF 通訊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [傳輸](../../../wcf/feature-details/transports.md)
- [選擇傳輸](../../../wcf/feature-details/choosing-a-transport.md)
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
