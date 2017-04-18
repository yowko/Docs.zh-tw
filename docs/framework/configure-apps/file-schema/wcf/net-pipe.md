---
title: "&lt;net.pipe&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# &lt;net.pipe&gt;
指定 Named Pipe Activation Service 的組態設定，該服務會管理具名管道連線的存留期，並且會處理透過具名管道送達的啟用要求。  
  
## 語法  
  
```  
  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
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
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## 類型  
 `Type`  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`maxPendingAccepts`|整數，指定共用服務之接聽端點上、未完成之並行接收執行緒的數目上限。  預設值為 2。|  
|`maxPendingConnections`|整數，指定可以等候分派之連線的數目上限。  預設值為 100。|  
|`receiveTimeout`|<xref:System.Timespan>，指定讀取框架資料以及從基礎連線執行連線分派的逾時。  預設為 "00:00:10"|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<allowAccounts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|組態項目的集合，其中包含 `securityIdentifier` 屬性，此屬性可為裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務且已授權可連線共用服務的處理序指定使用者帳戶。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.serviceModel.activation\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|包含 SMSvcHost.exe 接聽程式處理序的組態設定。|  
  
## 請參閱  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>