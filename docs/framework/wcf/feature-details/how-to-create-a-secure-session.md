---
title: "HOW TO：建立安全工作階段 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安全性 [WCF], 建立工作階段"
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# HOW TO：建立安全工作階段
利用 [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 繫結的例外狀況，當啟用訊息安全性時，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中由系統提供的繫結會自動使用安全工作階段。  
  
 根據預設，安全工作階段不會存留回收的 Web 伺服器。  當建立安全工作階段時，用戶端和服務會快取與安全工作階段有關聯的索引鍵。  當交換訊息時，只會交換快取索引鍵的識別碼。  如果回收 Web 伺服器，也會回收快取，讓 Web 伺服器無法為識別碼擷取快取索引鍵。  如果發生這種情況，便會將例外狀況擲回用戶端。  使用可設定狀態之安全性內容權杖 \(SCT\) 的安全工作階段可以存留已回收的 Web 伺服器。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]在安全工作階段中使用可設定狀態之 SCT 的詳細資訊，請參閱 [HOW TO：為安全工作階段建立安全性內容權杖](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)。  
  
### 使用其中一個系統提供的繫結來指定服務使用安全工作階段  
  
-   請將服務設定為使用支援訊息安全性之系統提供的繫結。  
  
     利用 [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 繫結的例外狀況，當系統提供的繫結設定為使用訊息安全性時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會自動使用安全工作階段。  下表列出了支援訊息安全性之系統提供的繫結，以及訊息安全性是否為預設的安全性機制。  
  
    |系統提供的繫結|組態項目|訊息安全性預設為開啟|  
    |-------------|----------|----------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|否|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|是|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|是|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|是|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|否|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|否|  
  
     下列程式碼範例是使用組態來指定名為 `wsHttpBinding_Calculator` 的繫結，它使用 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、訊息安全性和安全工作階段。  
  
    ```  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     下列程式碼範例會指定 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、訊息安全性和安全工作階段是用於保護 `secureCalculator` 服務的安全。  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  將 `establishSecurityContext` 屬性設定為 `false` 以關閉 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 的安全工作階段。  對於其他系統提供的繫結，安全工作階段只能藉由建立自訂繫結來關閉。  
  
### 使用自訂繫結來指定服務使用安全工作階段  
  
-   請建立自訂繫結，指定 SOAP 訊息受到安全工作階段的保護。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 建立自訂繫結的詳細資訊，請參閱 [HOW TO：自訂系統提供的繫結](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)。  
  
     下列程式碼範例會使用組態來指定使用安全工作階段傳送訊息的自訂繫結。  
  
    ```  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     下列程式碼範例建立了一個會使用 <xref:System.ServiceModel.Configuration.AuthenticationMode> 驗證模式來啟動載入安全工作階段的自訂繫結。  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## 請參閱  
 [WCF 繫結概觀](../../../../docs/framework/wcf/bindings-overview.md)