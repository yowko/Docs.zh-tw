---
title: "&lt;serviceActivations&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;serviceActivations&gt;
組態項目，這個項目可讓您加入設定，這些設定定義會對應至您的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務型別的虛擬服務啟動設定。  如此一來，不需 .svc 檔案也能啟動裝載於 WAS\/IIS 中的服務。  
  
## 語法  
  
```  
  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|加入組態項目，此項目指定服務應用程式的啟動。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceHostingEnvironment\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|定義服務裝載環境為特定傳輸產生的類型。|  
  
## 備註  
 下列範例示範如何在您的 web.config 檔案中設定啟動設定。  
  
```  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 使用這個組態時，您不需要使用 .svc 檔案也可以啟動 GreetingService。  
  
 請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。  您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。  此外，`serviceHostingEnvironment` 是 machinetoApplication 可繼承的區段。  如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。  
  
 以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。  relatativeAddress 必須有副檔名，亦即  .svc、.xoml 或 .xamlx。  您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。  發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>   
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>   
 <xref:System.ServiceModel.ServiceHostingEnvironment>