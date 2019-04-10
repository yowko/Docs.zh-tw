---
title: 權杖驗證器
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 501f1801c1cb475a87c586f8bbc14146b9141047
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306244"
---
# <a name="token-authenticator"></a><span data-ttu-id="0e885-102">權杖驗證器</span><span class="sxs-lookup"><span data-stu-id="0e885-102">Token Authenticator</span></span>
<span data-ttu-id="0e885-103">這個範例示範如何實作自訂權杖驗證器。</span><span class="sxs-lookup"><span data-stu-id="0e885-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="0e885-104">Windows Communication Foundation (WCF) 中的權杖驗證器用來驗證語彙基元，用訊息，確認它是前後一致，而且驗證身分識別相關聯的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0e885-104">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="0e885-105">自訂權杖驗證器適用於各種情況，例如：</span><span class="sxs-lookup"><span data-stu-id="0e885-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>

-   <span data-ttu-id="0e885-106">您想要覆寫與權杖有關聯的預設驗證機制。</span><span class="sxs-lookup"><span data-stu-id="0e885-106">When you want to override the default authentication mechanism associated with a token.</span></span>

-   <span data-ttu-id="0e885-107">您正在建置自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="0e885-107">When you are building a custom token.</span></span>

 <span data-ttu-id="0e885-108">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="0e885-108">This sample demonstrates the following:</span></span>

-   <span data-ttu-id="0e885-109">用戶端如何透過使用者名稱/密碼組進行驗證。</span><span class="sxs-lookup"><span data-stu-id="0e885-109">How a client can authenticate using a username/password pair.</span></span>

-   <span data-ttu-id="0e885-110">伺服器如何使用自訂權杖驗證器驗證用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="0e885-110">How the server can validate the client credentials using a custom token authenticator.</span></span>

-   <span data-ttu-id="0e885-111">如何使用自訂權杖驗證器繫結的 WCF 服務程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e885-111">How the WCF service code ties in with the custom token authenticator.</span></span>

-   <span data-ttu-id="0e885-112">如何使用伺服器的 X.509 憑證來驗證伺服器。</span><span class="sxs-lookup"><span data-stu-id="0e885-112">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="0e885-113">這個範例也示範如何呼叫者身分識別是可以由存取 WCF 自訂權杖驗證程序之後。</span><span class="sxs-lookup"><span data-stu-id="0e885-113">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="0e885-114">服務會公開 (Expose) 單一的端點來與已使用組態檔 App.config 定義之服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="0e885-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="0e885-115">端點是由位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="0e885-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="0e885-116">繫結已設定成標準 `wsHttpBinding`，以及將安全性模式設為訊息 (`wsHttpBinding` 的預設模式)。</span><span class="sxs-lookup"><span data-stu-id="0e885-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="0e885-117">這個範例會將標準 `wsHttpBinding` 設定為使用用戶端使用者名稱驗證。</span><span class="sxs-lookup"><span data-stu-id="0e885-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="0e885-118">服務也會使用 `serviceCredentials` 行為來設定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="0e885-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="0e885-119">`securityCredentials` 行為允許您指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="0e885-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="0e885-120">服務憑證是由用戶端用來驗證服務並提供訊息保護。</span><span class="sxs-lookup"><span data-stu-id="0e885-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="0e885-121">下列組態會參考在安裝範例期間所安裝的 localhost 憑證，如下列安裝指示中所述。</span><span class="sxs-lookup"><span data-stu-id="0e885-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="0e885-122">用戶端的端點組態是由組態名稱、服務端點的絕對位址、繫結和合約所組成。</span><span class="sxs-lookup"><span data-stu-id="0e885-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="0e885-123">用戶端繫結是透過適當的 `Mode` 和 `clientCredentialType` 所設定。</span><span class="sxs-lookup"><span data-stu-id="0e885-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <endpoint name=""
                address="http://localhost:8000/servicemodelsamples/service"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
```

 <span data-ttu-id="0e885-124">用戶端實作會設定要使用的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="0e885-124">The client implementation sets the user name and password to use.</span></span>

```
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="0e885-125">自訂權杖驗證器</span><span class="sxs-lookup"><span data-stu-id="0e885-125">Custom Token Authenticator</span></span>
 <span data-ttu-id="0e885-126">使用下列步驟來建立自訂權杖驗證器：</span><span class="sxs-lookup"><span data-stu-id="0e885-126">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="0e885-127">撰寫自訂權杖驗證器。</span><span class="sxs-lookup"><span data-stu-id="0e885-127">Write a custom token authenticator.</span></span>

     <span data-ttu-id="0e885-128">範例會實作自訂權杖驗證器，以驗證使用者名稱是否具備有效的電子郵件格式。</span><span class="sxs-lookup"><span data-stu-id="0e885-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="0e885-129">此驗證器會衍生 <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="0e885-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="0e885-130">這個類別中最重要的方法是 <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>。</span><span class="sxs-lookup"><span data-stu-id="0e885-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="0e885-131">在這個方法中，驗證器會確認使用者名稱的格式有效，以及主機名稱不是來自惡意網域。</span><span class="sxs-lookup"><span data-stu-id="0e885-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="0e885-132">如果兩個條件都符合，便會傳回 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 執行個體的唯讀集合，而這個集合則用來提供表示儲存於使用者名稱權杖內之資訊的宣告。</span><span class="sxs-lookup"><span data-stu-id="0e885-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. <span data-ttu-id="0e885-133">提供由自訂權杖驗證器傳回的授權原則。</span><span class="sxs-lookup"><span data-stu-id="0e885-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="0e885-134">這個範例自行提供名為 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 的 `UnconditionalPolicy` 實作，此實作會傳回一組在已於建構函式中傳遞給它的宣告和身分識別。</span><span class="sxs-lookup"><span data-stu-id="0e885-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. <span data-ttu-id="0e885-135">撰寫自訂安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="0e885-135">Write a custom security token manager.</span></span>

     <span data-ttu-id="0e885-136">您可以使用 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 來為特定 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 物件 (這會在 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 方法中傳遞給前者) 建立 `CreateSecurityTokenAuthenticator`。</span><span class="sxs-lookup"><span data-stu-id="0e885-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="0e885-137">安全性權杖管理員也會用來建立權杖提供者與權杖序列化程式，但是這些不在本範例的討論範圍。</span><span class="sxs-lookup"><span data-stu-id="0e885-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="0e885-138">在這個範例中，自訂安全性權杖管理員繼承自 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 類別，並且會覆寫 `CreateSecurityTokenAuthenticator` 方法，以便在傳遞的權杖需求表示要求使用者名稱驗證器時傳回自訂使用者名稱權杖驗證器。</span><span class="sxs-lookup"><span data-stu-id="0e885-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. <span data-ttu-id="0e885-139">撰寫自訂服務認證。</span><span class="sxs-lookup"><span data-stu-id="0e885-139">Write a custom service credential.</span></span>

     <span data-ttu-id="0e885-140">服務認證類別可用來表示針對服務所設定的認證，並建立用來取得權杖驗證器、權杖提供者和權杖序列化程式的安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="0e885-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. <span data-ttu-id="0e885-141">將服務設定為使用自訂服務認證。</span><span class="sxs-lookup"><span data-stu-id="0e885-141">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="0e885-142">為了讓服務能夠使用自訂服務認證，範例已在擷取預先設定於預設服務認證中的服務憑證之後刪除預設服務認證類別，然後將新的服務認證執行個體設定為使用預先設定的服務憑證，再將這個新服務認證執行個體新增至服務行為。</span><span class="sxs-lookup"><span data-stu-id="0e885-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="0e885-143">若要顯示呼叫者的資訊，您可以使用 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0e885-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="0e885-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 包含有關目前呼叫者的宣告資訊。</span><span class="sxs-lookup"><span data-stu-id="0e885-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="0e885-145">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="0e885-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0e885-146">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="0e885-146">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="0e885-147">設定批次檔</span><span class="sxs-lookup"><span data-stu-id="0e885-147">Setup Batch File</span></span>
 <span data-ttu-id="0e885-148">本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e885-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="0e885-149">這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="0e885-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="0e885-150">下面提供批次檔的各區段簡要概觀，讓您將批次檔修改為可在適當的組態下執行。</span><span class="sxs-lookup"><span data-stu-id="0e885-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

-   <span data-ttu-id="0e885-151">建立伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="0e885-151">Creating the server certificate.</span></span>

     <span data-ttu-id="0e885-152">下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="0e885-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="0e885-153">`%SERVER_NAME%` 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="0e885-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="0e885-154">您可以變更這個變數來指定自己的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="0e885-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="0e885-155">這個批次檔中的預設值為 localhost。</span><span class="sxs-lookup"><span data-stu-id="0e885-155">The default in this batch file is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="0e885-156">將伺服器憑證安裝至用戶端的受信任憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="0e885-156">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="0e885-157">Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="0e885-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="0e885-158">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="0e885-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="0e885-159">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。</span><span class="sxs-lookup"><span data-stu-id="0e885-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="0e885-160">安裝批次檔是設計用來從 Windows SDK 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="0e885-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="0e885-161">它要求 MSSDK 環境變數指向安裝 SDK 的目錄。</span><span class="sxs-lookup"><span data-stu-id="0e885-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="0e885-162">這個環境變數是自動在 Windows SDK 命令提示字元中設定。</span><span class="sxs-lookup"><span data-stu-id="0e885-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="0e885-163">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="0e885-163">To set up and build the sample</span></span>

1. <span data-ttu-id="0e885-164">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0e885-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0e885-165">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0e885-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="0e885-166">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="0e885-166">To run the sample on the same computer</span></span>

1. <span data-ttu-id="0e885-167">從範例安裝資料夾內以系統管理員權限開啟 Visual Studio 2012 命令提示字元執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="0e885-167">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="0e885-168">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="0e885-168">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="0e885-169">Setup.bat 批次檔被設計來從 Visual Studio 2012 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="0e885-169">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="0e885-170">路徑環境變數設定在 Visual Studio 2012 命令提示字元會指向包含 Setup.bat 指令碼所需的可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="0e885-170">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="0e885-171">從 service\bin 啟動 service.exe。</span><span class="sxs-lookup"><span data-stu-id="0e885-171">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="0e885-172">從 \client\bin 啟動 client.exe。</span><span class="sxs-lookup"><span data-stu-id="0e885-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="0e885-173">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="0e885-173">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="0e885-174">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="0e885-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="0e885-175">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="0e885-175">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="0e885-176">在服務電腦上為服務二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="0e885-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="0e885-177">將服務程式檔複製到服務電腦上的服務目錄。</span><span class="sxs-lookup"><span data-stu-id="0e885-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="0e885-178">同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="0e885-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="0e885-179">您伺服器憑證的主體名稱必須包含電腦的完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="0e885-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="0e885-180">必須更新服務 App.config 檔以反映這個新憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="0e885-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="0e885-181">只要將 `%SERVER_NAME%` 變數設定為服務執行所在之電腦的完整主機名稱，就可以使用 Setup.bat 建立憑證。</span><span class="sxs-lookup"><span data-stu-id="0e885-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="0e885-182">請注意，setup.bat 檔必須從開發人員命令提示字元執行適用於 Visual Studio 開啟系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="0e885-182">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="0e885-183">將伺服器憑證複製到用戶端的 CurrentUser-TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="0e885-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="0e885-184">只有在伺服器憑證是由用戶端受信任的簽發者發行時才需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="0e885-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="0e885-185">在服務電腦的 App.config 檔中變更基底位址的值，以指定完整電腦名稱而不要指定 localhost。</span><span class="sxs-lookup"><span data-stu-id="0e885-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="0e885-186">在服務電腦上，從命令提示字元執行 service.exe。</span><span class="sxs-lookup"><span data-stu-id="0e885-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="0e885-187">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="0e885-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="0e885-188">在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="0e885-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="0e885-189">在用戶端電腦上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="0e885-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="0e885-190">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="0e885-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0e885-191">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="0e885-191">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="0e885-192">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="0e885-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
