---
title: "&lt;netMsmqBinding&gt; 的 &lt;message&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;netMsmqBinding&gt; 的 &lt;message&gt;
定義此 `netMsmqBinding` 繫結上的 SOAP 訊息安全性設定。  
  
## 語法  
  
```  
  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|algorithmSuite|設定訊息加密和金鑰包裝演算法，用來針對 MSMQ 傳輸上傳送的訊息實現訊息安全性。<br /><br /> 預設值是 `Aes256`。  此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。|  
|clientCredentialType|指定在為 MSMQ 傳輸上傳送的訊息執行用戶端驗證時，要使用的認證類型。  有效值包括以下的值：<br /><br /> -   None：這會允許服務與匿名用戶端互動。  服務和用戶端都不需要認證。<br />-   Windows：這會讓 SOAP 交換加入 Windows 認證的已驗證內容中。  如此一定會執行 Kerberos 驗證。<br />-   UserName：這會讓服務要求用戶端必須使用 UserName 認證進行驗證。  此案例中的認證必須使用 `clientCredentials` 行為來指定。 **Caution:**  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 不支援傳送密碼摘要，或是使用密碼衍生金鑰，甚至對訊息安全性使用該金鑰。  因此，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會在使用 UserName 認證時強制保護交換。  這個模式需要使用 `clientCredential` 行為和 `serviceCertificate` 在用戶端上指定服務憑證。 <br /><br /> -   Certificate：這會讓服務要求用戶端使用憑證來進行驗證。  此案例中的用戶端認證必須使用 `clientCredentials` 行為來指定。  此案例中的服務認證需要藉由指定 `serviceCertificate`，以使用 `clientCredentials` 行為來指定。<br />-   CardSpace：這會讓服務要求用戶端使用 CardSpace 來進行驗證。  `clientCredential` 行為中必須提供 `serviceCertiifcate`。<br /><br /> 預設值是 `Windows`。  此屬性的型別為 <xref:System.ServiceModel.MessageCredentialType>。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|定義繫結的安全性設定。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>   
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>   
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>   
 <xref:System.ServiceModel.MessageSecurityOverMsmq>   
 [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)