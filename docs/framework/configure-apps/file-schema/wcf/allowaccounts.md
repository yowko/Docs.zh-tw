---
title: "&lt;allowAccounts&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;allowAccounts&gt;
包含組態項目的集合，這些項目指定裝載 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務之處理序的使用者帳戶，並被授予共用服務的連線存取權。  
  
 \<system.serviceModel.activation\>  
  
## 語法  
  
```  
  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|屬性|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|加入裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務之處理序的使用者帳戶，並獲授予共用服務的連線權限。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<net.pipe\>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) 或[\<net.tcp\>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)|指定 Net Pipe 或 TCP 共用服務的組態設定。|  
  
## 請參閱  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>   
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>   
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>   
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>