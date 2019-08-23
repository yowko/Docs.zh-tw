---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 032139b714aa11079c7ee8610c332e404b3981ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919005"
---
# <a name="exposedmethod"></a>\<exposedMethod >
表示 COM+ 方法，這個方法會在 COM+ 元件上的介面公開為 Web 服務時公開。  
  
 \<system.ServiceModel>  
\<comContracts>  
\<comContract>  
\<方法 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|NAME|包含 COM+ 方法的字串，這個方法會在 COM+ 元件上的介面公開為 Web 服務時公開。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|[ \<ExposedMethod >](exposedmethod.md)元素的集合。|  
  
## <a name="remarks"></a>備註  
 COM+ 整合設定工具 (ComSvcConfig.exe) 可用來從 COM 介面加入特定的方法，使這些方法可以出現在所產生的服務合約上。  
  
 例如，您可以使用下列命令，從 `IFinances`.Financial 元件上的 `ItemOrders` COM 介面將三個具名方法加入至所產生的服務合約中。  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 當您同時執行 ComSvcConfig 時, 它會產生下列服務合約, 並將先前所述的方法列示為[ \<exposedMethod >](exposedmethod.md)元素。  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 在服務初始化期間, 執行時間會藉由反映並僅新增[ \<exposedMethod >](exposedmethod.md)專案清單中包含的方法, 嘗試產生服務合約。 這時會針對每個未包含在服務合約中的介面方法加以追蹤。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [整合 COM 應用程式](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [如何：設定 COM + 服務設定](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
