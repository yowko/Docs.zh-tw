---
title: "憑證用戶端的訊息安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
caps.latest.revision: 16
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 16
---
# 憑證用戶端的訊息安全性
下列狀況顯示使用訊息安全性模式加以保障的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端及服務。用戶端與服務皆以憑證驗證。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][分散式應用程式安全性](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).  
  
 如需應用程式範例，請參閱[訊息安全性憑證](../../../../docs/framework/wcf/samples/message-security-certificate.md)。  
  
 ![包含憑證的用戶端](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")  
  
|特性|描述|  
|--------|--------|  
|安全性模式|訊息|  
|互通性|僅限 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]|  
|驗證 \(伺服器\)|使用服務憑證|  
|驗證 \(用戶端\)|使用用戶端憑證|  
|完整性|是|  
|機密性|是|  
|傳輸|HTTP|  
|繫結|<xref:System.ServiceModel.WSHttpBinding>|  
  
## 服務  
 下列程式碼和組態要獨立執行。執行下列其中一項：  
  
-   使用不含組態的程式碼建立獨立服務。  
  
-   使用提供的組態建立服務，但不要定義任何端點。  
  
### 程式碼  
 下列程式碼顯示如何建立使用訊息安全性產生安全內容的服務端點。  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### 組態  
 可使用以下組態來取代程式碼。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCerficiateClient"   
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## 用戶端  
 下列程式碼和組態要獨立執行。執行下列其中一項：  
  
-   使用此程式碼 \(和用戶端程式碼\) 建立獨立用戶端。  
  
-   建立未定義任何端點位址的用戶端，然後改用可接受組態名稱當做引數的用戶端建構函式。例如：  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### 程式碼  
 下列程式碼會建立用戶端。繫結會使用訊息模式安全性，而且用戶端認證類型設為 `Certificate`。  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### 組態  
 下列組態指定使用端點行為的用戶端憑證。如需關於憑證的詳細資訊，請參閱 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。程式碼也使用 \<`identity`\> 項目指定預期伺服器識別的網域名稱系統 \(DNS\)。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]身分識別的詳細資訊，請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## 請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Windows Server AppFabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)