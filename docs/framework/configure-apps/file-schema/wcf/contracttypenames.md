---
title: "&lt;contractTypeNames&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;contractTypeNames&gt;
組態區段，這個區段會指定合約型別名稱清單 \(要搜尋之服務的合約名稱\)，以及通常用於搜尋服務的準則。  如果指定多個合約名稱，則只會回覆符合「所有」合約的服務端點。  請注意，在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 中，一個端點僅支援一個合約。  
  
## 語法  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <dynamicEndpoint>   
          <standardEndpoint>  
             <discoveryClientSettings discoveryEndpoint=”String” >  
               <findCriteria duration=”TimeSpan”  
                  maxResults=”Integer”   
                  scopeMatchBy=”Uri” >  
                  <contractTypeNames>  
                     <add name="String" namespace="String" />  
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
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|合約型別名稱是一種屬性，它是指一組通常用於搜尋服務的準則。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<findCriteria\>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。  您可以將標準群組為搜尋準則 \(指定您要尋找的服務\)，並且尋找終止準則 \(搜尋應持續的時間長短\)。|  
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.FindCriteria>   
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>   
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>