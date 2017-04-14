---
title: "&lt;clientCredentials&gt; 的 &lt;windows&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;clientCredentials&gt; 的 &lt;windows&gt; 項目
指定要用於代表用戶端的 Windows 認證的設定。  
  
## 語法  
  
```  
  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`allowedImpersonationLevel`|設定用戶端與伺服器通訊的模擬喜好設定。  用戶端選取的模擬模式不會在伺服器上強制使用。  有效值包括以下的值：<br /><br /> -   Identification：伺服器可取得用戶端的身分識別和權限，但無法模擬用戶端。<br />-   Impersonation：伺服器可在本機系統上模擬用戶端的安全性內容。<br />-   Delegation：伺服器可在遠端系統上模擬用戶端的安全性內容。<br />-   Anonymous：伺服器無法模擬或識別用戶端。<br />-   None：未指派模擬等級。<br /><br /> 預設為 Identification。  此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。|  
|`allowNtlm`|將這個屬性設定為 `true` 時，如果 Kerberos 無法使用，會允許驗證降級為 NTLM。<br /><br /> 將這個屬性設定為 `false`，可以讓 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 在使用 NTLM 時能夠盡力擲回例外狀況。  請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>   
 <xref:System.ServiceModel.Security.WindowsClientCredential>   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)