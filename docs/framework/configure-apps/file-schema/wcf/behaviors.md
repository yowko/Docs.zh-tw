---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 8fcb5ac0c552d1ac2e849c95a5c0757d0c142f3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926400"
---
# <a name="behaviors"></a>\<行為 >
這個項目會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。  每個集合會定義分別由端點和服務使用的行為項目。 每個行為項目都由其唯一的 `name` 屬性所識別。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>語法  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|這個組態區段表示為特定端點定義的所有行為。|  
|[\<serviceBehaviors>](servicebehaviors.md)|這個組態區段表示為特定服務定義的所有行為。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|所有 Windows Communication Foundation (WCF) 組態項目的根項目。|  
  
## <a name="remarks"></a>備註  
 您可以使用 `<remove>` 項目移除集合中的特定行為。 若要這麼做，只需在 `name` 項目的 `<remove>` 屬性中提供要移除之行為的名稱。  您也可以使用 `<clear>` 項目來清除行為集合的所有內容，確保該行為集合在啟始時就是空的。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [使用行為來設定與擴充執行階段](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [設定用戶端行為](../../../wcf/configuring-client-behaviors.md)
- [指定用端執行階段行為](../../../wcf/specifying-client-run-time-behavior.md)
- [指定服務執行階段行為](../../../wcf/specifying-service-run-time-behavior.md)
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
