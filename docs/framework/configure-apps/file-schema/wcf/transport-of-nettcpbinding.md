---
title: "&lt;netTcpBinding&gt; 的 &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# &lt;netTcpBinding&gt; 的 &lt;transport&gt;
定義以 [\<netTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)設定之端點的訊息層級安全性需求類型。  
  
## 語法  
  
```  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"  
             sslProtocols="Ssl3|Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|clientCredentialType|選擇項。  指定當使用傳輸安全性執行用戶端驗證時，要使用的認證類型。<br /><br /> -   預設值是 `Windows`。<br />-   此屬性的型別為 <xref:System.ServiceModel.TcpClientCredentialType>。|  
|protectionLevel|選擇項。  定義 TCP 傳輸層級的安全性。  簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。  加密會提供傳輸期間的資料層級隱私權。<br /><br /> 預設值是 `EncryptAndSign`。|  
|sslProtocols|SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。  預設值是 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。|  
|policyEnforcement|此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtectionPolicy> 的時間。<br /><br /> 1.  Never：絕不強制執行此原則 \(延伸保護已停用\)。<br />2.  WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。<br />3.  Always：一律強制執行此原則。  不支援延伸保護的用戶端將無法驗證。|  
  
## clientCredentialType 屬性  
  
|值|描述|  
|-------|--------|  
|無|用戶端為匿名。  這需要服務的憑證。|  
|Windows|使用 SP Negotiation \(Kerberos 交涉\) 指定用戶端的 Windows 驗證。|  
|憑證|用戶端會透過憑證來驗證。  這會使用 SSL Negotiation，並需要服務的憑證。|  
  
## protectionLevel 屬性  
  
|值|描述|  
|-------|--------|  
|無|無保護。|  
|Sign|訊息會經過簽署。|  
|EncryptAndSign|-   訊息會經過加密和簽署。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|指定 [\<netTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)的安全性功能。|  
  
## 備註  
 使用傳輸安全性來達成 SOAP 訊息的完整性與機密性，以及交互驗證。  如果在繫結上選取這個安全性模式，便會使用安全性傳輸設定通道堆疊，並以傳輸安全性 \(如 Windows Negotiate 或 SSL over TCP\) 保護 SOAP 訊息。  
  
## 請參閱  
 <xref:System.ServiceModel.TcpTransportSecurity>   
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.NetTcpTransportSecurityElement>   
 [確保服務與用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)