---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: b1cec9272a1de029ab72ea4d5f36c74630e5b93a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089493"
---
# <a name="contracttypenames"></a>\<contractTypeNames>
組態區段，這個區段會指定合約型別名稱清單 (要搜尋之服務的合約名稱)，以及通常用於搜尋服務的準則。 如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。 請注意，在 Windows Communication Foundation (WCF) 端點僅支援一個合約。  
  
 \<system.ServiceModel>  
\<standardEndpoints>  
  
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
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|合約型別名稱是一種屬性，它是指一組通常用於搜尋服務的準則。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<findCriteria>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。 準則可以分組為搜尋準則 （指定您要尋找的服務），以及尋找終止準則 （搜尋應持續多久）。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
