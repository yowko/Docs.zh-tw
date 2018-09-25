---
title: HOW TO：設定安全性模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
author: BrucePerlerMS
ms.openlocfilehash: 32fd1ebede841488d1bfabd2f92bd3fb1ffb55e8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087339"
---
# <a name="how-to-set-the-security-mode"></a>HOW TO：設定安全性模式
Windows Communication Foundation (WCF) 安全性有三種常見的安全性模式，最預先定義繫結上找到： 傳輸、 訊息和 「 傳輸與訊息認證 」。 另外有兩種額外的模式適用於下列兩種繫結：<xref:System.ServiceModel.BasicHttpBinding> 上的「僅限傳輸-認證」以及 <xref:System.ServiceModel.NetMsmqBinding> 上的「兩者並存」模式。 然而，此主題將著重在三種常見的安全性模式：<xref:System.ServiceModel.SecurityMode.Transport>、<xref:System.ServiceModel.SecurityMode.Message> 與 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。  
  
 請注意，並非所有預先定義的繫結都支援這些模式。 本主題將使用 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.NetTcpBinding> 類別來設定模式，並示範如何以程式設計方式及透過組態來設定模式。  
  
 如需詳細資訊，請參閱 WCF 安全性，請參閱[安全性概觀](../../../docs/framework/wcf/feature-details/security-overview.md)， [Securing Services](../../../docs/framework/wcf/securing-services.md)，並[Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)。 如需有關傳輸模式與訊息的詳細資訊，請參閱[傳輸安全性](../../../docs/framework/wcf/feature-details/transport-security.md)並[訊息安全性](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)。  
  
### <a name="to-set-the-security-mode-in-code"></a>若要在程式碼中設定安全性模式  
  
1.  針對您正在使用的繫結類別建立執行個體。 如需預先定義繫結的清單，請參閱 < [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)。 下列範例會建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體。  
  
2.  針對 `Mode` 屬性傳回的物件，設定其 `Security` 屬性。  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     另外，如下列程式碼所示，設定訊息的模式。  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     或者，如下列程式碼所示，使用訊息認證來設定傳輸的模式。  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  您也可以如下列程式碼所示，在繫結的建構函式中設定模式。  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>設定 ClientCredentialType 屬性  
 將模式設為三個值中的其中一個值，可決定您設定 `ClientCredentialType` 屬性的方式。 例如，使用 <xref:System.ServiceModel.WSHttpBinding> 類別並將模式設為 `Transport` 時，代表您必須將 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 類別的 <xref:System.ServiceModel.HttpTransportSecurity> 屬性設為適當值。  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>若要設定傳輸模式的 ClientCredentialType 屬性  
  
1.  建立繫結的執行個體。  
  
2.  將 `Mode` 屬性設定為 `Transport`。  
  
3.  將 `ClientCredential` 屬性設定為適當值。 下列程式碼會將屬性設為 `Windows`。  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>若要設定訊息模式的 ClientCredentialType 屬性  
  
1.  建立繫結的執行個體。  
  
2.  將 `Mode` 屬性設定為 `Message`。  
  
3.  將 `ClientCredential` 屬性設定為適當值。 下列程式碼會將屬性設為 `Certificate`。  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>若要在組態中設定 Mode 與 ClientCredentialType 屬性  
  
1.  加入至適當的繫結項目[\<繫結 >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)組態檔的項目。 下列範例會將[ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。  
  
2.  新增`<binding>`項目並將其`name`屬性設為適當的值。  
  
3.  新增 `<security>` 項目，並將 `mode` 屬性設為 `Message`、`Transport` 或 `TransportWithMessageCredential`。  
  
4.  如果模式已設為 `Transport`，則新增 `<transport>` 項目並將 `clientCredential` 屬性設為適當值。  
  
     下列範例會將模式設為 "`Transport"`，然後將 `clientCredentialType` 項目的 `<transport>` 屬性設為 "`Windows"`。  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     另外，將 `security mode` 設為 "`Message"`，並在它後面加上 `<"message">` 項目。 這個範例會將 `clientCredentialType` 設為 "`Certificate"`。  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     特殊情況下會使用 <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> 值 (請參見下列說明)。  
  
### <a name="using-transportwithmessagecredential"></a>使用 TransportWithMessageCredential  
 當您將安全性模式設為 `TransportWithMessageCredential` 時，傳輸會決定用來提供傳輸層安全性的實際機制。 例如，HTTP 通訊協定會使用 Secure Sockets Layer (SSL) over HTTP (HTTPS)。 因此，會忽略對任何傳輸安全性物件 (例如 `ClientCredentialType`) 的 <xref:System.ServiceModel.HttpTransportSecurity> 屬性設定。  換句話說，您只能設定訊息安全性物件的 `ClientCredentialType` (對 `WSHttpBinding` 繫結來說，指的是 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> 物件)。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何： 使用傳輸安全性和訊息認證](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用 SSL 憑證設定連接埠](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [如何：使用傳輸安全性和訊息認證](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [傳輸安全性](../../../docs/framework/wcf/feature-details/transport-security.md)  
 [訊息安全性](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [安全性概觀](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [系統提供的繫結](../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)  
 [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)  
 [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
