---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855162"
---
# <a name="findcriteria"></a>\<findCriteria>
組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。 準則可以分組為搜尋準則（指定您要尋找的服務），並尋找終止準則（搜尋應持續的時間長度）。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<尋找準則 >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|持續期間|TimeSpan 值，用於指定等候網路服務回覆的時間上限。 預設持續時間為 20 秒。|  
|maxResults|整數，用於指定等候網路服務或網際網路服務傳來的回覆數量上限。 如果在經過 `duration` 屬性中指定的值之前所收到的回覆即超過數量上限，尋找作業就會結束。|  
|scopeMatchBy|URI，指定比對 Probe 訊息中的範圍與端點的範圍時要使用的比對演算法。<br /><br /> 支援的範圍比對規則有五種。 如果您不指定範圍比對規則，則會使用 `ScopeMatchByPrefix`。 如需詳細資訊，請參閱<xref:System.ServiceModel.Discovery.FindCriteria>。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|Configuration 元素的集合，其中包含工作流程服務合約類型的名稱。|  
|\<尋找準則 > 的\<延伸模組 >|XML 項目物件的集合，這些物件會提供擴充。|  
|[\<scopes>](scopes.md)|物件的集合，這些物件包含尋找作業找尋特定服務時所用的絕對 URI。<br /><br /> 如果找到特定的服務，就會順利比對服務 URI 和範圍 URI (有時候會藉助處理複雜比對的範圍規則)。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|包含應用程式參與服務探索處理序做為用戶端所需的設定。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
