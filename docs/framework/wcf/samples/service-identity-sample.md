---
title: 服務身分識別範例
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 999e05918eb7ac852336136a1e7512a2e9d7b9db
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964542"
---
# <a name="service-identity-sample"></a><span data-ttu-id="70470-102">服務身分識別範例</span><span class="sxs-lookup"><span data-stu-id="70470-102">Service Identity Sample</span></span>
<span data-ttu-id="70470-103">這個服務身分識別範例示範如何設定服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="70470-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="70470-104">在設計階段，用戶端可以使用服務的中繼資料擷取身分識別，然後在執行階段，用戶端就可以驗證服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="70470-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="70470-105">服務身分識別的概念主要是允許用戶端在呼叫任何作業之前驗證服務，從而保護用戶端以免遭到未經驗證的呼叫。</span><span class="sxs-lookup"><span data-stu-id="70470-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="70470-106">在安全連線上，服務還會在允許用戶端存取之前驗證其認證，但這不是本範例的重點。</span><span class="sxs-lookup"><span data-stu-id="70470-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="70470-107">請參閱[用戶端](../../../../docs/framework/wcf/samples/client.md)中顯示伺服器驗證的範例。</span><span class="sxs-lookup"><span data-stu-id="70470-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="70470-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="70470-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="70470-109">這個範例說明下列功能：</span><span class="sxs-lookup"><span data-stu-id="70470-109">This sample illustrates the following features:</span></span>

- <span data-ttu-id="70470-110">如何在服務的不同端點上設定不同類型的身分識別。</span><span class="sxs-lookup"><span data-stu-id="70470-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="70470-111">每個身分識別類型各有不同的功能。</span><span class="sxs-lookup"><span data-stu-id="70470-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="70470-112">要使用的身分識別類型取決於端點繫結上使用的安全性認證類型。</span><span class="sxs-lookup"><span data-stu-id="70470-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>

- <span data-ttu-id="70470-113">身分識別可在組態中以宣告方式設定，或是在程式碼中以命令方式指定。</span><span class="sxs-lookup"><span data-stu-id="70470-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="70470-114">對於用戶端和服務，通常都應該使用組態來設定身分識別。</span><span class="sxs-lookup"><span data-stu-id="70470-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>

- <span data-ttu-id="70470-115">如何在用戶端設定自訂身分識別。</span><span class="sxs-lookup"><span data-stu-id="70470-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="70470-116">自訂身分識別通常是對身分識別現有類型進行的自訂，這可讓用戶端檢查服務認證中提供的其他宣告資訊，以便在呼叫服務之前做出授權決策。</span><span class="sxs-lookup"><span data-stu-id="70470-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="70470-117">這個範例會檢查特定憑證的身分識別 (名為 identity.com) 以及此憑證內含的 RSA 金鑰。</span><span class="sxs-lookup"><span data-stu-id="70470-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="70470-118">在用戶端的組態中使用憑證和 RSA 身分識別類型時，取得這些值的簡易方式是檢查這些值序列化所在之處的服務 WSDL。</span><span class="sxs-lookup"><span data-stu-id="70470-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>

 <span data-ttu-id="70470-119">下列範例程式碼示範如何使用 WSHttpBinding，透過憑證的「網域名稱伺服器」(DNS) 來設定服務端點的身分識別。</span><span class="sxs-lookup"><span data-stu-id="70470-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 <span data-ttu-id="70470-120">身分識別也可以在 App.config 檔的組態中指定。</span><span class="sxs-lookup"><span data-stu-id="70470-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="70470-121">下列範例示範如何設定服務端點的 UPN (使用者主體名稱) 身分識別。</span><span class="sxs-lookup"><span data-stu-id="70470-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>

```xml
<endpoint address="upnidentity"
        behaviorConfiguration=""
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_Windows"
        name="WSHttpBinding_ICalculator_Windows"
        contract="Microsoft.ServiceModel.Samples.ICalculator">
  <!-- Set the UPN identity for this endpoint -->
  <identity>
      <userPrincipalName value="host\myservice.com" />
  </identity >
</endpoint>
```

 <span data-ttu-id="70470-122">透過從 <xref:System.ServiceModel.EndpointIdentity> 和 <xref:System.ServiceModel.Security.IdentityVerifier> 類別衍生的方式，可以在用戶端上設定自訂身分識別。</span><span class="sxs-lookup"><span data-stu-id="70470-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="70470-123">在概念上，可以將 <xref:System.ServiceModel.Security.IdentityVerifier> 類別視為服務之 `AuthorizationManager` 類別的用戶端對等類別。</span><span class="sxs-lookup"><span data-stu-id="70470-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="70470-124">下列程式碼範例示範 `OrgEndpointIdentity` 的實作，它會在伺服器憑證的主體名稱中儲存要符合的組織名稱。</span><span class="sxs-lookup"><span data-stu-id="70470-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="70470-125">在 `CheckAccess` 類別上的 `CustomIdentityVerifier` 方法中，會針對組織名稱進行授權檢查。</span><span class="sxs-lookup"><span data-stu-id="70470-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>

```csharp
// This custom EndpointIdentity stores an organization name
public class OrgEndpointIdentity : EndpointIdentity
{
    private string orgClaim;
    public OrgEndpointIdentity(string orgName)
    {
        orgClaim = orgName;
    }
    public string OrganizationClaim
    {
        get { return orgClaim; }
        set { orgClaim = value; }
    }
}

//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to
//check that X.509 certificate's distinguished name claim contains
//the organization name e.g. the string value "O=Contoso"
class CustomIdentityVerifier : IdentityVerifier
{
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)
    {
        bool returnvalue = false;
        foreach (ClaimSet claimset in authContext.ClaimSets)
        {
            foreach (Claim claim in claimset)
            {
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")
                {
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))
                    {
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);
                        Console.WriteLine("Right: {0}", claim.Right);
                        Console.WriteLine("Resource: {0}",claim.Resource);
                        Console.WriteLine();
                        returnvalue = true;
                    }
                }
            }
        }
        return returnvalue;
    }
}
```

 <span data-ttu-id="70470-126">這個範例會使用名為 identity.com 的憑證，其位於語言特定的身分識別方案資料夾中。</span><span class="sxs-lookup"><span data-stu-id="70470-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="70470-127">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="70470-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="70470-128">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="70470-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="70470-129">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="70470-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="70470-130">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="70470-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="70470-131">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="70470-131">To run the sample on the same computer</span></span>

1. <span data-ttu-id="70470-132">在 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 或 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，使用 MMC 嵌入式管理單元工具，將身分識別方案資料夾中的 Identity.pfx 憑證檔匯入至 LocalMachine/My (Personal) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="70470-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="70470-133">這個檔案有密碼保護。</span><span class="sxs-lookup"><span data-stu-id="70470-133">This file is password protected.</span></span> <span data-ttu-id="70470-134">它會在匯入時要求您提供密碼。</span><span class="sxs-lookup"><span data-stu-id="70470-134">During the import you are asked for a password.</span></span> <span data-ttu-id="70470-135">在`xyz` [密碼] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="70470-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="70470-136">如需詳細資訊，請參閱[如何：使用 MMC 嵌入式管理](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)單元主題來查看憑證。</span><span class="sxs-lookup"><span data-stu-id="70470-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="70470-137">完成後, 請以系統管理員許可權在 Visual Studio 的開發人員命令提示字元中執行安裝程式, 這會將此憑證複製到 CurrentUser/Trusted 人脈存放區, 以供用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="70470-137">Once this is done, run Setup.bat in a Developer Command Prompt for Visual Studio with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>

2. <span data-ttu-id="70470-138">在[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]上, 使用系統管理員許可權在 Visual Studio 2012 命令提示字元內的範例安裝資料夾中執行安裝程式 .bat。</span><span class="sxs-lookup"><span data-stu-id="70470-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt with administrator privileges.</span></span> <span data-ttu-id="70470-139">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="70470-139">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="70470-140">安裝 .bat 批次檔是設計用來從 Visual Studio 2012 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="70470-140">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="70470-141">在 Visual Studio 2012 命令提示字元中設定的 PATH 環境變數會指向包含安裝程式 .bat 腳本所需之可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="70470-141">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="70470-142">當您完成範例時，請務必執行 Cleanup.bat 以移除憑證。</span><span class="sxs-lookup"><span data-stu-id="70470-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="70470-143">其他安全性範例使用相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="70470-143">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="70470-144">從 \service\bin 目錄啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="70470-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="70470-145">確定服務指出它已準備就緒, 並顯示按\<下 enter > 終止服務的提示。</span><span class="sxs-lookup"><span data-stu-id="70470-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4. <span data-ttu-id="70470-146">從 \client\bin 目錄啟動 Client.exe，或是在 Visual Studio 中按下 F5 鍵來建置並執行。</span><span class="sxs-lookup"><span data-stu-id="70470-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="70470-147">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="70470-147">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="70470-148">如果用戶端和服務無法通訊, 請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="70470-148">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="70470-149">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="70470-149">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="70470-150">建置範例的用戶端部分之前，請務必在 Client.cs 檔案內的 `CallServiceCustomClientIdentity` 方法中變更服務端點位址的值，</span><span class="sxs-lookup"><span data-stu-id="70470-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="70470-151">然後才建置範例。</span><span class="sxs-lookup"><span data-stu-id="70470-151">Then build the sample.</span></span>  
  
2. <span data-ttu-id="70470-152">在服務電腦上建立目錄。</span><span class="sxs-lookup"><span data-stu-id="70470-152">Create a directory on the service computer.</span></span>  
  
3. <span data-ttu-id="70470-153">將服務程式檔從 service\bin 複製到服務電腦上的目錄。</span><span class="sxs-lookup"><span data-stu-id="70470-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="70470-154">同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="70470-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4. <span data-ttu-id="70470-155">在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="70470-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5. <span data-ttu-id="70470-156">將用戶端程式檔複製到用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="70470-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="70470-157">同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。</span><span class="sxs-lookup"><span data-stu-id="70470-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6. <span data-ttu-id="70470-158">在服務上, 于`setup.bat service`使用系統管理員許可權開啟 Visual Studio 的開發人員命令提示字元中執行。</span><span class="sxs-lookup"><span data-stu-id="70470-158">On the service, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="70470-159">`setup.bat` 使用引數執行時,會建立具有電腦完整功能變數名稱的服務憑證,並將服務憑證匯出至名`service`為 .cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="70470-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7. <span data-ttu-id="70470-160">從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="70470-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="70470-161">在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="70470-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="70470-162">其中會有多個必須加以變更的執行個體。</span><span class="sxs-lookup"><span data-stu-id="70470-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="70470-163">在用戶端上, 于 Visual Studio 以系統管理員許可權開啟的開發人員命令提示字元中執行 Importservicecert.bat。</span><span class="sxs-lookup"><span data-stu-id="70470-163">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="70470-164">這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="70470-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="70470-165">在服務電腦上，從命令提示字元啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="70470-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="70470-166">在用戶端電腦上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="70470-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="70470-167">如果用戶端和服務無法通訊, 請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="70470-167">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="70470-168">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="70470-168">To clean up after the sample</span></span>  
  
- <span data-ttu-id="70470-169">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="70470-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70470-170">跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="70470-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="70470-171">如果您已在電腦上執行使用憑證的 Windows Communication Foundation (WCF) 範例, 請務必清除已安裝在 CurrentUser-TrustedPeople 存放區中的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="70470-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="70470-172">若要這麼做, 請使用下列命令:`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`例如: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="70470-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
