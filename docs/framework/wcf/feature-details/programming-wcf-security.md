---
title: WCF 安全性程式設計
description: 瞭解如何建立安全的 WCF 應用程式，包括驗證、機密性和完整性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 4ffbf6a05abd3ed9ebcea4b2e85f0dc305a4f2db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244765"
---
# <a name="programming-wcf-security"></a>WCF 安全性程式設計

本主題說明用來建立安全 Windows Communication Foundation (WCF) 應用程式的基本程式設計工作。 本主題僅涵蓋驗證、機密性和完整性，統稱為 *傳輸安全性*。 本主題未涵蓋授權 (控制資源或服務存取) ;如需授權的詳細資訊，請參閱 [授權](authorization-in-wcf.md)。  
  
> [!NOTE]
> 如需安全性概念的重要簡介（特別是關於 WCF），請參閱 MSDN 上的 [適用于 Web 服務增強功能的案例、模式](/previous-versions/msp-n-p/ff648183(v=pandp.10))和實務教學課程組合 (WSE) 3.0。  
  
 WCF 安全性的程式設計是以三個步驟為基礎，設定下列各項：安全性模式、用戶端認證類型，以及認證值。 您可以透過程式碼或組態執行這些步驟。  
  
## <a name="setting-the-security-mode"></a>設定安全性模式  

 以下說明在 WCF 中使用安全性模式進行程式設計的一般步驟：  
  
1. 針對應用程式需求選取一項適合的預先定義繫結程序。 如需系結選項的清單，請參閱 [系統提供](../system-provided-bindings.md)的系結。 根據預設，幾乎所有的繫結都會啟用安全性。 其中一個例外狀況是 <xref:System.ServiceModel.BasicHttpBinding> 使用 configuration、)  (的類別 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) 。  
  
     您選取的繫結將決定傳輸方式。 例如，<xref:System.ServiceModel.WSHttpBinding> 會使用 HTTP 做為傳輸方式；而 <xref:System.ServiceModel.NetTcpBinding> 則使用 TCP。  
  
2. 選取其中一項安全性模式來進行繫結。 請注意，您選取的繫結會決定可用的模式選項有哪些。 例如，<xref:System.ServiceModel.WSDualHttpBinding> 不允許使用傳輸安全性 (未包含在選項中)。 同樣地，<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 和 <xref:System.ServiceModel.NetNamedPipeBinding> 也都不允許使用訊息安全性。  
  
     您有下列三個選擇：  
  
    1. `Transport`  
  
         傳輸安全性將視您選取之繫結所使用的機制而定。 例如，假使您使用 `WSHttpBinding`，則安全性機制為安全通訊端層 (SSL) (同時也是 HTTPS 通訊協定的機制)。 一般來說，傳輸安全性的主要優點在於，不管您使用哪種傳輸機制，都能提供良好的輸送量。 但是，它有兩項限制：首先就是傳輸機制會指出用來驗證使用者的認證類型。 只有當服務需要與其他要求不同認證類型的服務交互操作時，這個限制才會成為缺點。 第二個限制是，由於訊息層級並未套用安全性，所以會以躍點方式 (而不是以端對端方式) 來實作安全性。 只有當用戶端與服務之間的訊息路徑包含媒介時，第二個限制才會成為問題。 如需使用何種傳輸的詳細資訊，請參閱 [選擇傳輸](choosing-a-transport.md)。 如需有關使用傳輸安全性的詳細資訊，請參閱 [傳輸安全性概觀](transport-security-overview.md)。  
  
    2. `Message`  
  
         訊息安全性表示每則訊息都包含保護訊息安全的必要標頭與資料。 由於標頭的組成份子各有不同，因此您可以加入任何數量的認證。 如果您正與其他需要特定認證類型 (但無法適用傳輸機制) 的服務進行交互操作，或是如果訊息必須與一個以上的服務搭配使用，而其中每個服務需要不同的認證類型時，這項特性就會變成一個要件。  
  
         如需詳細資訊，請參閱 [訊息安全性](message-security-in-wcf.md)。  
  
    3. `TransportWithMessageCredential`  
  
         這項選擇使用傳輸層來保護訊息傳輸的安全，而每則訊息則包含其他服務所需的豐富認證。 這項選擇會將傳輸安全性的效能優點，與訊息安全性的豐富認證優勢加以結合。 您可透過下列繫結來獲得這項優勢：<xref:System.ServiceModel.BasicHttpBinding>、<xref:System.ServiceModel.WSFederationHttpBinding>、<xref:System.ServiceModel.NetPeerTcpBinding> 和 <xref:System.ServiceModel.WSHttpBinding>。  
  
3. 如果您決定在 HTTP 上使用傳輸安全性 (亦即，HTTPS)，必須同時使用 SSL 憑證來設定主機，並啟用連接埠上的 SSL。 如需詳細資訊，請參閱 [HTTP 傳輸安全性](http-transport-security.md)。  
  
4. 如果您正在使用 <xref:System.ServiceModel.WSHttpBinding> 而且不需要建立安全工作階段，請將 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> 屬性設為 `false`。  
  
     當用戶端與服務透過對稱金鑰來建立通道時，就會產生安全工作階段 (用戶端與伺服器都會在對話期間全程使用相同的金鑰，直到對話結束為止)。  
  
## <a name="setting-the-client-credential-type"></a>設定用戶端認證類型  

 視需要選取用戶端認證類型。 如需詳細資訊，請參閱 [選取認證類型](selecting-a-credential-type.md)。 下列為可用的用戶端認證類型：  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 視模式的設定方式而定，您必須設定認證類型。 例如，如果您選取了 `wsHttpBinding`，並將模式設為 [訊息]，則也可以將 Message 項目的 `clientCredentialType` 屬性設為下列其中一個值：`None`、`Windows`、`UserName`、`Certificate` 和 `IssuedToken`，如下列組態範例所示。  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 或在程式碼中：  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>設定服務認證值  

 一旦您選取了用戶端認證類型，就必須設定實際認證以供服務與用戶端使用。 在服務上，認證需透過 <xref:System.ServiceModel.Description.ServiceCredentials> 類別來加以設定，並由 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 類別的 <xref:System.ServiceModel.ServiceHostBase> 屬性傳回。 使用中的繫結意指服務認證類型、選擇的安全性模式，以及用戶端認證類型。 下列程式碼將為服務認證設定憑證。  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>設定用戶端認證值  

 在用戶端上，用戶端認證值是使用 <xref:System.ServiceModel.Description.ClientCredentials> 類別進行設定，並由 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 類別的 <xref:System.ServiceModel.ClientBase%601> 屬性傳回。 下列程式碼將透過 TCP 通訊協定在用戶端上將憑證設為認證。  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [基本 WCF 程式設計](../basic-wcf-programming.md)
- [常見的安全性案例](common-security-scenarios.md)
