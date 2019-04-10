---
title: 支援權杖
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 5f2b1500f54f8ade3c4924e3eb22cd022c6800c0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334181"
---
# <a name="supporting-tokens"></a><span data-ttu-id="4f090-102">支援權杖</span><span class="sxs-lookup"><span data-stu-id="4f090-102">Supporting Tokens</span></span>
<span data-ttu-id="4f090-103">這個支援權杖範例會示範如何將其他權杖加入至使用 WS-Security 的訊息。</span><span class="sxs-lookup"><span data-stu-id="4f090-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="4f090-104">範例除了使用者名稱安全性權杖之外，還會新增 X.509 二進位安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="4f090-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="4f090-105">權杖會在 WS-Security 訊息標頭中從用戶端傳遞至服務，而且使用與 X.509 安全性權杖相關聯的私密金鑰簽署該訊息的一部分，以便向接收者證明持有 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="4f090-106">在必須有多個宣告與訊息產生關聯才能驗證或授權傳送者的情況下，這將十分有幫助。</span><span class="sxs-lookup"><span data-stu-id="4f090-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="4f090-107">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="4f090-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4f090-108">示範</span><span class="sxs-lookup"><span data-stu-id="4f090-108">Demonstrates</span></span>
 <span data-ttu-id="4f090-109">範例會示範下列情況：</span><span class="sxs-lookup"><span data-stu-id="4f090-109">The sample demonstrates:</span></span>

-   <span data-ttu-id="4f090-110">用戶端如何傳遞其他安全性權杖給服務。</span><span class="sxs-lookup"><span data-stu-id="4f090-110">How a client can pass additional security tokens to a service.</span></span>

-   <span data-ttu-id="4f090-111">伺服器如何存取與其他安全性權杖相關聯的宣告。</span><span class="sxs-lookup"><span data-stu-id="4f090-111">How the server can access claims associated with additional security tokens.</span></span>

-   <span data-ttu-id="4f090-112">如何使用伺服器的 X.509 憑證保護用於訊息加密和簽章的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="4f090-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
>  <span data-ttu-id="4f090-113">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="4f090-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="4f090-114">用戶端透過使用者名稱權杖和支援的 X.509 安全性權杖進行驗證</span><span class="sxs-lookup"><span data-stu-id="4f090-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>
 <span data-ttu-id="4f090-115">服務會公開用來通訊的單一端點，此端點是使用 `BindingHelper` 和 `EchoServiceHost` 類別，透過程式設計所建立的。</span><span class="sxs-lookup"><span data-stu-id="4f090-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="4f090-116">端點是由位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="4f090-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="4f090-117">繫結是透過使用 `SymmetricSecurityBindingElement` 和 `HttpTransportBindingElement` 的自訂繫結所設定。</span><span class="sxs-lookup"><span data-stu-id="4f090-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="4f090-118">這個範例會設定 `SymmetricSecurityBindingElement`，使其在傳輸期間使用服務 X.509 憑證來保護對稱金鑰，以及在 WS-Security 訊息標頭中傳遞 `UserNameToken` 以及支援的 `X509SecurityToken`。</span><span class="sxs-lookup"><span data-stu-id="4f090-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="4f090-119">對稱金鑰會用來加密訊息本文和使用者名稱安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="4f090-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="4f090-120">支援權杖會包含在 WS-Security 訊息標頭中，當做其他二進位安全性權杖傳遞。</span><span class="sxs-lookup"><span data-stu-id="4f090-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="4f090-121">支援權杖的真實性是使用與支援之 X.509 安全性權杖相關聯的私密金鑰來簽署訊息的一部分，而獲得證明。</span><span class="sxs-lookup"><span data-stu-id="4f090-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

```csharp
public static Binding CreateMultiFactorAuthenticationBinding()
{
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

    // the message security binding element will be configured to require 2 tokens:
    // 1) A username-password encrypted with the service token
    // 2) A client certificate used to sign the message

    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();

    // Create supporting token parameters for the client X509 certificate.
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();
    // Specify that the supporting token is passed in message send by the client to the service
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;
    // Turn off derived keys
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);

    // Create a CustomBinding based on the constructed security binding element.
    return new CustomBinding(messageSecurity, httpTransport);
}
```

 <span data-ttu-id="4f090-122">此行為會指定要用於用戶端驗證的服務認證，以及服務 X.509 憑證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4f090-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="4f090-123">此範例會使用 `CN=localhost` 做為服務 X.509 憑證中的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="4f090-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

```csharp
override protected void InitializeRuntime()
{
    // Extract the ServiceCredentials behavior or create one.
    ServiceCredentials serviceCredentials =
        this.Description.Behaviors.Find<ServiceCredentials>();
    if (serviceCredentials == null)
    {
        serviceCredentials = new ServiceCredentials();
        this.Description.Behaviors.Add(serviceCredentials);
    }

    // Set the service certificate
    serviceCredentials.ServiceCertificate.SetCertificate(
                                       "CN=localhost");

/*
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.
*/
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;

    // Create the custom binding and add an endpoint to the service.
    Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
    this.AddServiceEndpoint(typeof(IEchoService),
                          multipleTokensBinding, string.Empty);
    base.InitializeRuntime();
}
```

 <span data-ttu-id="4f090-124">服務程式碼：</span><span class="sxs-lookup"><span data-stu-id="4f090-124">Service code:</span></span>

```csharp
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]
public class EchoService : IEchoService
{
    public string Echo()
    {
        string userName;
        string certificateSubjectName;
        GetCallerIdentities(
            OperationContext.Current.ServiceSecurityContext,
            out userName,
            out certificateSubjectName);
            return $"Hello {userName}, {certificateSubjectName}";
    }

    public void Dispose()
    {
    }

    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,
            string claimType, out TClaimResource resourceValue)
            where TClaimResource : class
    {
        resourceValue = default(TClaimResource);
        IEnumerable<Claim> matchingClaims =
            claimSet.FindClaims(claimType, Rights.PossessProperty);
        if(matchingClaims == null)
            return false;
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
        if (enumerator.MoveNext())
        {
            resourceValue =
              (enumerator.Current.Resource == null) ? null :
              (enumerator.Current.Resource as TClaimResource);
            return true;
        }
        else
        {
            return false;
        }
    }

    // Returns the username and certificate subject name provided by
    //the client
    void GetCallerIdentities(ServiceSecurityContext
        callerSecurityContext,
        out string userName, out string certificateSubjectName)
    {
        userName = null;
        certificateSubjectName = null;

       // Look in all the claimsets in the authorization context
       foreach (ClaimSet claimSet in
               callerSecurityContext.AuthorizationContext.ClaimSets)
       {
            if (claimSet is WindowsClaimSet)
            {
                // Try to find a Name claim. This will have been
                // generated from the windows username.
                string tmpName;
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                      out tmpName))
                {
                    userName = tmpName;
                }
            }
            else if (claimSet is X509CertificateClaimSet)
            {
                // Try to find an X500DisinguishedName claim. This will
                // have been generated from the client certificate.
                X500DistinguishedName tmpDistinguishedName;
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,
                               ClaimTypes.X500DistinguishedName,
                               out tmpDistinguishedName))
                {
                    certificateSubjectName = tmpDistinguishedName.Name;
                }
            }
        }
    }
}
```

 <span data-ttu-id="4f090-125">用戶端端點與服務端點的設定方式相似。</span><span class="sxs-lookup"><span data-stu-id="4f090-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="4f090-126">用戶端會使用相同的 `BindingHelper` 類別來建立繫結。</span><span class="sxs-lookup"><span data-stu-id="4f090-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="4f090-127">其餘的設定工作則在 `Client` 類別中進行。</span><span class="sxs-lookup"><span data-stu-id="4f090-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="4f090-128">用戶端會將使用者名稱安全性權杖和支援之 X.509 安全性權杖的相關資訊，以及安裝程式碼中的服務 X.509 憑證相關資訊，設定為用戶端端點行為集合。</span><span class="sxs-lookup"><span data-stu-id="4f090-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

```csharp
 static void Main()
 {
     // Create the custom binding and an endpoint address for
     // the service.
     Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
         EndpointAddress serviceAddress = new EndpointAddress(
         "http://localhost/servicemodelsamples/service.svc");
       ChannelFactory<IEchoService> channelFactory = null;
       IEchoService client = null;

       Console.WriteLine("Username authentication required.");
       Console.WriteLine(
         "Provide a valid machine or domain account. [domain\\user]");
       Console.WriteLine("   Enter username:");
       string username = Console.ReadLine();
       Console.WriteLine("   Enter password:");
       string password = "";
       ConsoleKeyInfo info = Console.ReadKey(true);
       while (info.Key != ConsoleKey.Enter)
       {
           if (info.Key != ConsoleKey.Backspace)
           {
               if (info.KeyChar != '\0')
               {
                   password += info.KeyChar;
                }
                info = Console.ReadKey(true);
            }
            else if (info.Key == ConsoleKey.Backspace)
            {
                if (password != "")
                {
                    password =
                       password.Substring(0, password.Length - 1);
                }
                info = Console.ReadKey(true);
            }
         }
         for (int i = 0; i < password.Length; i++)
            Console.Write("*");
         Console.WriteLine();
         try
         {
           // Create a proxy with the previously create binding and
           // endpoint address
              channelFactory =
                 new ChannelFactory<IEchoService>(
                     multipleTokensBinding, serviceAddress);
           // configure the username credentials, the client
           // certificate and the server certificate on the channel
           // factory
           channelFactory.Credentials.UserName.UserName = username;
           channelFactory.Credentials.UserName.Password = password;
           channelFactory.Credentials.ClientCertificate.SetCertificate(
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);
           client = channelFactory.CreateChannel();
           Console.WriteLine("Echo service returned: {0}",
                                           client.Echo());

           ((IChannel)client).Close();
           channelFactory.Close();
        }
        catch (CommunicationException e)
        {
         Abort((IChannel)client, channelFactory);
         // if there is a fault then print it out
         FaultException fe = null;
         Exception tmp = e;
         while (tmp != null)
         {
            fe = tmp as FaultException;
            if (fe != null)
            {
                break;
            }
            tmp = tmp.InnerException;
        }
        if (fe != null)
        {
           Console.WriteLine("The server sent back a fault: {0}",
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);
        }
        else
        {
         Console.WriteLine("The request failed with exception: {0}",e);
        }
    }
    catch (TimeoutException)
    {
        Abort((IChannel)client, channelFactory);
        Console.WriteLine("The request timed out");
    }
    catch (Exception e)
    {
         Abort((IChannel)client, channelFactory);
          Console.WriteLine(
          "The request failed with unexpected exception: {0}", e);
    }
    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();
}
```

## <a name="displaying-callers-information"></a><span data-ttu-id="4f090-129">顯示呼叫端的資訊</span><span class="sxs-lookup"><span data-stu-id="4f090-129">Displaying Callers' Information</span></span>
 <span data-ttu-id="4f090-130">若要顯示呼叫者的資訊，您可以使用 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4f090-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="4f090-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` 包含與目前呼叫者關聯的授權宣告。</span><span class="sxs-lookup"><span data-stu-id="4f090-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="4f090-132">這些宣告會自動提供 Windows Communication Foundation (WCF) 的每個訊息中收到的權杖。</span><span class="sxs-lookup"><span data-stu-id="4f090-132">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

```csharp
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string
                         claimType, out TClaimResource resourceValue)
    where TClaimResource : class
{
    resourceValue = default(TClaimResource);
    IEnumerable<Claim> matchingClaims =
    claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
          return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    if (enumerator.MoveNext())
    {
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);
        return true;
    }
    else
    {
         return false;
    }
}

// Returns the username and certificate subject name provided by the client
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)
{
    userName = null;
    certificateSubjectName = null;

    // Look in all the claimsets in the authorization context
    foreach (ClaimSet claimSet in
      callerSecurityContext.AuthorizationContext.ClaimSets)
    {
        if (claimSet is WindowsClaimSet)
        {
            // Try to find a Name claim. This will have been generated
            //from the windows username.
            string tmpName;
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                     out tmpName))
            {
                userName = tmpName;
            }
        }
        else if (claimSet is X509CertificateClaimSet)
         {
            //Try to find an X500DisinguishedName claim.
            //This will have been generated from the client
            //certificate.
            X500DistinguishedName tmpDistinguishedName;
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,
               ClaimTypes.X500DistinguishedName,
               out tmpDistinguishedName))
            {
                    certificateSubjectName = tmpDistinguishedName.Name;
            }
        }
    }
}
```

## <a name="running-the-sample"></a><span data-ttu-id="4f090-133">執行範例</span><span class="sxs-lookup"><span data-stu-id="4f090-133">Running the Sample</span></span>
 <span data-ttu-id="4f090-134">當您執行範例時，用戶端首先會提示您提供使用者名稱權杖的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4f090-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="4f090-135">請務必提供正確的值，您的系統帳戶，因為 WCF 服務上的對應至系統所提供的身分識別提供使用者名稱權杖中的值。</span><span class="sxs-lookup"><span data-stu-id="4f090-135">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="4f090-136">然後，用戶端便會顯示服務的回應。</span><span class="sxs-lookup"><span data-stu-id="4f090-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="4f090-137">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="4f090-137">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="4f090-138">設定批次檔</span><span class="sxs-lookup"><span data-stu-id="4f090-138">Setup Batch File</span></span>
 <span data-ttu-id="4f090-139">這個範例隨附的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的網際網路資訊服務 (IIS) 裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f090-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="4f090-140">這個批次檔必須經過修改才能跨機器運作，或在非裝載的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="4f090-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="4f090-141">下面提供批次檔的各區段簡要概觀，讓您將批次檔修改為可在適當的組態下執行。</span><span class="sxs-lookup"><span data-stu-id="4f090-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="4f090-142">建立用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="4f090-142">Creating the Client Certificate</span></span>
 <span data-ttu-id="4f090-143">下列 Setup.bat 批次檔中的程式行會建立要使用的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="4f090-144">`%CLIENT_NAME%` 變數會指定用戶端憑證的主體。</span><span class="sxs-lookup"><span data-stu-id="4f090-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="4f090-145">這個範例使用 "client.com" 做為主體名稱。</span><span class="sxs-lookup"><span data-stu-id="4f090-145">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="4f090-146">憑證會儲存在 `CurrentUser` 存放區位置下的 My (Personal) 存放區中。</span><span class="sxs-lookup"><span data-stu-id="4f090-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="4f090-147">將用戶端憑證安裝至伺服器的受信任存放區中</span><span class="sxs-lookup"><span data-stu-id="4f090-147">Installing the Client Certificate into the Server's Trusted Store</span></span>
 <span data-ttu-id="4f090-148">Setup.bat 批次檔中的下列程式行會將用戶端憑證複製到伺服器的受信任人存放區。</span><span class="sxs-lookup"><span data-stu-id="4f090-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="4f090-149">這是必要步驟，因為伺服器系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="4f090-150">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。</span><span class="sxs-lookup"><span data-stu-id="4f090-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="4f090-151">建立伺服器憑證</span><span class="sxs-lookup"><span data-stu-id="4f090-151">Creating the Server Certificate</span></span>
 <span data-ttu-id="4f090-152">下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="4f090-153">`%SERVER_NAME%` 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="4f090-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="4f090-154">您可以變更這個變數來指定自己的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="4f090-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="4f090-155">這個批次檔中的預設值為 localhost。</span><span class="sxs-lookup"><span data-stu-id="4f090-155">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="4f090-156">憑證會儲存在 LocalMachine 存放區位置下的 My (Personal) 存放區中。</span><span class="sxs-lookup"><span data-stu-id="4f090-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="4f090-157">憑證會儲存在 IIS 裝載服務的 LocalMachine 存放區中。</span><span class="sxs-lookup"><span data-stu-id="4f090-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="4f090-158">對於自我裝載的服務，您應該以 CurrentUser 取代字串 LocalMachine，將批次檔改為在 CurrentUser 存放區的位置上儲存伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="4f090-159">將伺服器憑證安裝至用戶端的受信任憑證存放區中</span><span class="sxs-lookup"><span data-stu-id="4f090-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>
 <span data-ttu-id="4f090-160">Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="4f090-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="4f090-161">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4f090-162">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。</span><span class="sxs-lookup"><span data-stu-id="4f090-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="4f090-163">啟用對憑證私密金鑰的存取</span><span class="sxs-lookup"><span data-stu-id="4f090-163">Enabling Access to the Certificate's Private Key</span></span>
 <span data-ttu-id="4f090-164">若要啟用從 IIS 裝載服務對憑證私密金鑰進行的存取，就必須將私密金鑰的適當權限授與用於執行 IIS 裝載處理序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4f090-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="4f090-165">Setup.bat 指令碼中的最後幾個步驟將會完成這個部分。</span><span class="sxs-lookup"><span data-stu-id="4f090-165">This is accomplished by last steps in the Setup.bat script.</span></span>

```
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4f090-166">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="4f090-166">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4f090-167">確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4f090-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="4f090-168">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4f090-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="4f090-169">若要在單一或跨電腦的組態中執行本範例，請使用下列指示。</span><span class="sxs-lookup"><span data-stu-id="4f090-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="4f090-170">若要在同一部機器上執行範例</span><span class="sxs-lookup"><span data-stu-id="4f090-170">To run the sample on the same machine</span></span>

1. <span data-ttu-id="4f090-171">從範例安裝資料夾內以系統管理員權限執行 Visual Studio 2012 命令提示字元執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="4f090-171">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="4f090-172">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-172">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="4f090-173">Setup.bat 批次檔被設計來從 Visual Studio 2012 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="4f090-173">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="4f090-174">路徑環境變數設定在 Visual Studio 2012 命令提示字元會指向包含 Setup.bat 指令碼所需的可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="4f090-174">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="4f090-175">當您完成範例時，請務必執行 Cleanup.bat 以移除憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="4f090-176">其他安全性範例使用相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-176">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="4f090-177">從 \client\bin 啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="4f090-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="4f090-178">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="4f090-178">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="4f090-179">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="4f090-179">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="4f090-180">若要跨機器執行範例</span><span class="sxs-lookup"><span data-stu-id="4f090-180">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="4f090-181">在服務機器上建立目錄。</span><span class="sxs-lookup"><span data-stu-id="4f090-181">Create a directory on the service machine.</span></span> <span data-ttu-id="4f090-182">使用網際網路資訊服務 (IIS) 管理工具，為這個目錄建立名為 servicemodelsamples 的虛擬應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f090-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="4f090-183">將 \inetpub\wwwroot\servicemodelsamples 中的服務程式檔複製至服務機器上的虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="4f090-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="4f090-184">確定複製 \bin 子目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f090-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="4f090-185">同時將 Setup.bat、Cleanup.bat 和 ImportClientCert.bat 檔案複製到服務機器。</span><span class="sxs-lookup"><span data-stu-id="4f090-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="4f090-186">在用戶端機器上為用戶端二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="4f090-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="4f090-187">將用戶端程式檔複製到用戶端機器上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="4f090-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="4f090-188">同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。</span><span class="sxs-lookup"><span data-stu-id="4f090-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="4f090-189">在伺服器上，執行`setup.bat service`在開發人員命令提示字元適用於 Visual Studio 開啟系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="4f090-189">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="4f090-190">執行`setup.bat`與`service`引數會建立具有機器完整網域名稱的服務憑證，並將服務憑證匯出為名為 Service.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f090-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="4f090-191">編輯 Web.config 以反映新的憑證名稱 (在`findValue`屬性中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) 做為機器的完整網域名稱相同。</span><span class="sxs-lookup"><span data-stu-id="4f090-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="4f090-192">從服務目錄中將 Service.cer 檔案複製至用戶端機器上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="4f090-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="4f090-193">在用戶端，執行`setup.bat client`在開發人員命令提示字元適用於 Visual Studio 開啟系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="4f090-193">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="4f090-194">使用 `setup.bat` 引數來執行 `client`，就會建立名稱為 client.com 的用戶端憑證，並且會將用戶端憑證匯出為名為 Client.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f090-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="4f090-195">在用戶端機器上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="4f090-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="4f090-196">若要這麼做，請使用伺服器的完整網域名稱取代 localhost。</span><span class="sxs-lookup"><span data-stu-id="4f090-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="4f090-197">從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。</span><span class="sxs-lookup"><span data-stu-id="4f090-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="4f090-198">在用戶端上執行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="4f090-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="4f090-199">這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="4f090-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="4f090-200">在伺服器上執行 ImportClientCert.bat，這樣會從 Client.cer 檔案中將用戶端憑證匯入至 LocalMachine - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="4f090-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="4f090-201">在用戶端機器上，從命令提示字元視窗啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="4f090-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="4f090-202">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="4f090-202">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4f090-203">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="4f090-203">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="4f090-204">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="4f090-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f090-205">跨機器執行此範例時，這個指令碼不會移除用戶端上的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="4f090-206">如果您已執行跨機器使用憑證的 WCF 範例，請務必清除已安裝在 CurrentUser-TrustedPeople 存放區的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="4f090-206">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="4f090-207">若要這樣做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 例如： `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="4f090-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
