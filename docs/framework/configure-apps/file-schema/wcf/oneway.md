---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f4a9422f4385e37a61ec85d680fcf7743a57bc0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932935"
---
# <a name="oneway"></a>\<oneWay>
針對自訂繫結啟用封包路由和使用單向方法。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<系結 >  
\<oneWay>  
  
## <a name="syntax"></a>語法  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`packetRoutable`|布林值，指定是否啟用封包路由。 預設為 `false`。|  
|`MaxAcceptedChannels`|整數，指定可接受的通道數目上限。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> 物件，包含目前通道的通道集區的屬性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 如果要啟用封包路由，便需要這個項目提供的單向轉換層。 使用者可以建立自訂繫結，將這個繫結置於工作階段感知或要求-回覆傳輸層上，讓它啟用路由傳送封包功能。 當您要以較原始的方式來公開單向方法時，也可以使用這個項目。 還有其他轉換可套用至這一層，例如複合雙工和可信賴傳訊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
