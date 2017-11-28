---
title: "&lt;entries&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62236c604cd91c2dfe4b92cfaac4004fc18d439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a>&lt;entries&gt; 的 &lt;add&gt;
代表將篩選條件對應至先前定義之用戶端端點的路由項目。 將符合此篩選條件的訊息傳送至這個目的地。  
  
 \<system.serviceModel >  
\<路由 >  
\<routingTables >  
\<資料表 >  
\<項目 >  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|backupList|字串，指定端點備份清單的參考。|  
|endpoint|字串，指定對用戶端端點的參考，該端點會接收與 `filterName` 屬性指定之篩選條件相符的訊息。|  
|filterName|字串，指定對篩選條件項目的參考。|  
|priority|整數，指定這個項目的優先權。<br /><br /> 路由表中的項目會根據優先權進行評估，其中 0 表示優先順序最低。 具有特定優先順序的所有項目會同時評估，如果找不到符合目前優先順序的項目，則會評估下一個優先順序層級。<br /><br /> 這是選擇性的值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<路由 >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|包含路由組態項目的組態區段。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
