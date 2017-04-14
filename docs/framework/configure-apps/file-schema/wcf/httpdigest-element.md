---
title: "&lt;httpDigest&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;httpDigest&gt; 項目
指定對服務驗證用戶端時，所使用的摘要式類型認證。  
  
## 語法  
  
```  
  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`impersonationLevel`|設定用戶端與伺服器通訊的模擬喜好設定。  用戶端選取的模擬模式不會在伺服器上強制使用。  有效值包括以下的值：<br /><br /> -   Identification：伺服器可取得用戶端的身分識別和權限，但無法模擬用戶端。<br />-   Impersonation：伺服器可在本機系統上模擬用戶端的安全性內容。<br />-   Delegation：伺服器可在遠端系統上模擬用戶端的安全性內容。<br />-   Anonymous：伺服器無法模擬或識別用戶端。<br />-   None：未指派模擬等級。<br /><br /> 預設為 Identification。  此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
  
## 備註  
 摘要是指使用演算法和一組輸入所決定的雜湊。  驗證者和被驗證者一致同意某個演算法，並交換做為輸入的資料。  用戶端可計算雜湊，並將它傳送至服務。  服務也會計算雜湊並比較兩者的值。  比對會驗證用戶端。  
  
 此功能必須與 Windows 和 Internet Information Services \(IIS\) 上的 Active Directory 一起啟用。  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [IIS 6.0 中的摘要式驗證](http://go.microsoft.com/fwlink/?LinkId=88443)。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>   
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>   
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [確保用戶端的安全](../../../../../docs/framework/wcf/securing-clients.md)   
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)