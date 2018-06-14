---
title: '&lt;namedPipeTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 652cb551fb318d43d4284dbee48aeb994f056692
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746793"
---
# <a name="ltnamedpipetransportgt"></a>&lt;namedPipeTransport&gt;
定義傳輸，這個傳輸會使通道在包含於自訂繫結時使用具名管道來傳輸訊息。  
  
\<system.serviceModel>  
\<繫結 >  
\<customBinding>  
\<繫結 >  
\<namePipeTransport >  
  
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
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|ChannelInitializationTimeout|取得或設定<xref:System.TimeSpan>，決定通道正在中斷連接之前，可以處於初始化狀態中的最大時間。|  
|ConnectionBufferSize|取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。|  
|hostNameComparisonMode|取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。|  
|manualAddressing|取得或設定值，這個值會指出是否需要訊息的手動定址。|  
|maxBufferPoolSize|取得或設定大小上限，以位元組為單位的傳輸所使用的任何緩衝區集區。|  
|maxBufferSize|取得或設定要使用之緩衝區的大小上限。 對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。|  
|maxOutputDelay|取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。|  
|maxPendingAccepts|取得或設定的服務可以有在接聽程式上等待處理服務傳入連線的通道數目上限。|  
|maxPendingConnections|取得或設定服務上等待分派之連線的數目上限。|  
|maxReceivedMessageSize|取得及設定可允許訊息大小上限，以位元組為單位，可接收。|  
|transferMode|取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。|  
|[\<n > 的\<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|為具名管道繫結指定其他連線集區設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<繫結 >](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
這個傳輸會使用以下格式的 URI "net.pipe://hostname/path"。 其他 URI 元件是選擇性的。  
  
`namedPipeTransport` 項目建立自訂繫結時的起點，此繫結會實作具名管道傳輸通訊協定。 這個傳輸是用於電腦的 Windows Communication Foundation (WCF) 至 WCF 通訊。  
  
## <a name="see-also"></a>另請參閱  
<xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
<xref:System.ServiceModel.Channels.TransportBindingElement>   
<xref:System.ServiceModel.Channels.CustomBinding>   
[傳輸](../../../../../docs/framework/wcf/feature-details/transports.md)   
[選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
[繫結](../../../../../docs/framework/wcf/bindings.md)   
[擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
[自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
[\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
