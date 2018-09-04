---
title: '&lt;tcpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 92590f556d93859e8681eea8f8f05da4f560e150
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563935"
---
# <a name="lttcptransportgt"></a>&lt;tcpTransport&gt;
定義 TCP 傳輸，通道可使用此傳輸來傳輸自訂繫結的訊息。  
  
 \<system.serviceModel>  
\<繫結 >  
\<customBinding>  
\<繫結 >  
\<tcpTransport>  
  
## <a name="syntax"></a>語法  
  
```xml  
<tcpTransport   
      channelInitializationTimeout="TimeSpan"   
      connectionBufferSize="Integer"   
      hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      manualAddressing="Boolean"   
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxOutputDelay="TimeSpan"  
      maxPendingAccepts="Integer"   
      maxPendingConnections="Integer"  
      maxReceivedMessageSize="Integer"   
      portSharingEnabled="Boolean"  
      teredoEnabled="Boolean"  
      transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >  
      <connectionPoolSettings  
            groupName="String"  
            idleTimeout"TimeSpan"  
            leaseTimeout="TimeSpan"  
            maxOutboundConnectionsPerEndpopint="Integer" />  
</tcpTransport>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|channelInitializationTimeout|取得或設定接受通道初始化的時間限制。  通道在中斷連接之前，可以處於初始化狀態中的最長時間 (以秒為單位)。 這個配額包含 TCP 連接可以使用 .Net Message Framing 通訊協定自行驗證所花費的時間。 用戶端必須先傳送一些初始資料，讓伺服器有足夠的資訊來執行驗證。 預設為 30 秒。|  
|connectionBufferSize|取得或設定用來在用戶端或服務的網路上，傳輸已序列化訊息區塊 (Chunk) 的緩衝區大小。|  
|hostNameComparisonMode|取得或設定值，這個值會指出在比對 URI 時主機名稱是否會用來取用服務。|  
|listenBacklog|Web 服務可擱置之佇列連線要求的最大數目。 `connectionLeaseTimeout` 屬性會限制用戶端在擲回連線例外狀況之前，等待連線的持續時間。 這是通訊端層級屬性，用來控制 Web 服務可擱置之佇列連線要求的最大數目。 當 ListenBacklog 太低時，WCF 會停止接受要求，因此將捨棄新的連接直到伺服器認可佇列中部分現有連接為止。預設值為 16 * 處理器數量。|  
|manualAddressing|取得或設定值，這個值會指出是否需要訊息的手動定址。|  
|maxBufferPoolSize|取得或設定此傳輸所使用之任何緩衝區集區的大小上限。|  
|maxBufferSize|取得或設定要使用之緩衝區的大小上限。 對於已進行資料流處理的訊息，這個值至少應為訊息標頭的最大可能大小 (可在緩衝模式中讀取)。|  
|maxOutputDelay|取得或設定訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。|  
|maxPendingAccepts|取得或設定可用於處理服務傳入連線的擱置中非同步接受作業的數目上限。|  
|maxPendingConnections|取得或設定服務上等待分派之連線的數目上限。|  
|maxReceivedMessageSize|取得及設定可接收之可允許的訊息大小上限。|  
|portSharingEnabled|布林值，指定是否啟用這個連線的 TCP 連接埠共用功能。 如果這是 `false`，則每個繫結將使用它自己的獨佔連接埠。 預設為 `false`。<br /><br /> 這個設定只與服務有關。 用戶端不受影響。<br /><br /> 使用這個設定必須將 [啟動類型] 改為 [手動] 或 [自動]，以啟用 Windows Communication Foundation (WCF) TCP Port Sharing Service。|  
|teredoEnabled|布林值，指定是否啟用 Teredo (對防火牆後的用戶端進行定址的技術)。 預設為 `false`。<br /><br /> 這個屬性會針對基礎 TCP 通訊端啟用 Teredo。 如需詳細資訊，請參閱 < [Teredo 概觀](https://go.microsoft.com/fwlink/?LinkId=95339)。<br /><br /> 這個屬性只適用於 [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] 和 [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]。 [!INCLUDE[wv](../../../../../includes/wv-md.md)] 具有整部機器的 Teredo 組態選項，所以在執行 Vista 時，會忽略這個屬性。 Teredo 需要用戶端和服務電腦都已安裝 Microsoft IPv6 堆疊並正確設定，才能使用 Teredo。 如需設定 Teredo 的詳細資訊，請參閱[Teredo 概觀](https://go.microsoft.com/fwlink/?LinkId=95339)。 如需詳細資訊，請參閱 < [Windows Server 2003 技術中心](https://go.microsoft.com/fwlink/?LinkId=49888)。|  
|transferMode|取得或設定值，這個值表示訊息是否使用連線導向傳輸進行緩衝或資料流處理。|  
|connectionPoolSettings|為具名管道繫結指定其他連線集區設定。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<繫結 >](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 這個傳輸會使用以下格式的 URI "net.tcp://hostname:port/path"。 其他 URI 元件是選擇性的。  
  
 `tcpTransport` 項目是在建立自訂繫結時的起點，該繫結會實作 TCP 傳輸通訊協定。 這個傳輸已針對 WCF 至 WCF 的通訊最佳化。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [傳輸](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
