---
title: WS 2007 聯合 HTTP 繫結
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: ad56665b5b6648fb93a9f31f18167a964b4cba92
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834661"
---
# <a name="ws-2007-federation-http-binding"></a>WS 2007 聯合 HTTP 繫結

這個範例會示範使用 <xref:System.ServiceModel.WS2007FederationHttpBinding>，這是能夠用來建置支援 WS-Trust 規格 1.3 版之聯合案例的標準繫結。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。

此範例包含以主控台為基礎的用戶端程式（*setup.exe*）、以主控台為基礎的 Security Token Service 程式（使用 *.exe*），以及以主控台為基礎的服務程式（*setup.exe*）。 服務會實作定義要求/回覆通訊模式的合約。 合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 (`Add`、`Subtract`、`Multiply` 和 `Divide`)。 用戶端自安全性權杖服務 (STS) 取得安全性權杆，並對指定的數學運算提出同步要求。 服務則以結果回覆。 您可以在主控台視窗中看到用戶端活動。

這個範例會使用 `ICalculator` 項目，讓 `ws2007FederationHttpBinding` 合約可供使用。 此系結在用戶端上的設定會顯示在下列程式碼中：

```xml
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

在[\<security >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)上，`security` 值會指定應該使用的安全性模式。 在此範例中，會使用 `message` 安全性，這也是為什麼在[@no__t 4security >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)內指定[@no__t 2message >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)的原因。 [@No__t 3message >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)內的[@no__t 1issuer >](../../configure-apps/file-schema/wcf/issuer.md)元素，會指定發行安全性權杖給用戶端的 STS 位址和系結，讓用戶端可以向 `ICalculator` 服務驗證。
  
在服務上設定此系結的方式如下列程式碼所示：

```xml
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

在[\<security >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)上，`security` 值會指定應該使用的安全性模式。 在此範例中，會使用 `message` 安全性，這也是為什麼在[@no__t 4security >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)內指定[@no__t 2message >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)的原因。 [@No__t 4message >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)內 `ws2007FederationHttpBinding` 的[@no__t 1issuerMetadata >](../../configure-apps/file-schema/wcf/issuermetadata.md)元素，會指定可用來抓取 STS 中繼資料的端點位址和識別。

服務的行為如下列程式碼所示：

```xml
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
  
[@No__t 1issuedTokenAuthentication >](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> 可讓服務在驗證期間允許用戶端轉譯的權杖上指定條件約束。 這個組態會指定服務接受主體名稱為 CN=STS 之憑證所簽署的權杖。

STS 會使用標準 <xref:System.ServiceModel.WS2007HttpBinding>，讓單一端點可供使用。 服務會回應用戶端對權杖的要求。 如果用戶端是以 Windows 帳戶進行驗證，服務就會發出包含用戶端之使用者名稱做為宣告的權杖。 在建立權杖期間，STS 會使用與 CN=STS 憑證關聯的私密金鑰來簽署該權杖。 此外，它還會建立對稱金鑰，並使用與 CN=localhost 憑證關聯的公開金鑰進行加密。 在將權杖傳回至用戶端時，STS 也會傳回對稱金鑰。 用戶端向 `ICalculator` 服務出示發行的權杖，然後使用對稱金鑰簽署訊息來證明它知道這把金鑰。

當您執行範例時，安全性權杖的要求會顯示在 STS 主控台視窗中。 作業的要求和回應會顯示在用戶端和服務主控台視窗中。 在任何主控台視窗中按下 ENTER 鍵，即可關閉應用程式。

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

此範例中包含的*安裝程式 .bat*檔案可讓您使用相關的憑證來設定伺服器和 STS，以執行自我裝載應用程式。 此批次檔會在 LocalMachine/TrustedPeople 憑證存放區中建立兩份憑證。 第一份憑證的主體名稱為 CN=STS，而且會由 STS 用來簽署發給用戶端的安全性權杖。 第二份憑證的主體名稱為 CN=localhost，而且會由 STS 用於以服務可解密的方式來加密金鑰。

## <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。

2. 以系統管理員許可權開啟 Visual Studio 的開發人員命令提示字元，並執行安裝程式 .bat 檔案，以建立所需的憑證。

 此批次檔會使用*certmgr.msc*與 Windows SDK 散發的 Makecert。 不過，您必須從 Visual Studio 命令提示字元內執行*安裝程式 .bat* ，讓腳本能夠找到這些工具。

1. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。

2. 若要在單一或跨電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](running-the-samples.md)中的指示。 如果您使用 [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]，則必須以較高的許可權（以滑鼠右鍵按一下*檔案，然後*按一下 [以**系統管理員身分執行**]）來執行*setup.exe*、setup.exe 和 mstest.exe *。*

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續：
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄：
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
