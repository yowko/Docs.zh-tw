---
title: "&lt;discoveryClient&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;discoveryClient&gt;
組態項目，用於建立自訂繫結，該繫結可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。  
  
## 語法  
  
```  
  
<discoveryClient discoveryEndpoint=”String” >  
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
</discoveryClient>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|discoveryEndpoint|字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。  您可以將標準群組為搜尋準則 \(指定您要尋找的服務\)，並且尋找終止準則 \(搜尋應持續的時間長短\)。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>   
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>