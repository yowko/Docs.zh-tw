---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c49c7cf3a196595556c2bf1b4ed4365bfe1e4cbf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704241"
---
# <a name="filtertables"></a>\<filterTables>
代表定義路由表的組態區段，該路由表包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。  
  
 \<system.serviceModel>  
\<路由 >  
\<routingTables>  
  
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
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<filters>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|路由表，其中包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|組態區段，其中包含路由篩選條件與路由表。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
