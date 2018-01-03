---
title: '&lt;n&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f804cdb57355b62db25a559dc3c5db7d4d69369e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltfindcriteriagt"></a>&lt;n&gt;
組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。 條件可以分組為搜尋準則 （指定您要尋找的服務），並且尋找終止準則 （搜尋應時間長短）。  
  
 \<系統。ServiceModel >  
\<Kind >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|持續期間|TimeSpan 值，用於指定等候網路服務回覆的時間上限。 預設時間長短為 20 秒。|  
|maxResults|整數，用於指定等候網路服務或網際網路服務傳來的回覆數量上限。 如果在經過 `duration` 屬性中指定的值之前所收到的回覆即超過數量上限，尋找作業就會結束。|  
|scopeMatchBy|URI，指定比對 Probe 訊息中的範圍與端點的範圍時要使用的比對演算法。<br /><br /> 支援的範圍比對規則有五種。 如果您不指定範圍比對規則，則會使用 `ScopeMatchByPrefix`。 如需詳細資訊，請參閱<xref:System.ServiceModel.Discovery.FindCriteria>。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<a d d >](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|組態項目集合，其中包含工作流程服務合約型別的名稱。|  
|\<延伸模組 > 的\<n >|XML 項目物件的集合，這些物件會提供擴充。|  
|[\<範圍 >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|物件的集合，這些物件包含尋找作業找尋特定服務時所用的絕對 URI。<br /><br /> 如果找到特定的服務，就會順利比對服務 URI 和範圍 URI (有時候會藉助處理複雜比對的範圍規則)。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<Kind >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|包含應用程式參與服務探索處理序做為用戶端所需的設定。|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
