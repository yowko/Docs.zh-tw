---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f9e64e667befb70d617574b2a03c3e6bebb2a143
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925595"
---
# <a name="filtertable"></a>\<filterTable>
表示路由表, 其中包含用來評估訊息的篩選器清單, 以及當篩選準則評估為 true 時, 要將訊息路由傳送至其中的用戶端端點。  
  
 \<system.serviceModel>  
\<路由 >  
\<routingTables>  
\<資料表 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|項目|描述|  
|-------------|-----------------|  
|NAME|字串，包含這個組態項目的唯一名稱。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|當篩選條件相符時，路由篩選器與訊息傳送目標端點之間的對應。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<routing>](routing.md)|包含路由表的組態區段。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
