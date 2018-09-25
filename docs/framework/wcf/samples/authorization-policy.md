---
title: 授權原則
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 78ca42abfd2df56edeeb273fcd8ba585aa16f635
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111434"
---
# <a name="authorization-policy"></a><span data-ttu-id="91172-102">授權原則</span><span class="sxs-lookup"><span data-stu-id="91172-102">Authorization Policy</span></span>

<span data-ttu-id="91172-103">此範例示範如何實作自訂宣告授權原則以及關聯的自訂服務授權管理員。</span><span class="sxs-lookup"><span data-stu-id="91172-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="91172-104">當服務對服務作業執行宣告架構的存取檢查，以及在執行存取檢查前便授予呼叫者特定權限時，這個方法就會很有用處。</span><span class="sxs-lookup"><span data-stu-id="91172-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="91172-105">此範例同時說明新增宣告的處理序，以及對最後宣告集的存取檢查處理序。</span><span class="sxs-lookup"><span data-stu-id="91172-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="91172-106">用戶端與伺服器之間的所有應用程式訊息都會經過簽署及加密。</span><span class="sxs-lookup"><span data-stu-id="91172-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="91172-107">根據預設，使用 `wsHttpBinding` 繫結時，會使用用戶端所提供的使用者名稱和密碼來登入有效的 Windows NT 帳戶。</span><span class="sxs-lookup"><span data-stu-id="91172-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="91172-108">此範例示範如何使用自訂 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="91172-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="91172-109">此外，此範例會說明用戶端如何使用 X.509 憑證來向服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="91172-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="91172-110">此範例說明 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 和 <xref:System.ServiceModel.ServiceAuthorizationManager> 的實作 (此實作會針對特定使用者將存取權限授予特定的服務方法)。</span><span class="sxs-lookup"><span data-stu-id="91172-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="91172-111">此樣本根據[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)，但會示範如何執行宣告轉換之前<xref:System.ServiceModel.ServiceAuthorizationManager>所呼叫。</span><span class="sxs-lookup"><span data-stu-id="91172-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="91172-112">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="91172-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="91172-113">這個範例所示範的作業摘要如下：</span><span class="sxs-lookup"><span data-stu-id="91172-113">In summary, this sample demonstrates how:</span></span>

-   <span data-ttu-id="91172-114">用戶端可以使用使用者名稱與密碼來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="91172-114">The client can be authenticated using a user name-password.</span></span>

-   <span data-ttu-id="91172-115">用戶端可以使用 X.509 憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="91172-115">The client can be authenticated using an X.509 certificate.</span></span>

-   <span data-ttu-id="91172-116">伺服器會向自訂 `UsernamePassword` 驗證器驗證用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="91172-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

-   <span data-ttu-id="91172-117">伺服器是使用該伺服器的 X.509 憑證來驗證的。</span><span class="sxs-lookup"><span data-stu-id="91172-117">The server is authenticated using the server's X.509 certificate.</span></span>

-   <span data-ttu-id="91172-118">伺服器可以使用 <xref:System.ServiceModel.ServiceAuthorizationManager> 來控制服務中特定方法的存取。</span><span class="sxs-lookup"><span data-stu-id="91172-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

-   <span data-ttu-id="91172-119">如何實作 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>。</span><span class="sxs-lookup"><span data-stu-id="91172-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="91172-120">服務會公開兩個端點，以便與使用組態檔 App.config 定義的服務進行通訊。每個端點是由位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="91172-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="91172-121">其中一個繫結使用標準 `wsHttpBinding` 繫結 (使用 WS-Security 和用戶端使用者名稱驗證) 來設定。</span><span class="sxs-lookup"><span data-stu-id="91172-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="91172-122">另一個繫結使用標準 `wsHttpBinding` 繫結 (使用 WS-Security 和用戶端憑證驗證) 來設定。</span><span class="sxs-lookup"><span data-stu-id="91172-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="91172-123">[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)指定要用於服務驗證的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="91172-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="91172-124">伺服器憑證必須包含相同的值，如`SubjectName`屬性設為`findValue`屬性中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="91172-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
          <clientCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

<span data-ttu-id="91172-125">每個用戶端的端點組態是由組態名稱、服務端點的絕對位址、繫結和合約所組成。</span><span class="sxs-lookup"><span data-stu-id="91172-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="91172-126">用戶端繫結已設定適當的安全性模式，指定在此情況下在[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)並`clientCredentialType`中所指定[\<訊息 >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="91172-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="91172-127">針對使用者名稱架構的端點，用戶端實作會設定要使用的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="91172-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

<span data-ttu-id="91172-128">針對憑證架構的端點，用戶端實作會設定要使用的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

<span data-ttu-id="91172-129">此範例使用自訂 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 來驗證使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="91172-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="91172-130">此範例會實作衍生自 `MyCustomUserNamePasswordValidator` 的 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>。</span><span class="sxs-lookup"><span data-stu-id="91172-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="91172-131">如需詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 相關文件。</span><span class="sxs-lookup"><span data-stu-id="91172-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="91172-132">為了示範與 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的整合，此自訂驗證器範例會實作 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法以接受使用者名稱/密碼組，以使其中的使用者名稱符合下列程式碼中所示的密碼。</span><span class="sxs-lookup"><span data-stu-id="91172-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
{
  // This method validates users. It allows in two users,
  // test1 and test2 with passwords 1tset and 2tset respectively.
  // This code is for illustration purposes only and
  // MUST NOT be used in a production environment because it
  // is NOT secure.
  public override void Validate(string userName, string password)
  {
    if (null == userName || null == password)
    {
      throw new ArgumentNullException();
    }

    if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
    {
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

<span data-ttu-id="91172-133">一旦驗證程式在服務程式碼中實作，服務主機就必須收到要使用的驗證程式執行個體的相關通知。</span><span class="sxs-lookup"><span data-stu-id="91172-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="91172-134">這是使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="91172-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="91172-135">或者，您可以在組態中相同的動作：</span><span class="sxs-lookup"><span data-stu-id="91172-135">Or you can do the same thing in configuration:</span></span>

```xml
<behavior ...>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

<span data-ttu-id="91172-136">Windows Communication Foundation (WCF) 提供豐富的宣告式模型來執行存取檢查。</span><span class="sxs-lookup"><span data-stu-id="91172-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="91172-137"><xref:System.ServiceModel.ServiceAuthorizationManager> 物件會被用來執行存取檢查並判斷與用戶端相關的宣告是否能夠滿足存取服務方法所需的必要需求。</span><span class="sxs-lookup"><span data-stu-id="91172-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="91172-138">針對示範目的，此範例會示範如何實作<xref:System.ServiceModel.ServiceAuthorizationManager>可實<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>宣告的型別為基礎的方法，以允許使用者的存取方法 http://example.com/claims/allowedoperation其值會是此作業之動作 URI允許呼叫。</span><span class="sxs-lookup"><span data-stu-id="91172-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type http://example.com/claims/allowedoperation whose value is the Action URI of the operation that is allowed to be called.</span></span>

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

<span data-ttu-id="91172-139">一旦實作了自訂 <xref:System.ServiceModel.ServiceAuthorizationManager>，就必須告知服務主機要使用的 <xref:System.ServiceModel.ServiceAuthorizationManager>。</span><span class="sxs-lookup"><span data-stu-id="91172-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="91172-140">執行方式如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="91172-140">This is done as shown in the following code.</span></span>

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="91172-141">要實作的主要 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 方法為 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="91172-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

<span data-ttu-id="91172-142">前一段程式碼說明 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法會檢查並確定未新增任何會影響處理的新宣告，然後再新增特定宣告。</span><span class="sxs-lookup"><span data-stu-id="91172-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="91172-143">允許的宣告是從 `GetAllowedOpList` 方法取得，此方法經過實作，會傳回可供使用者執行的特定作業清單。</span><span class="sxs-lookup"><span data-stu-id="91172-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="91172-144">授權原則會新增宣告以便處理特定作業。</span><span class="sxs-lookup"><span data-stu-id="91172-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="91172-145">此宣告稍後會由 <xref:System.ServiceModel.ServiceAuthorizationManager> 使用，以執行存取檢查決策。</span><span class="sxs-lookup"><span data-stu-id="91172-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="91172-146">一旦實作了自訂 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>，就必須告知服務主機要使用的授權原則。</span><span class="sxs-lookup"><span data-stu-id="91172-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="91172-147">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="91172-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="91172-148">用戶端會順利呼叫 Add、Subtract 和 Multiple 方法，並在嘗試呼叫 Divide 方法時取得「拒絕存取」訊息。</span><span class="sxs-lookup"><span data-stu-id="91172-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="91172-149">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="91172-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="91172-150">設定批次檔</span><span class="sxs-lookup"><span data-stu-id="91172-150">Setup Batch File</span></span>

<span data-ttu-id="91172-151">本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="91172-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="91172-152">下面提供批次檔的各區段簡要概觀，讓批次檔得以修改為在適當的組態下執行：</span><span class="sxs-lookup"><span data-stu-id="91172-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

-   <span data-ttu-id="91172-153">建立伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-153">Creating the server certificate.</span></span>

     <span data-ttu-id="91172-154">下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="91172-155">%SERVER_NAME% 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="91172-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="91172-156">您可以變更這個變數來指定自己的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="91172-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="91172-157">預設值為 localhost。</span><span class="sxs-lookup"><span data-stu-id="91172-157">The default value is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="91172-158">將伺服器憑證安裝至用戶端的受信任憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="91172-158">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="91172-159">Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="91172-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="91172-160">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="91172-161">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。</span><span class="sxs-lookup"><span data-stu-id="91172-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   <span data-ttu-id="91172-162">建立用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-162">Creating the client certificate.</span></span>

     <span data-ttu-id="91172-163">下列 Setup.bat 批次檔中的程式行會建立要使用的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="91172-164">%USER_NAME% 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="91172-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="91172-165">這個值會設定為 "test1"，因為這是 `IAuthorizationPolicy` 會尋找的名稱。</span><span class="sxs-lookup"><span data-stu-id="91172-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="91172-166">如果變更了 %USER_NAME% 的值，您就必須在 `IAuthorizationPolicy.Evaluate` 方法中變更對應的值。</span><span class="sxs-lookup"><span data-stu-id="91172-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

     <span data-ttu-id="91172-167">憑證會儲存在 CurrentUser 存放區位置下的 My (Personal) 存放區中。</span><span class="sxs-lookup"><span data-stu-id="91172-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="91172-168">將用戶端憑證安裝至伺服器的受信任憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="91172-168">Installing the client certificate into server's trusted certificate store.</span></span>

     <span data-ttu-id="91172-169">Setup.bat 批次檔中的下列程式行會將用戶端憑證複製到受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="91172-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="91172-170">這是必要步驟，因為伺服器系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="91172-171">如果您已經有一個以信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將用戶端憑證填入伺服器憑證存放區的步驟。</span><span class="sxs-lookup"><span data-stu-id="91172-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="91172-172">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="91172-172">To set up and build the sample</span></span>

1. <span data-ttu-id="91172-173">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="91172-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="91172-174">若要在單一或跨電腦的組態中執行本範例，請使用下列指示。</span><span class="sxs-lookup"><span data-stu-id="91172-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="91172-175">如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="91172-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="91172-176">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="91172-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="91172-177">開啟系統管理員權限適用於 Visual Studio 開發人員命令提示字元並執行*Setup.bat*從範例安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="91172-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="91172-178">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="91172-179">Setup.bat 批次檔被設計來執行適用於 Visual Studio 從開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="91172-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="91172-180">Visual Studio 指向包含所需的可執行檔的目錄路徑環境變數設定在 「 開發人員命令提示字元*Setup.bat*指令碼。</span><span class="sxs-lookup"><span data-stu-id="91172-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="91172-181">從啟動 Service.exe *service\bin*。</span><span class="sxs-lookup"><span data-stu-id="91172-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="91172-182">從啟動 Client.exe *\client\bin*。</span><span class="sxs-lookup"><span data-stu-id="91172-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="91172-183">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="91172-183">Client activity is displayed on the client console application.</span></span>

  <span data-ttu-id="91172-184">如果用戶端和服務能夠進行通訊，請參閱[疑難排解祕訣](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="91172-184">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="91172-185">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="91172-185">To run the sample across computers</span></span>

1. <span data-ttu-id="91172-186">在服務電腦上建立目錄。</span><span class="sxs-lookup"><span data-stu-id="91172-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="91172-187">從服務程式檔複製*\service\bin*到服務電腦上的目錄。</span><span class="sxs-lookup"><span data-stu-id="91172-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="91172-188">同時將 Setup.bat、Cleanup.bat、GetComputerName.vbs 和 ImportClientCert.bat 檔複製到服務電腦上。</span><span class="sxs-lookup"><span data-stu-id="91172-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="91172-189">在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="91172-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="91172-190">將用戶端程式檔複製到用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="91172-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="91172-191">同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。</span><span class="sxs-lookup"><span data-stu-id="91172-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="91172-192">在伺服器上，執行`setup.bat service`中開發人員命令提示字元使用系統管理員權限開啟的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="91172-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="91172-193">執行`setup.bat`具有`service`引數建立電腦的完整的網域名稱服務憑證，並將服務憑證匯出至名為的檔案*Service.cer*。</span><span class="sxs-lookup"><span data-stu-id="91172-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="91172-194">編輯*Service.exe.config*以反映新的憑證名稱 (在`findValue`屬性中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) 這是完整的網域名稱相同電腦。</span><span class="sxs-lookup"><span data-stu-id="91172-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="91172-195">也會變更**computername**中\<服務 > /\<baseAddresses > 項目服務電腦的完整名稱從 localhost。</span><span class="sxs-lookup"><span data-stu-id="91172-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="91172-196">複製*Service.cer*檔案從服務目錄至用戶端目錄用戶端電腦上的。</span><span class="sxs-lookup"><span data-stu-id="91172-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="91172-197">在用戶端，執行`setup.bat client`中開發人員命令提示字元使用系統管理員權限開啟的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="91172-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="91172-198">執行`setup.bat`具有`client`引數會建立名為用戶端憑證**test1** ，並將用戶端憑證匯出為名為檔案*Client.cer*。</span><span class="sxs-lookup"><span data-stu-id="91172-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="91172-199">在  *Client.exe.config*檔案在用戶端電腦上，變更端點位址值以符合您的服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="91172-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="91172-200">執行這項操作來取代**localhost**伺服器的完整的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="91172-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="91172-201">從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。</span><span class="sxs-lookup"><span data-stu-id="91172-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="91172-202">在用戶端，執行*ImportServiceCert.bat*中開發人員命令提示字元使用系統管理員權限開啟的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="91172-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="91172-203">這會在將服務憑證從 Service.cer 檔案匯入**CurrentUser-TrustedPeople**儲存。</span><span class="sxs-lookup"><span data-stu-id="91172-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="91172-204">在伺服器上，執行*ImportClientCert.bat*中開發人員命令提示字元使用系統管理員權限開啟的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="91172-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="91172-205">這會從 Client.cer 檔案匯入的用戶端憑證**LocalMachine-TrustedPeople**儲存。</span><span class="sxs-lookup"><span data-stu-id="91172-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="91172-206">在伺服器電腦上，從命令提示字元視窗啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="91172-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="91172-207">在用戶端電腦上，從命令提示字元視窗啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="91172-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

   <span data-ttu-id="91172-208">如果用戶端和服務能夠進行通訊，請參閱[疑難排解祕訣](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="91172-208">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="91172-209">在此範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="91172-209">Clean up after the sample</span></span>

<span data-ttu-id="91172-210">若要清除在此範例之後，執行*Cleanup.bat*當您完成執行範例中的 [samples] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="91172-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="91172-211">這樣會從憑證存放區中移除伺服器與用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="91172-212">跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="91172-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="91172-213">如果您已執行 WCF 範例，在電腦之間使用的憑證，請務必清除的服務憑證已安裝在 CurrentUser-TrustedPeople 存放。</span><span class="sxs-lookup"><span data-stu-id="91172-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="91172-214">若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="91172-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>