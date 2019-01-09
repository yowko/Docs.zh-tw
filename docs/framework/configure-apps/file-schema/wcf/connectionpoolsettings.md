---
title: '&lt;Namedpipetransport&gt;'
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 2d79b3e28d1a80011cba7c515d979ae0037785a5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149523"
---
# <a name="ltconnectionpoolsettingsgt"></a>&lt;Namedpipetransport&gt;
為具名管道繫結指定其他連線集區設定。  
  
 \<system.serviceModel>  
\<繫結 >  
\<customBinding>  
\<繫結 >  
\<namePipeTransport >  
\<p >  
  
## <a name="syntax"></a>語法  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`groupName`|定義用於傳出通道之連線集區名稱的字串。 在資料流處理模式中，不會共用連線，意指會停用連線集區。 預設為 "default" 字串。 您可以修改這個值，將特定用戶端的連線隔離在不同群組中。|  
|`idleTimeout`|正的 <xref:System.TimeSpan>，指定連線在中斷連接之前，可以閒置的最長時間。 預設為 00:02:00。|  
|`maxOutboundConnectionsPerEndpoint`|正整數，指定與服務初始化之遠端端點連線的數目上限。 超過這個限制的連線都會進入佇列，直到低於此限制的空間可用為止。 `idleTimeout` 會限制在擲回例外狀況之前，連線保留在佇列中的持續期間。 預設值為 10。<br /><br /> 這個屬性會限制從用戶端到特定服務端點的同時作用中連線數目。 如果因為擁有更多個作用中的用戶端連線而超出這個值，對用戶端而言，服務可能會像是沒有回應。 在這種情況下，這個值應調整為超過預期的、用戶端對特定端點之同時連線的數目上限。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<Connectionpoolsettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|定義傳輸，此傳輸會使用具名管道產生可傳輸訊息的通道。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [傳輸](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
