---
title: "&lt;servicePointManager&gt; 項目 (網路設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<servicePointManager> 項目"
  - "servicePointManager 項目"
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 16
---
# &lt;servicePointManager&gt; 項目 (網路設定)
設定網路資源連線。  
  
## 語法  
  
```  
  
      <servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**描述**|  
|------------|------------|  
|`checkCertificateName`|指定系統是否應該先驗證憑證上的名稱符合伺服器主機名稱，然後再使用憑證。  預設值是 `true`。|  
|`checkCertificateRevocationList`|指定系統是否應該先檢查是否已撤銷憑證，然後再使用憑證。  預設值是 `false`。|  
|`dnsRefreshTimeout`|指定在搭配使用 DNS Round Robin 選項的情況下，要多久的時間來快取網域名稱服務 \(DNS\)，以毫秒為單位。  預設值為 120,000 毫秒 \(兩分鐘\)。|  
|`enableDnsRoundRobin`|指定具有多個網際網路通訊協定 \(IP\) 位址之主機名稱的 DNS 解析是否會傳回所有位址，或者只傳回第一個位址。  預設值是 `false`。|  
|`encryptionPolicy`|指定在 <xref:System.Net.ServicePointManager> 執行個體上套用至 SSL\/TLS 工作階段的加密原則。  可能的值相當於 <xref:System.Net.Security.EncryptionPolicy> 列舉的值。  當加密原則設定為 `NoEncryption` 時，需要使用 <xref:System.Security.Authentication.CipherAlgorithmType>。  預設值是 `RequireEncryption`。|  
|`expect100Continue`|指定 POST 方法是否預期會收到來自伺服器的 `100-continue` 回應。  預設值是 `true`。|  
|`useNagleAlgorithm`|指定由服務點管理員控制的連線是否會使用 Nagle 演算法。  預設值是 `true`。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## 備註  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 請參閱  
 <xref:System.Net.ServicePointManager>   
 <xref:System.Net.Security.EncryptionPolicy>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)