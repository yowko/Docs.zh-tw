---
title: "&lt;scopes&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4771c519edda36541034d9256beb858ef17763c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a>&lt;scopes&gt; 的 &lt;add&gt;
加入自訂的範圍 URI，這個 URI 可用於在查詢期間篩選服務端點。  
  
\<系統。ServiceModel >  
\<行為 >  
\<endpointBehaviors >  
\<行為 >  
\<endpointDiscovery >  
\<範圍 >  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|範圍|URI，其中包含端點的範圍資訊，可用於比對尋找服務的準則。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<範圍 >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
