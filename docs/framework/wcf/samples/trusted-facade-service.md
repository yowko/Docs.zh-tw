---
title: 信任的外觀服務
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: d5a4cfe63f2fc6facbe4ce78d1c0047349e303fd
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807657"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="4fed9-102">信任的外觀服務</span><span class="sxs-lookup"><span data-stu-id="4fed9-102">Trusted Facade Service</span></span>
<span data-ttu-id="4fed9-103">這個案例範例示範如何呼叫者的身分識別資訊從一項服務之間使用 Windows Communication Foundation (WCF) 安全性基礎結構。</span><span class="sxs-lookup"><span data-stu-id="4fed9-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="4fed9-104">這是使用外觀服務將服務提供的功能公開至公用網路的一般設計模式。</span><span class="sxs-lookup"><span data-stu-id="4fed9-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="4fed9-105">外觀服務通常是在周邊網路中 (也就是非警戒區域和遮蔽式子網路)，並會與實作商務邏輯並可存取內部資料的後端服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="4fed9-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="4fed9-106">外觀服務和後端服務之間的通訊通道會經過防火牆，而且其目的通常僅限一項。</span><span class="sxs-lookup"><span data-stu-id="4fed9-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="4fed9-107">本範例由以下元件組成：</span><span class="sxs-lookup"><span data-stu-id="4fed9-107">This sample consists of the following components:</span></span>  
  
-   <span data-ttu-id="4fed9-108">計算機用戶端</span><span class="sxs-lookup"><span data-stu-id="4fed9-108">Calculator client</span></span>  
  
-   <span data-ttu-id="4fed9-109">計算機外觀服務</span><span class="sxs-lookup"><span data-stu-id="4fed9-109">Calculator façade service</span></span>  
  
-   <span data-ttu-id="4fed9-110">計算機後端服務</span><span class="sxs-lookup"><span data-stu-id="4fed9-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="4fed9-111">外觀服務主要負責驗證要求及呼叫者。</span><span class="sxs-lookup"><span data-stu-id="4fed9-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="4fed9-112">在成功驗證之後，會使用周邊網路到內部網路之間的控制式通訊通道，將要求轉遞至後端服務。</span><span class="sxs-lookup"><span data-stu-id="4fed9-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="4fed9-113">做為轉遞要求的一部分，外觀服務會包含呼叫者身分識別的相關資訊，讓後端服務可以用此資訊進行處理。</span><span class="sxs-lookup"><span data-stu-id="4fed9-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="4fed9-114">將使用訊息 `Username` 標頭內的 `Security` 安全性權杖來傳輸呼叫者身分識別。</span><span class="sxs-lookup"><span data-stu-id="4fed9-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="4fed9-115">範例會使用 WCF 安全性基礎結構來傳輸及擷取這項資訊從`Security`標頭。</span><span class="sxs-lookup"><span data-stu-id="4fed9-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fed9-116">後端服務會信任外觀服務以驗證呼叫者。</span><span class="sxs-lookup"><span data-stu-id="4fed9-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="4fed9-117">因此，後端服務不會再次驗證呼叫者，而是會在轉遞要求中使用外觀服務提供的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="4fed9-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="4fed9-118">由於此信任關係，後端服務必須驗證外觀服務，確保轉遞的訊息是來自可信任的來源，在此例中也就是指外觀服務。</span><span class="sxs-lookup"><span data-stu-id="4fed9-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="4fed9-119">實作</span><span class="sxs-lookup"><span data-stu-id="4fed9-119">Implementation</span></span>  
 <span data-ttu-id="4fed9-120">在本範例中有兩個通訊路徑。</span><span class="sxs-lookup"><span data-stu-id="4fed9-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="4fed9-121">第一個是在用戶端和外觀服務之間，第二個則是在外觀服務和後端服務之間。</span><span class="sxs-lookup"><span data-stu-id="4fed9-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="4fed9-122">用戶端和外觀服務之間的通訊路徑</span><span class="sxs-lookup"><span data-stu-id="4fed9-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="4fed9-123">用戶端到外觀服務的通訊路徑會搭配使用 `wsHttpBinding` 和 `UserName` 用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="4fed9-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="4fed9-124">這表示用戶端透過使用者名稱和密碼來驗證外觀服務，而外觀服務使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="4fed9-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="4fed9-125">繫結組態如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4fed9-125">The binding configuration looks like the following example.</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="4fed9-126">外觀服務會使用自訂 `UserNamePasswordValidator` 實作驗證呼叫者。</span><span class="sxs-lookup"><span data-stu-id="4fed9-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="4fed9-127">針對示範用途，驗證時只會確定呼叫者的使用者名稱和呈現的密碼相符。</span><span class="sxs-lookup"><span data-stu-id="4fed9-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="4fed9-128">在實際狀況中，可能會使用 Active Directory 或自訂 ASP.NET 成員資格提供者來驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="4fed9-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="4fed9-129">驗證器實作是在 `FacadeService.cs` 檔案中。</span><span class="sxs-lookup"><span data-stu-id="4fed9-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="4fed9-130">已將自訂驗證器設定為在外觀服務組態檔的 `serviceCredentials` 行為內使用。</span><span class="sxs-lookup"><span data-stu-id="4fed9-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="4fed9-131">這個行為也可用來設定服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="4fed9-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate   
               findValue="localhost"   
               storeLocation="LocalMachine"   
               storeName="My"   
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="4fed9-132">外觀服務和後端服務之間的通訊路徑</span><span class="sxs-lookup"><span data-stu-id="4fed9-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="4fed9-133">外觀服務到後端服務的通訊路徑會使用由數個繫結項目組成的 `customBinding` 。</span><span class="sxs-lookup"><span data-stu-id="4fed9-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="4fed9-134">此繫結會完成兩個動作。</span><span class="sxs-lookup"><span data-stu-id="4fed9-134">This binding accomplishes two things.</span></span> <span data-ttu-id="4fed9-135">第一，會驗證外觀服務和後端服務，確保通訊為安全而且是來自可信任的來源。</span><span class="sxs-lookup"><span data-stu-id="4fed9-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="4fed9-136">第二，也會傳輸 `Username` 安全性權杖內部的初始呼叫者身分識別。</span><span class="sxs-lookup"><span data-stu-id="4fed9-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="4fed9-137">在此情況下，只有初始呼叫者的使用者名稱會傳輸至後端服務，而訊息中不含密碼。</span><span class="sxs-lookup"><span data-stu-id="4fed9-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="4fed9-138">這是因為後端服務信任外觀服務，以在轉遞要求至呼叫者之前先驗證呼叫者。</span><span class="sxs-lookup"><span data-stu-id="4fed9-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="4fed9-139">由於外觀服務會對後端服務進行自我驗證，後端服務便會信任轉遞之要求中所含的資訊。</span><span class="sxs-lookup"><span data-stu-id="4fed9-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="4fed9-140">下列為此通訊路徑的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="4fed9-140">The following is the binding configuration for this communication path.</span></span>  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="4fed9-141">[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)繫結項目會處理初始呼叫者的使用者名稱傳輸和擷取。</span><span class="sxs-lookup"><span data-stu-id="4fed9-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="4fed9-142">[ \<Windowsstreamsecurity 正在 >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)和[ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)負責驗證外觀和後端服務以及訊息保護。</span><span class="sxs-lookup"><span data-stu-id="4fed9-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="4fed9-143">若要轉遞要求，外觀服務實作必須提供初始呼叫者的使用者名稱，讓該 WCF 安全性基礎結構，可將此放置轉遞的訊息。</span><span class="sxs-lookup"><span data-stu-id="4fed9-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="4fed9-144">會在外觀服務實作中提供初始呼叫者的使用者名稱，方法是在用戶端 Proxy 執行個體 (外觀服務用此執行個體與後端服務通訊) 上的 `ClientCredentials` 屬性設定即可。</span><span class="sxs-lookup"><span data-stu-id="4fed9-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="4fed9-145">下列程式碼會顯示如何在外觀服務上實作 `GetCallerIdentity` 方法。</span><span class="sxs-lookup"><span data-stu-id="4fed9-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="4fed9-146">其他方法也使用相同的模式。</span><span class="sxs-lookup"><span data-stu-id="4fed9-146">Other methods use the same pattern.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="4fed9-147">如前面程式碼所示，不會在 `ClientCredentials` 屬性中設定密碼，而只會設定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4fed9-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="4fed9-148">WCF 安全性基礎結構會建立沒有密碼的使用者名稱安全性權杖在此情況下，而這正是在此案例中所需。</span><span class="sxs-lookup"><span data-stu-id="4fed9-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="4fed9-149">在後端服務上，必須驗證使用者名稱安全性權杖中所含的資訊。</span><span class="sxs-lookup"><span data-stu-id="4fed9-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="4fed9-150">根據預設，WCF 安全性會嘗試將使用者對應至 Windows 帳戶，使用提供的密碼。</span><span class="sxs-lookup"><span data-stu-id="4fed9-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="4fed9-151">在此情況下，將不會提供密碼，而且驗證使用者名稱也不需要後端服務，這是因為外觀服務已經執行驗證了。</span><span class="sxs-lookup"><span data-stu-id="4fed9-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="4fed9-152">若要實作這項功能在 WCF 中，自訂`UserNamePasswordValidator`提供它只會強制使用者名稱權杖中指定，並不會執行任何額外的驗證。</span><span class="sxs-lookup"><span data-stu-id="4fed9-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,   
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the   
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new   
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="4fed9-153">已將自訂驗證器設定為在外觀服務組態檔的 `serviceCredentials` 行為內使用。</span><span class="sxs-lookup"><span data-stu-id="4fed9-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,   
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="4fed9-154">若要擷取使用者名稱資訊以及與信任的外觀服務帳戶相關的資訊，後端服務實作會使用 `ServiceSecurityContext` 類別。</span><span class="sxs-lookup"><span data-stu-id="4fed9-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="4fed9-155">下列程式碼會顯示如何實作 `GetCallerIdentity` 方法。</span><span class="sxs-lookup"><span data-stu-id="4fed9-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =   
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on   
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in   
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets   
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in   
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&   
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject   
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 <span data-ttu-id="4fed9-156">使用 `ServiceSecurityContext.Current.WindowsIdentity` 屬性擷取外觀服務的帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="4fed9-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="4fed9-157">若要存取初始呼叫者的相關資訊，後端服務會使用 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` 屬性。</span><span class="sxs-lookup"><span data-stu-id="4fed9-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="4fed9-158">這個屬性會查詢型別為 `Identity` 的 `Name`宣告。</span><span class="sxs-lookup"><span data-stu-id="4fed9-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="4fed9-159">這個宣告會由 WCF 安全性基礎結構中包含的資訊從自動產生`Username`安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="4fed9-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="4fed9-160">執行範例</span><span class="sxs-lookup"><span data-stu-id="4fed9-160">Running the sample</span></span>  
 <span data-ttu-id="4fed9-161">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="4fed9-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4fed9-162">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="4fed9-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="4fed9-163">您可以在外觀和後端服務的主控台視窗中按 ENTER 鍵，即可關閉服務。</span><span class="sxs-lookup"><span data-stu-id="4fed9-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4fed9-164">信任的外觀案例範例所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要憑證安全性的外觀服務並對用戶端自我驗證。</span><span class="sxs-lookup"><span data-stu-id="4fed9-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="4fed9-165">如需詳細資訊，請參閱本主題結尾的安裝程序。</span><span class="sxs-lookup"><span data-stu-id="4fed9-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="4fed9-166">下面會提供批次檔之不同區段的簡短概觀。</span><span class="sxs-lookup"><span data-stu-id="4fed9-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="4fed9-167">建立伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="4fed9-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="4fed9-168">下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="4fed9-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="4fed9-169">`%SERVER_NAME%` 變數會指定伺服器名稱，預設值為 localhost。</span><span class="sxs-lookup"><span data-stu-id="4fed9-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="4fed9-170">憑證是儲存在 LocalMachine 存放區中。</span><span class="sxs-lookup"><span data-stu-id="4fed9-170">The certificate is stored in the LocalMachine store.</span></span>  
  
-   <span data-ttu-id="4fed9-171">將外觀服務的憑證安裝至用戶端信任的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="4fed9-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="4fed9-172">下列程式行會將外觀服務的憑證複製到用戶端受信任人的存放區中。</span><span class="sxs-lookup"><span data-stu-id="4fed9-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="4fed9-173">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="4fed9-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4fed9-174">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證的步驟。</span><span class="sxs-lookup"><span data-stu-id="4fed9-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4fed9-175">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="4fed9-175">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4fed9-176">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4fed9-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4fed9-177">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="4fed9-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="4fed9-178">若要在同一部機器上執行範例</span><span class="sxs-lookup"><span data-stu-id="4fed9-178">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="4fed9-179">確定路徑中包含 Makecert.exe 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4fed9-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="4fed9-180">從範例安裝資料夾執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="4fed9-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="4fed9-181">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="4fed9-181">This installs all the certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="4fed9-182">從不同主控台視窗中的 \BackendService\bin 目錄啟動 BackendService.exe</span><span class="sxs-lookup"><span data-stu-id="4fed9-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4.  <span data-ttu-id="4fed9-183">從不同主控台視窗中的 \FacadeService\bin 目錄啟動 FacadeService.exe</span><span class="sxs-lookup"><span data-stu-id="4fed9-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5.  <span data-ttu-id="4fed9-184">從 \client\bin 啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="4fed9-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="4fed9-185">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="4fed9-185">Client activity is displayed on the client console application.</span></span>  
  
6.  <span data-ttu-id="4fed9-186">如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="4fed9-186">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4fed9-187">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="4fed9-187">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="4fed9-188">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="4fed9-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fed9-189">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4fed9-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4fed9-190">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4fed9-190">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4fed9-191">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="4fed9-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4fed9-192">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4fed9-192">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a><span data-ttu-id="4fed9-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fed9-193">See Also</span></span>
