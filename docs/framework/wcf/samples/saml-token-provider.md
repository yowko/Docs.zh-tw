---
title: SAML 權杖提供者
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: e662d9b84bbc43178946fdadc8ddbec6f6b6e042
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771097"
---
# <a name="saml-token-provider"></a><span data-ttu-id="ce588-102">SAML 權杖提供者</span><span class="sxs-lookup"><span data-stu-id="ce588-102">SAML Token Provider</span></span>
<span data-ttu-id="ce588-103">這個範例會示範如何實作自訂的用戶端 SAML 權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="ce588-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="ce588-104">Windows Communication Foundation (WCF) 中的權杖提供者用來提供認證給安全性基礎結構。</span><span class="sxs-lookup"><span data-stu-id="ce588-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="ce588-105">一般而言，權杖提供者會檢查目標並發行適當的認證，讓安全性基礎結構能夠保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="ce588-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="ce588-106">WCF 隨附預設的 「 認證管理員權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="ce588-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="ce588-107">WCF 也隨附[!INCLUDE[infocard](../../../../includes/infocard-md.md)]權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="ce588-107">WCF also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="ce588-108">自訂權杖提供者適用於下列情況：</span><span class="sxs-lookup"><span data-stu-id="ce588-108">Custom token providers are useful in the following cases:</span></span>

-   <span data-ttu-id="ce588-109">如果您有這些權杖提供者無法使用的認證存放區。</span><span class="sxs-lookup"><span data-stu-id="ce588-109">If you have a credential store that these token providers cannot operate with.</span></span>

-   <span data-ttu-id="ce588-110">如果您想要提供您自己自訂的機制，來轉換認證從使用者提供詳細資訊，以 WCF 用戶端架構時使用的認證時。</span><span class="sxs-lookup"><span data-stu-id="ce588-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

-   <span data-ttu-id="ce588-111">如果您要建置自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="ce588-111">If you are building a custom token.</span></span>

 <span data-ttu-id="ce588-112">此範例示範如何建置自訂權杖提供者可從用於 WCF 用戶端架構外部取得的 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="ce588-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="ce588-113">簡而言之，這個範例示範下面的情形：</span><span class="sxs-lookup"><span data-stu-id="ce588-113">To summarize, this sample demonstrates the following:</span></span>

-   <span data-ttu-id="ce588-114">如何使用自訂權杖提供者設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="ce588-114">How a client can be configured with a custom token provider.</span></span>

-   <span data-ttu-id="ce588-115">如何將 SAML 權杖傳遞至自訂用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="ce588-115">How a SAML token can be passed to the custom client credentials.</span></span>

-   <span data-ttu-id="ce588-116">如何將 SAML 權杖提供給 WCF 用戶端架構。</span><span class="sxs-lookup"><span data-stu-id="ce588-116">How the SAML token is provided to the WCF client framework.</span></span>

-   <span data-ttu-id="ce588-117">用戶端如何使用伺服器的 X.509 憑證來驗證伺服器。</span><span class="sxs-lookup"><span data-stu-id="ce588-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="ce588-118">服務會公開兩個端點，以便與使用組態檔 App.config 定義的服務進行通訊。每個端點是由位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="ce588-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="ce588-119">繫結已設定成會使用訊息安全性的標準 `wsFederationHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="ce588-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="ce588-120">其中一個端點會預期用戶端經由使用對稱式證明金鑰的 SAML 權杖驗證，而另一個端點則預期用戶端經由使用非對稱式證明金鑰的 SAML 權杖驗證。</span><span class="sxs-lookup"><span data-stu-id="ce588-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="ce588-121">服務也會使用 `serviceCredentials` 行為來設定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="ce588-122">`serviceCredentials` 行為可以讓您設定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="ce588-123">服務憑證是由用戶端用來驗證服務並提供訊息保護。</span><span class="sxs-lookup"><span data-stu-id="ce588-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="ce588-124">下列組態會參考在安裝範例期間所安裝的 localhost 憑證，如本主題結尾處的安裝指示所述。</span><span class="sxs-lookup"><span data-stu-id="ce588-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="ce588-125">`serviceCredentials` 行為也會允許您設定受信任可簽署 SAML 權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="ce588-126">下列組態會參考在範例期間安裝的 'Alice' 憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="ce588-127">下列步驟示範如何開發自訂 SAML 權杖提供者，並將它與 WCF 整合： 安全性架構：</span><span class="sxs-lookup"><span data-stu-id="ce588-127">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1. <span data-ttu-id="ce588-128">撰寫自訂 SAML 權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="ce588-128">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="ce588-129">此範例會實作自訂 SAML 權杖提供者，此權杖提供者會根據建構階段所提供的 SAML 判斷提示傳回安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="ce588-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="ce588-130">為了執行這個工作，此自訂權杖提供者會衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 類別，並覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ce588-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="ce588-131">這個方法會建立並傳回新的 `SecurityToken`。</span><span class="sxs-lookup"><span data-stu-id="ce588-131">This method creates and returns a new `SecurityToken`.</span></span>

    ```
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. <span data-ttu-id="ce588-132">撰寫自訂安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="ce588-132">Write custom security token manager.</span></span>

     <span data-ttu-id="ce588-133"><xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別會用來建立特定 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 物件的 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>，而該提供者會透過 `CreateSecurityTokenProvider` 方法傳遞給該管理員。</span><span class="sxs-lookup"><span data-stu-id="ce588-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="ce588-134">安全性權杖管理員也會用來建立權杖驗證器與權杖序列化程式，但是這些不在本範例的討論範圍。</span><span class="sxs-lookup"><span data-stu-id="ce588-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="ce588-135">在這個範例中，自訂安全性權杖管理員繼承自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別，並且會覆寫 `CreateSecurityTokenProvider` 方法，以便在傳遞的權杖需求表示要求 SAML 權杖時傳回自訂 SAML 權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="ce588-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="ce588-136">如果用戶端認證類別 (請參閱步驟 3) 尚未指定判斷提示，安全性權杖管理員就會建立適當的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ce588-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

    ```
    public class SamlSecurityTokenManager :
     ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. <span data-ttu-id="ce588-137">撰寫自訂用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-137">Write a custom client credential.</span></span>

     <span data-ttu-id="ce588-138">用戶端認證類別會用來代表針對用戶端 Proxy 設定的認證，並且會建立用來取得權杖驗證器、權杖提供者以及權杖序列化程式的安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="ce588-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

    ```
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. <span data-ttu-id="ce588-139">將用戶端設定成使用自訂用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="ce588-139">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="ce588-140">此範例會刪除預設用戶端認證類別並提供新的用戶端認證類別，以便讓用戶端能夠使用自訂用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="ce588-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

    ```
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 <span data-ttu-id="ce588-141">服務端上會顯示與呼叫者關聯的宣告。</span><span class="sxs-lookup"><span data-stu-id="ce588-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="ce588-142">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="ce588-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ce588-143">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="ce588-143">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="ce588-144">設定批次檔</span><span class="sxs-lookup"><span data-stu-id="ce588-144">Setup Batch File</span></span>
 <span data-ttu-id="ce588-145">這個範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="ce588-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="ce588-146">這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="ce588-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="ce588-147">下面提供批次檔的各區段簡要概觀，讓將批次檔得以修改為在適當的組態下執行。</span><span class="sxs-lookup"><span data-stu-id="ce588-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

-   <span data-ttu-id="ce588-148">建立伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="ce588-148">Creating the server certificate:</span></span>

     <span data-ttu-id="ce588-149">下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="ce588-150">`%SERVER_NAME%` 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="ce588-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="ce588-151">您可以變更這個變數來指定自己的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="ce588-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="ce588-152">這個批次檔中的預設值為 localhost。</span><span class="sxs-lookup"><span data-stu-id="ce588-152">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="ce588-153">憑證會儲存在 LocalMachine 存放區位置下的 My (Personal) 存放區中。</span><span class="sxs-lookup"><span data-stu-id="ce588-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="ce588-154">將伺服器憑證安裝至用戶端的受信任憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="ce588-154">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="ce588-155">Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="ce588-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ce588-156">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ce588-157">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證的步驟。</span><span class="sxs-lookup"><span data-stu-id="ce588-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

-   <span data-ttu-id="ce588-158">建立簽發者憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-158">Creating the issuer certificate.</span></span>

     <span data-ttu-id="ce588-159">下列 Setup.bat 批次檔中的程式行會建立要使用的簽發者憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="ce588-160">`%USER_NAME%` 變數會指定簽發者名稱。</span><span class="sxs-lookup"><span data-stu-id="ce588-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="ce588-161">您可以變更這個變數來指定自己的簽發者名稱。</span><span class="sxs-lookup"><span data-stu-id="ce588-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="ce588-162">這個批次檔中的預設值為 Alice。</span><span class="sxs-lookup"><span data-stu-id="ce588-162">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="ce588-163">憑證會儲存在位於 CurrentUser 存放區位置下的 My 存放區中。</span><span class="sxs-lookup"><span data-stu-id="ce588-163">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="ce588-164">將簽發者憑證安裝至伺服器的受信任憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="ce588-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="ce588-165">Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="ce588-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ce588-166">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ce588-167">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將簽發者憑證填入伺服器憑證的步驟。</span><span class="sxs-lookup"><span data-stu-id="ce588-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="ce588-168">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="ce588-168">To set up and build the sample</span></span>

1. <span data-ttu-id="ce588-169">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ce588-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ce588-170">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ce588-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="ce588-171">如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce588-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ce588-172">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="ce588-172">To run the sample on the same computer</span></span>

1. <span data-ttu-id="ce588-173">從範例安裝資料夾內以系統管理員權限執行 Visual Studio 2012 命令提示字元執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="ce588-173">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="ce588-174">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-174">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ce588-175">Setup.bat 批次檔被設計來從 Visual Studio 2012 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="ce588-175">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="ce588-176">路徑環境變數設定在 Visual Studio 2012 命令提示字元會指向包含 Setup.bat 指令碼所需的可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="ce588-176">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="ce588-177">從 service\bin 啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="ce588-177">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="ce588-178">從 \client\bin 啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="ce588-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ce588-179">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="ce588-179">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="ce588-180">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="ce588-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ce588-181">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="ce588-181">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="ce588-182">在服務電腦上為服務二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="ce588-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="ce588-183">將服務程式檔複製到服務電腦上的服務目錄。</span><span class="sxs-lookup"><span data-stu-id="ce588-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="ce588-184">同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="ce588-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="ce588-185">您伺服器憑證的主體名稱必須包含電腦的完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="ce588-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="ce588-186">此 Service.exe.config 檔必須更新以反映這個新憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="ce588-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="ce588-187">您可以修改 Setup.bat 批次檔來建立伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="ce588-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="ce588-188">請注意，在開發人員命令提示字元使用系統管理員權限開啟的 Visual Studio 視窗必須執行 setup.bat 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce588-188">Note that the setup.bat file must be run in a Developer Command Prompt for Visual Studio window opened with administrator privileges.</span></span> <span data-ttu-id="ce588-189">您必須將 `%SERVER_NAME%` 變數設定為用來裝載服務之電腦的完整主機名稱。</span><span class="sxs-lookup"><span data-stu-id="ce588-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="ce588-190">將伺服器憑證複製到用戶端的 CurrentUser-TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="ce588-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="ce588-191">當伺服器憑證是由用戶端信任的簽發者發行時，就不需要這個步驟。</span><span class="sxs-lookup"><span data-stu-id="ce588-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="ce588-192">在服務電腦的 Service.exe.config 檔中變更基底位址的值，以指定完整電腦名稱而不要指定 localhost。</span><span class="sxs-lookup"><span data-stu-id="ce588-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="ce588-193">在服務電腦上，從命令提示字元執行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="ce588-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="ce588-194">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="ce588-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="ce588-195">在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="ce588-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="ce588-196">在用戶端電腦上，從命令提示字元視窗啟動 `Client.exe`。</span><span class="sxs-lookup"><span data-stu-id="ce588-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="ce588-197">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="ce588-197">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ce588-198">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="ce588-198">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="ce588-199">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="ce588-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
