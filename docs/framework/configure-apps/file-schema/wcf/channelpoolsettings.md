---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44e79c7af470cefead8bcfb0ef96606ecde30383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltchannelpoolsettingsgt"></a>&lt;channelPoolSettings&gt;
指定自訂繫結的通道集區設定。  
  
 \<system.serviceModel >  
\<繫結 >  
\<customBinding >  
\<繫結 >  
\<oneWay >  
\<channelPoolSettings >  
  
## <a name="syntax"></a>語法  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`idleTimeout`|正的 <xref:System.TimeSpan>，指定集區中的通道在中斷連接之前，可以閒置的最長時間。 預設為 00:02:00。|  
|`leaseTimeout`|<xref:System.TimeSpan>，指定已傳回到集區之通道多久之後將關閉的間隔時間。 預設為 00:10:00。|  
|`maxOutboundChannelsPerEndpoint`|正整數，指定每個遠端端點可儲存在集區中的最大通道數目。 預設值為 10。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|啟用自訂繫結的封包路由。|  
  
## <a name="remarks"></a>備註  
 配額是一種用來避免資源過度耗費的原則機制。 這類配額會防止惡意或是無意間發生的阻斷服務 (DOS) 攻擊。 當設定自訂通道配額的時候，請使用這個項目。  
  
 `ChannelPoolSettings` 指定三種配額：  
  
-   `idleTimeout` 配額，可用來降低在伺服器上藉由佔用資源一段延長期間所產生的阻斷服務 (DOS) 攻擊情形。 在用戶端，設定正確的值可以增加與服務的連接可靠性。 預設值是依據最為保守穩當的資源配置所設定。 這個設定值適合開發環境和小規模的安裝情況。 如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。  
  
-   `leaseTimeout` 配額，其用途在於整合負載平衡器和改善可靠性。 預設值是依據保守的資源配置所設定。 這個設定值適合開發環境和小規模的安裝情況。 如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。  
  
-   `maxOutboundChannelsPerEndpoint` 配額會設定伺服器和用戶端雙方的快取限制，並可用來改善可靠性。 預設值是依據最為保守穩當的資源配置所設定，這個設定值適合開發環境和小規模的安裝情況。 如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
