---
title: "WS 2007 聯合 HTTP 繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# WS 2007 聯合 HTTP 繫結
這個範例會示範使用 <xref:System.ServiceModel.WS2007FederationHttpBinding>，這是能夠用來建置支援 WS\-Trust 規格 1.3 版之聯合案例的標準繫結。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例是由主控台用戶端程式 \(Client.exe\)、主控台安全性權杖服務程式 \(Securitytokenservice.exe\) 和主控台服務程式 \(Service.exe\) 所組成。服務會實作定義要求\/回覆通訊模式的合約。合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 \(`Add`、`Subtract`、`Multiply` 和 `Divide`\)。用戶端自安全性權杖服務 \(STS\) 取得安全性權杆，並對指定的數學運算提出同步要求。服務則以結果回覆。您可以在主控台視窗中看到用戶端活動。  
  
 這個範例會使用 `ws2007FederationHttpBinding` 項目，讓 `ICalculator` 合約可供使用。在下列程式碼中，將示範用戶端上的這個繫結組態。  
  
```  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Endpoint address and binding for Security Token Service -->  
          <issuer address ="http://localhost:8000/sts/windows"   
                  binding ="ws2007HttpBinding" />                
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
  
```  
  
 在 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) 上，`security` 值會指定必須使用的安全性模式。這個範例中所使用的是 `message` 安全性，因此會在 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)中指定 [\<訊息\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)。在 [\<訊息\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)中的 [\<issuer\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) 項目會指定 STS 的位址與繫結，此 STS 會將安全性權杖發出至用戶端，使用戶端可以向 `ICalculator` 服務進行驗證。  
  
 在下列程式碼中，將示範服務上的這個繫結組態。  
  
```  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Metadata address for Security Token Service -->  
          <issuerMetadata address ="http://localhost:8000/sts/mex" >  
            <identity>  
              <certificateReference storeLocation ="CurrentUser"   
                                    storeName="TrustedPeople"   
                                    x509FindType ="FindBySubjectDistinguishedName"   
                                    findValue ="CN=STS" />  
            </identity>  
          </issuerMetadata>  
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
  
```  
  
 在 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) 上，`security` 值會指定必須使用的安全性模式。這個範例中所使用的是 `message` 安全性，因此會在 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)中指定 [\<訊息\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)。在 [\<訊息\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)內之 `ws2007FederationHttpBinding` 的 [\<issuerMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) 項目會指定端點的位址與身分識別，而該端點可用於擷取 STS 的中繼資料。  
  
 服務的行為如下列程式碼中所示。  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name ="ServiceBehaviour" >  
      <serviceDebug includeExceptionDetailInFaults ="true"/>  
      <serviceMetadata httpGetEnabled ="true"/>  
      <serviceCredentials>  
        <issuedTokenAuthentication>  
          <knownCertificates>  
            <add storeLocation ="LocalMachine"  
                 storeName="TrustedPeople"  
                 x509FindType="FindBySubjectDistinguishedName"  
                 findValue="CN=STS" />  
          </knownCertificates>  
        </issuedTokenAuthentication>  
        <serviceCertificate storeLocation ="LocalMachine"  
                            storeName ="My"  
                            x509FindType ="FindBySubjectDistinguishedName"  
                            findValue ="CN=localhost"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
 [\<issuedTokenAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)\> 允許服務在其允許於驗證期間提出之用戶端的權杖上指定條件約束 \(Constraint\)。這個組態會指定服務接受主體名稱為 CN\=STS 之憑證所簽署的權杖。  
  
 STS 會使用標準 <xref:System.ServiceModel.WS2007HttpBinding>，讓單一端點可供使用。服務會回應用戶端對權杖的要求。如果用戶端是以 Windows 帳戶進行驗證，服務就會發出包含用戶端之使用者名稱做為宣告的權杖。在建立權杖期間，STS 會使用與 CN\=STS 憑證關聯的私密金鑰來簽署該權杖。此外，它還會建立對稱金鑰，並使用與 CN\=localhost 憑證關聯的公開金鑰進行加密。在將權杖傳回至用戶端時，STS 也會傳回對稱金鑰。用戶端向 `ICalculator` 服務出示發行的權杖，然後使用對稱金鑰簽署訊息來證明它知道這把金鑰。  
  
 當您執行範例時，安全性權杖的要求會顯示在 STS 主控台視窗中。作業的要求和回應會顯示在用戶端和服務主控台視窗中。在任何主控台視窗中按下 ENTER 鍵，即可關閉應用程式。  
  
 `Add(100,15.99) = 115.99`  
  
 `Subtract(145,76.54) = 68.46`  
  
 `Multiply(9,81.25) = 731.25`  
  
 `Divide(22,7) = 3.14285714285714`  
  
 `Press <ENTER> to terminate client.`  
  
 這個範例中包含的 Setup.bat 檔可讓您使用相關的憑證設定伺服器與 STS，以執行自我裝載應用程式。此批次檔會在 LocalMachine\/TrustedPeople 憑證存放區中建立兩份憑證。第一份憑證的主體名稱為 CN\=STS，而且會由 STS 用來簽署發給用戶端的安全性權杖。第二份憑證的主體名稱為 CN\=localhost，而且會由 STS 用於以服務可解密的方式來加密金鑰。  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  使用系統管理員權限來開啟 Visual Studio 命令提示字元，然後執行 Setup.bat 檔案，以便建立必要的憑證。  
  
 這個批次檔會使用隨 Windows SDK 發佈的 Certmgr.exe 和 Makecert.exe。但是，您必須從 Visual Studio 命令提示字元中執行 Setup.bat，以便讓這段指令碼尋找這些工具。  
  
1.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
2.  若要在單一或跨電腦的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。如果要使用 [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]，您就必須使用更高的權限執行 Service.exe、Client.exe 和 SecurityTokenService.exe \(用滑鼠右鍵按一下這些檔案，然後按一下 \[**以系統管理員身分執行**\]\)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## 請參閱