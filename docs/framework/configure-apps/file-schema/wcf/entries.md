---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 610ba29ec98f4b1f2a9b1db3542bcb3aefb46457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925656"
---
# <a name="entries"></a>\<專案 >
這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。  
  
 \<system.serviceModel>  
\<路由 >  
\<routingTables>  
\<資料表 >  
\<專案 >  
  
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
|[\<filters>](filters-of-routing.md)|將篩選條件對應至先前定義的用戶端端點。 將符合此篩選條件的訊息傳送至這個目的地。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<routing>](routing.md)|包含路由表的組態區段。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
