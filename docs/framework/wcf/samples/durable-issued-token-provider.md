---
title: 永久性發行權杖提供者
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: b7f204fcb2c1b72a73e091ecf37c2921f7575516
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650077"
---
# <a name="durable-issued-token-provider"></a>永久性發行權杖提供者
這個範例示範如何實作自訂用戶端發行的權杖提供者。  
  
## <a name="discussion"></a>討論  
 Windows Communication Foundation (WCF) 中的權杖提供者用來提供認證給安全性基礎結構。 一般而言，權杖提供者會檢查目標並發行適當的認證，讓安全性基礎結構能夠保護訊息的安全。 WCF 隨附[!INCLUDE[infocard](../../../../includes/infocard-md.md)]權杖提供者。 自訂權杖提供者適用於下列情況：  
  
- 如果您有內建權杖提供者無法使用的認證存放區。  
  
- 如果您想要提供您自己自訂的機制，來轉換認證從使用者提供詳細資訊，以當 WCF 用戶端會使用認證時。  
  
- 如果您要建置自訂權杖。  
  
 這個範例示範如何建置自訂權杖提供者，以便快取安全性權杖服務 (STS) 發行的權杖。  
  
 簡而言之，這個範例示範下面的情形：  
  
- 如何使用自訂權杖提供者設定用戶端。  
  
- 如何發行的權杖可以快取，並提供給 WCF 用戶端。  
  
- 用戶端如何使用伺服器的 X.509 憑證來驗證伺服器。  
  
 這個範例是由用戶端主控台程式 (Client.exe)、安全性權杖服務主控台程式 (Securitytokenservice.exe) 和服務主控台程式 (Service.exe) 所組成。 服務會實作定義要求-回覆通訊模式的合約。 合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。 用戶端會從安全性權杖服務 (STS) 取得安全性權杖，並對指定的數學運算作業提出同步要求，服務則會以結果回覆。 您可以在主控台視窗中看到用戶端活動。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此範例會公開 ICalculator 合約使用[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。 在下列程式碼中，將示範用戶端上的這個繫結組態。  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows" 
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 在 `security` 的 `wsFederationHttpBinding` 項目上，`mode` 值會設定應該使用的安全性模式。 本範例中會使用訊息安全性，因此 `message` 的 `wsFederationHttpBinding` 項目是在 `security` element of `wsFederationHttpBinding` 中指定的。 `issuer` 之 `wsFederationHttpBinding` 項目內 `message` 的 `wsFederationHttpBinding` 項目會指定將安全性權杖發行給用戶端之安全性權杖服務的位址與繫結，讓用戶端可以驗證至計算機服務。  
  
 在下列程式碼中，將示範服務上的這個繫結組態。  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser" 
                                    storeName="TrustedPeople" 
                                    x509FindType="FindBySubjectDistinguishedName" 
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 在 `security` 的 `wsFederationHttpBinding` 項目上，`mode` 值會設定應該使用的安全性模式。 本範例中會使用訊息安全性，因此 `message` 的 `wsFederationHttpBinding` 項目是在 `security` element of `wsFederationHttpBinding` 中指定的。 `issuerMetadata` 之 `wsFederationHttpBinding` 項目內 `message` 的 `wsFederationHttpBinding` 項目會指定端點的位址與身分識別，這個端點可用於擷取安全性權杖服務的中繼資料。  
  
 服務的行為如下列程式碼中所示。  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine" 
              storeName="TrustedPeople" 
              x509FindType="FindBySubjectDistinguishedName" 
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine" 
                        storeName="My" 
                        x509FindType="FindBySubjectDistinguishedName" 
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 `issuedTokenAuthentication` 項目內的 `serviceCredentials` 項目允許服務在權杖上指定條件約束，而此權杖是服務允許用戶端於驗證期間提出的權杖。 這個組態會指定服務接受主體名稱為 CN=STS 之憑證所簽署的權杖。  
  
 安全性權杖服務會使用標準 wsHttpBinding 來公開單一端點。 「安全性權杖服務」會對用戶端要求權杖做出回應，假設用戶端驗證是使用 Windows 帳戶，會再發行包含用戶端之使用者名稱的權杖，當做發行之權杖中的宣告。 在建立權杖的過程中，「安全性權杖服務」會使用與 CN=STS 憑證關聯的私密金鑰來簽署權杖。 此外，它還會建立對稱金鑰，並使用與 CN=localhost 憑證關聯的公開金鑰進行加密。 在將權杖傳回至用戶端時，「安全性權杖服務」也會傳回對稱金鑰。 用戶端會向計算機服務出示發行權杖，然後使用對稱金鑰簽署訊息來證明它知道這把金鑰。  
  
## <a name="custom-client-credentials-and-token-provider"></a>自訂用戶端認證和權杖提供者  
 下列步驟示範如何開發自訂權杖提供者快取發行的權杖，並將它與 WCF 整合： 安全性。  
  
#### <a name="to-develop-a-custom-token-provider"></a>若要開發自訂權杖提供者  
  
1. 撰寫自訂權杖提供者。  
  
     範例會實作自訂權杖提供者，以傳回擷取自快取的安全性權杖。  
  
     為了執行這個工作，自訂權杖提供者會衍生 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 類別並覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> 方法。 這個方法會嘗試從快取中取得權杖，如果快取中找不到權杖，就從基礎提供者擷取權杖，然後再快取該權杖。 在這兩種情況下，方法都會傳回 `SecurityToken`。  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. 撰寫自訂安全性權杖管理員。  
  
     此 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 會用來建立特定 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> (以 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 方法傳遞至該管理員) 的 `CreateSecurityTokenProvider`。 安全性權杖管理員也會用來建立權杖驗證器與權杖序列化程式，但是這些不在本範例的討論範圍。 在這個範例中，自訂安全性權杖管理員繼承自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別，並且會覆寫 `CreateSecurityTokenProvider` 方法，以便在傳遞的權杖需求表示要求發行的權杖時傳回自訂權杖提供者。  
  
    ```  
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        Else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. 撰寫自訂用戶端憑證。  
  
     用戶端認證類別會用來代表針對用戶端 Proxy 設定的認證，並且建立用來取得權杖驗證器、權杖提供者及權杖序列化程式的安全性權杖管理員。  
  
    ```  
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        Get  
        {  
          return this.cache;  
        }  
        Set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. 實作權杖快取。 範例實作會使用抽象基底類別，而指定之權杖快取的消費者則透過此基底類別與快取進行互動。  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     為了讓用戶端使用自訂用戶端認證，範例會刪除預設用戶端認證類別並提供新的用戶端認證類別。  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>執行範例  
 請參閱下列指示以執行範例。 當您執行範例時，安全性權杖的要求會顯示在「安全性權杖服務」主控台視窗中。 作業要求和回應會顯示在用戶端和服務主控台視窗中。 在任何主控台視窗中按下 ENTER 鍵，即可關閉應用程式。  
  
## <a name="the-setupcmd-batch-file"></a>Setup.cmd 批次檔  
 本範例中所包含的 Setup.cmd 批次檔可讓您使用相關的憑證設定伺服器和安全性權杖服務，以執行自我裝載應用程式。 批次檔會在 CurrentUser/TrustedPeople 憑證存放區中建立兩份憑證。 第一份憑證的主體名稱為 CN=STS，而且由「安全性權杖服務」用來簽署發行給用戶端的安全性權杖。 第二份憑證的主體名稱為 CN=localhost，而且由「安全性權杖服務」用於加密服務可以解密的密碼。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 執行 Setup.cmd 檔以建立所需的憑證。  
  
2. 若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。 確認已建置方案中的所有專案 (Shared、RSTRSTR、Service、SecurityTokenService 和 Client)。  
  
3. 確定 Service.exe 和 SecurityTokenService.exe 都以系統管理員權限執行中。  
  
4. 執行 Client.exe。  
  
#### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
1. 當您完成執行範例後，請執行範例資料夾中的 Cleanup.cmd。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
