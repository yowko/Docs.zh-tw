---
title: 永久性發行權杖提供者
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 7def23a00e42e134d8c0b9bd911710917681ad31
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504587"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="de4df-102">永久性發行權杖提供者</span><span class="sxs-lookup"><span data-stu-id="de4df-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="de4df-103">這個範例示範如何實作自訂用戶端發行的權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="de4df-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="de4df-104">討論</span><span class="sxs-lookup"><span data-stu-id="de4df-104">Discussion</span></span>  
 <span data-ttu-id="de4df-105">Windows Communication Foundation (WCF) 中的權杖提供者用來提供認證給安全性基礎結構。</span><span class="sxs-lookup"><span data-stu-id="de4df-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="de4df-106">一般而言，權杖提供者會檢查目標並發行適當的認證，讓安全性基礎結構能夠保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="de4df-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="de4df-107">WCF 隨附[!INCLUDE[infocard](../../../../includes/infocard-md.md)]權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="de4df-107">WCF ships with a [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="de4df-108">自訂權杖提供者適用於下列情況：</span><span class="sxs-lookup"><span data-stu-id="de4df-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="de4df-109">如果您有內建權杖提供者無法使用的認證存放區。</span><span class="sxs-lookup"><span data-stu-id="de4df-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
-   <span data-ttu-id="de4df-110">如果您想要提供您自己自訂的機制，來轉換認證從使用者提供詳細資訊，以當 WCF 用戶端會使用認證時。</span><span class="sxs-lookup"><span data-stu-id="de4df-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
-   <span data-ttu-id="de4df-111">如果您要建置自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="de4df-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="de4df-112">這個範例示範如何建置自訂權杖提供者，以便快取安全性權杖服務 (STS) 發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="de4df-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="de4df-113">簡而言之，這個範例示範下面的情形：</span><span class="sxs-lookup"><span data-stu-id="de4df-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="de4df-114">如何使用自訂權杖提供者設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="de4df-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="de4df-115">如何發行的權杖可以快取，並提供給 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="de4df-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
-   <span data-ttu-id="de4df-116">用戶端如何使用伺服器的 X.509 憑證來驗證伺服器。</span><span class="sxs-lookup"><span data-stu-id="de4df-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="de4df-117">這個範例是由用戶端主控台程式 (Client.exe)、安全性權杖服務主控台程式 (Securitytokenservice.exe) 和服務主控台程式 (Service.exe) 所組成。</span><span class="sxs-lookup"><span data-stu-id="de4df-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="de4df-118">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="de4df-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="de4df-119">合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。</span><span class="sxs-lookup"><span data-stu-id="de4df-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="de4df-120">用戶端會從安全性權杖服務 (STS) 取得安全性權杖，並對指定的數學運算作業提出同步要求，服務則會以結果回覆。</span><span class="sxs-lookup"><span data-stu-id="de4df-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="de4df-121">您可以在主控台視窗中看到用戶端活動。</span><span class="sxs-lookup"><span data-stu-id="de4df-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de4df-122">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="de4df-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="de4df-123">此範例會公開 ICalculator 合約使用[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="de4df-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="de4df-124">在下列程式碼中，將示範用戶端上的這個繫結組態。</span><span class="sxs-lookup"><span data-stu-id="de4df-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="de4df-125">在 `security` 的 `wsFederationHttpBinding` 項目上，`mode` 值會設定應該使用的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="de4df-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="de4df-126">本範例中會使用訊息安全性，因此 `message` 的 `wsFederationHttpBinding` 項目是在 `security` element of `wsFederationHttpBinding` 中指定的。</span><span class="sxs-lookup"><span data-stu-id="de4df-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="de4df-127">`issuer` 之 `wsFederationHttpBinding` 項目內 `message` 的 `wsFederationHttpBinding` 項目會指定將安全性權杖發行給用戶端之安全性權杖服務的位址與繫結，讓用戶端可以驗證至計算機服務。</span><span class="sxs-lookup"><span data-stu-id="de4df-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="de4df-128">在下列程式碼中，將示範服務上的這個繫結組態。</span><span class="sxs-lookup"><span data-stu-id="de4df-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="de4df-129">在 `security` 的 `wsFederationHttpBinding` 項目上，`mode` 值會設定應該使用的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="de4df-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="de4df-130">本範例中會使用訊息安全性，因此 `message` 的 `wsFederationHttpBinding` 項目是在 `security` element of `wsFederationHttpBinding` 中指定的。</span><span class="sxs-lookup"><span data-stu-id="de4df-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="de4df-131">`issuerMetadata` 之 `wsFederationHttpBinding` 項目內 `message` 的 `wsFederationHttpBinding` 項目會指定端點的位址與身分識別，這個端點可用於擷取安全性權杖服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="de4df-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="de4df-132">服務的行為如下列程式碼中所示。</span><span class="sxs-lookup"><span data-stu-id="de4df-132">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="de4df-133">`issuedTokenAuthentication` 項目內的 `serviceCredentials` 項目允許服務在權杖上指定條件約束，而此權杖是服務允許用戶端於驗證期間提出的權杖。</span><span class="sxs-lookup"><span data-stu-id="de4df-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="de4df-134">這個組態會指定服務接受主體名稱為 CN=STS 之憑證所簽署的權杖。</span><span class="sxs-lookup"><span data-stu-id="de4df-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="de4df-135">安全性權杖服務會使用標準 wsHttpBinding 來公開單一端點。</span><span class="sxs-lookup"><span data-stu-id="de4df-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="de4df-136">「安全性權杖服務」會對用戶端要求權杖做出回應，假設用戶端驗證是使用 Windows 帳戶，會再發行包含用戶端之使用者名稱的權杖，當做發行之權杖中的宣告。</span><span class="sxs-lookup"><span data-stu-id="de4df-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="de4df-137">在建立權杖的過程中，「安全性權杖服務」會使用與 CN=STS 憑證關聯的私密金鑰來簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="de4df-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="de4df-138">此外，它還會建立對稱金鑰，並使用與 CN=localhost 憑證關聯的公開金鑰進行加密。</span><span class="sxs-lookup"><span data-stu-id="de4df-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="de4df-139">在將權杖傳回至用戶端時，「安全性權杖服務」也會傳回對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="de4df-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="de4df-140">用戶端會向計算機服務出示發行權杖，然後使用對稱金鑰簽署訊息來證明它知道這把金鑰。</span><span class="sxs-lookup"><span data-stu-id="de4df-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="de4df-141">自訂用戶端認證和權杖提供者</span><span class="sxs-lookup"><span data-stu-id="de4df-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="de4df-142">下列步驟示範如何開發自訂權杖提供者快取發行的權杖，並將它與 WCF 整合： 安全性。</span><span class="sxs-lookup"><span data-stu-id="de4df-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
#### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="de4df-143">若要開發自訂權杖提供者</span><span class="sxs-lookup"><span data-stu-id="de4df-143">To develop a custom token provider</span></span>  
  
1.  <span data-ttu-id="de4df-144">撰寫自訂權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="de4df-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="de4df-145">範例會實作自訂權杖提供者，以傳回擷取自快取的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="de4df-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="de4df-146">為了執行這個工作，自訂權杖提供者會衍生 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 類別並覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="de4df-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="de4df-147">這個方法會嘗試從快取中取得權杖，如果快取中找不到權杖，就從基礎提供者擷取權杖，然後再快取該權杖。</span><span class="sxs-lookup"><span data-stu-id="de4df-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="de4df-148">在這兩種情況下，方法都會傳回 `SecurityToken`。</span><span class="sxs-lookup"><span data-stu-id="de4df-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
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
  
2.  <span data-ttu-id="de4df-149">撰寫自訂安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="de4df-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="de4df-150">此 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 會用來建立特定 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> (以 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 方法傳遞至該管理員) 的 `CreateSecurityTokenProvider`。</span><span class="sxs-lookup"><span data-stu-id="de4df-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="de4df-151">安全性權杖管理員也會用來建立權杖驗證器與權杖序列化程式，但是這些不在本範例的討論範圍。</span><span class="sxs-lookup"><span data-stu-id="de4df-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="de4df-152">在這個範例中，自訂安全性權杖管理員繼承自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別，並且會覆寫 `CreateSecurityTokenProvider` 方法，以便在傳遞的權杖需求表示要求發行的權杖時傳回自訂權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="de4df-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
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
  
3.  <span data-ttu-id="de4df-153">撰寫自訂用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="de4df-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="de4df-154">用戶端認證類別會用來代表針對用戶端 Proxy 設定的認證，並且建立用來取得權杖驗證器、權杖提供者及權杖序列化程式的安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="de4df-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
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
  
4.  <span data-ttu-id="de4df-155">實作權杖快取。</span><span class="sxs-lookup"><span data-stu-id="de4df-155">Implement the token cache.</span></span> <span data-ttu-id="de4df-156">範例實作會使用抽象基底類別，而指定之權杖快取的消費者則透過此基底類別與快取進行互動。</span><span class="sxs-lookup"><span data-stu-id="de4df-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="de4df-157">為了讓用戶端使用自訂用戶端認證，範例會刪除預設用戶端認證類別並提供新的用戶端認證類別。</span><span class="sxs-lookup"><span data-stu-id="de4df-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="de4df-158">執行範例</span><span class="sxs-lookup"><span data-stu-id="de4df-158">Running the sample</span></span>  
 <span data-ttu-id="de4df-159">請參閱下列指示以執行範例。</span><span class="sxs-lookup"><span data-stu-id="de4df-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="de4df-160">當您執行範例時，安全性權杖的要求會顯示在「安全性權杖服務」主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="de4df-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="de4df-161">作業要求和回應會顯示在用戶端和服務主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="de4df-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="de4df-162">在任何主控台視窗中按下 ENTER 鍵，即可關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="de4df-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="de4df-163">Setup.cmd 批次檔</span><span class="sxs-lookup"><span data-stu-id="de4df-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="de4df-164">本範例中所包含的 Setup.cmd 批次檔可讓您使用相關的憑證設定伺服器和安全性權杖服務，以執行自我裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="de4df-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="de4df-165">批次檔會在 CurrentUser/TrustedPeople 憑證存放區中建立兩份憑證。</span><span class="sxs-lookup"><span data-stu-id="de4df-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="de4df-166">第一份憑證的主體名稱為 CN=STS，而且由「安全性權杖服務」用來簽署發行給用戶端的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="de4df-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="de4df-167">第二份憑證的主體名稱為 CN=localhost，而且由「安全性權杖服務」用於加密服務可以解密的密碼。</span><span class="sxs-lookup"><span data-stu-id="de4df-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="de4df-168">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="de4df-168">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="de4df-169">執行 Setup.cmd 檔以建立所需的憑證。</span><span class="sxs-lookup"><span data-stu-id="de4df-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2.  <span data-ttu-id="de4df-170">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="de4df-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="de4df-171">確認已建置方案中的所有專案 (Shared、RSTRSTR、Service、SecurityTokenService 和 Client)。</span><span class="sxs-lookup"><span data-stu-id="de4df-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3.  <span data-ttu-id="de4df-172">確定 Service.exe 和 SecurityTokenService.exe 都以系統管理員權限執行中。</span><span class="sxs-lookup"><span data-stu-id="de4df-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="de4df-173">執行 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="de4df-173">Run Client.exe.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="de4df-174">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="de4df-174">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="de4df-175">當您完成執行範例後，請執行範例資料夾中的 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="de4df-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="de4df-176">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="de4df-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="de4df-177">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="de4df-177">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="de4df-178">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="de4df-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="de4df-179">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="de4df-179">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## <a name="see-also"></a><span data-ttu-id="de4df-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de4df-180">See Also</span></span>
