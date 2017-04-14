---
title: "&lt;allowAccounts&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;allowAccounts&gt; 的 &lt;add&gt;
指定裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務並獲得共用服務連線存取權之處理序的使用者帳戶。  
  
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
  
|屬性|描述|  
|--------|--------|  
|securityIdentifier|字串，指定用於識別使用者帳戶的唯一識別碼。  預設值為 LocalSystem、Administrators、NS、LS 和 IIS\_USRS。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<allowAccounts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|組態項目的集合，其中包含 `securityIdentifier` 屬性，此屬性可為裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務且已授權可連線共用服務的處理序指定使用者帳戶。|  
  
## 範例  
 下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。  
  
```  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>   
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>   
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>   
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>