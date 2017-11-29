---
title: "&lt;項目&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b6d8d1c3797d60b26443e07cc527ea8b86f526e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltentriesgt"></a>&lt;項目&gt;
這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。  
  
 \<system.serviceModel >  
\<路由 >  
\<routingTables >  
\<資料表 >  
\<項目 >  
  
## <a name="syntax"></a>語法  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<篩選條件 >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|將篩選條件對應至先前定義的用戶端端點。 將符合此篩選條件的訊息傳送至這個目的地。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|包含路由表的組態區段。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
