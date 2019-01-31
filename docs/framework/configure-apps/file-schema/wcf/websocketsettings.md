---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 298bf27b171772bb039b11b5e5de70e7d45b061d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258435"
---
# <a name="websocketsettings"></a>\<webSocketSettings>
用來指定 Web 通訊端設定的組態元素。  
  
\<system.ServiceModel>  
\<bindings>  
\<netHttpBinding>  
  
## <a name="syntax"></a>語法  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|createNotificationOnConnection|指定是否在連接時傳送通知。|  
|disablePayloadMasking|指定是否停用 Web 通訊端遮罩。|  
|keepAliveInterval|指定保持運作的間隔。|  
|maxPendingConnections|指定服務上等待分派的連線數目上限。|  
|receiveBufferSize|指定接收緩衝區的大小。|  
|sendBufferSize|指定傳送緩衝區的大小。|  
|subProtocol|指定 Web 通訊端子通訊協定。|  
|transportUsage|指定何時要使用 Web 通訊端。|  
  
## <a name="transportusage-attribute"></a>transportUsage 屬性  
  
|值|描述|  
|-----------|-----------------|  
|WhenDuplex|當合約為雙工合約時，使用 Web 通訊端通訊協定。|  
|永遠|不論合約為何，永遠使用 Web 通訊端通訊協定。|  
|永不|永遠不使用 Web 通訊端通訊協定。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|\<netHttpBinding>|指定 NetHttpBinding|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用\<webSocketSettings > 項目。  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
