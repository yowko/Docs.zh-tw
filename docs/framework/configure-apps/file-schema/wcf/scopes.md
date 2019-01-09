---
title: '&lt;範圍&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 7afab700c2d9eb91ffe57bfefaf5864782a0af5f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145324"
---
# <a name="ltscopesgt"></a>&lt;範圍&gt;
包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。  
  
\<system.ServiceModel>  
\<行為 >  
\<endpointBehaviors>  
\<行為 >  
\<endpointDiscovery >  
\<範圍 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|屬性|描述|  
|---------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|加入端點的範圍資訊，可用於比對尋找服務的準則。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<endpointDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
