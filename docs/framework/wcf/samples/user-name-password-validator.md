---
title: "使用者名稱密碼驗證程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 627670c989510bd82e4d9b6aa7550476be1ce750
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="user-name-password-validator"></a><span data-ttu-id="93931-102">使用者名稱密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="93931-102">User Name Password Validator</span></span>
<span data-ttu-id="93931-103">這個範例會示範如何實作自訂的 UserNamePassword 驗證程式。</span><span class="sxs-lookup"><span data-stu-id="93931-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="93931-104">當內建 UserNamePassword 驗證模式都不符合應用程式需求時，這個驗證程式就很有用；例如，當使用者名稱/密碼組儲存在某些外部存放區時，例如資料庫中。</span><span class="sxs-lookup"><span data-stu-id="93931-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="93931-105">這個範例示範的服務具有可檢查兩組特定使用者名稱/密碼組的自訂驗證程式。</span><span class="sxs-lookup"><span data-stu-id="93931-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="93931-106">用戶端會使用這些使用者名稱/密碼組來向服務驗證。</span><span class="sxs-lookup"><span data-stu-id="93931-106">The client uses such a username/password pair to authenticate to the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93931-107">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="93931-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="93931-108">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="93931-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="93931-109">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="93931-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93931-110">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="93931-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  <span data-ttu-id="93931-111">因為任何人都可以建構使用自訂驗證程式能接受之使用者名稱/密碼組的使用者名稱認證，所以服務的安全性會低於標準 UserNamePassword 驗證程式提供之預設行為的安全性。</span><span class="sxs-lookup"><span data-stu-id="93931-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="93931-112">標準 UserNamePassword 驗證程式會嘗試將提供的使用者名稱/密碼組對應至 Windows 帳戶，並在這個對應失敗時發生驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="93931-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="93931-113">這個範例中的自訂 UserNamePassword 驗證程式「不得」用於實際執行程式碼 (Production Code) 中，這個驗證程式僅供說明用途。</span><span class="sxs-lookup"><span data-stu-id="93931-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>  
  
 <span data-ttu-id="93931-114">這個範例所示範的作業摘要如下：</span><span class="sxs-lookup"><span data-stu-id="93931-114">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="93931-115">用戶端可以透過使用者名稱權杖進行驗證。</span><span class="sxs-lookup"><span data-stu-id="93931-115">The client can be authenticated using a Username Token.</span></span>  
  
-   <span data-ttu-id="93931-116">伺服器會向自訂 UserNamePasswordValidator 驗證用戶端的認證，以及如何將使用者名稱與密碼驗證邏輯的自訂錯誤傳播至用戶端。</span><span class="sxs-lookup"><span data-stu-id="93931-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>  
  
-   <span data-ttu-id="93931-117">伺服器是使用該伺服器的 X.509 憑證來驗證的。</span><span class="sxs-lookup"><span data-stu-id="93931-117">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="93931-118">服務會公開 (Expose) 單一的端點來與已使用組態檔 App.config 定義之服務進行通訊。端點是由位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="93931-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="93931-119">繫結設定的標準`wsHttpBinding`經由預設使用 WS Securityand 使用者名稱驗證。</span><span class="sxs-lookup"><span data-stu-id="93931-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Securityand username authentication.</span></span> <span data-ttu-id="93931-120">服務行為會指定 `Custom` 模式，以驗證用戶端使用者名稱/密碼組以及該驗證程式類別的類型。</span><span class="sxs-lookup"><span data-stu-id="93931-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="93931-121">行為也會使用 `serviceCertificate` 項目來指定伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="93931-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="93931-122">伺服器憑證必須包含相同值的`SubjectName`為`findValue`中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="93931-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <!-- use host/baseAddresses to configure base address provided by host -->  
      <host>  
        <baseAddresses>  
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />  
        </baseAddresses>  
      </host>  
      <!-- use base address specified above, provide one endpoint -->  
      <endpoint address="username"  
                binding="wsHttpBinding"  
                bindingConfiguration="Binding"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- username binding -->  
      <binding name="Binding">  
        <security mode="Message">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceDebug includeExceptionDetailInFaults ="true"/>  
        <serviceCredentials>  
          <!--   
          The serviceCredentials behavior allows one to   
          specify a custom validator for username/password  
          combinations.  
          -->  
          <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />  
          <!--   
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="93931-123">用戶端的端點組態是由組態名稱、服務端點的絕對位址、繫結和合約所組成。</span><span class="sxs-lookup"><span data-stu-id="93931-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="93931-124">用戶端繫結已設定了適當的模式與訊息 `clientCredentialType`。</span><span class="sxs-lookup"><span data-stu-id="93931-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- Username based endpoint -->  
      <endpoint name="Username"  
address="http://localhost:8001/servicemodelsamples/service/username"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- Username binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="93931-125">用戶端實作會提示使用者輸入使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="93931-125">The client implementation prompts the user to enter a username and password.</span></span>  
  
```  
// Get the username and password  
Console.WriteLine("Username authentication required.");  
Console.WriteLine("Provide a username.");  
Console.WriteLine("   Enter username: (test1)");  
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
            password = password.Substring(0, password.Length - 1);  
        }  
        info = Console.ReadKey(true);  
    }  
}  
for (int i = 0; i < password.Length; i++)  
{  
    Console.Write("*");  
}  
Console.WriteLine();  
// Create a proxy with Certificate endpoint configuration  
CalculatorProxy proxy = new CalculatorProxy("Username")  
try  
{  
  proxy.ClientCredentials.Username.Username = username;  
  proxy.ClientCredentials.Username.Password = password;  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = proxy.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  }  
  catch (Exception e)  
  {  
      Console.WriteLine("Call failed:");  
      while (e != null)  
      {  
          Console.WriteLine("\t{0}", e.Message);  
          e = e.InnerException;  
      }  
      proxy.Abort();  
  }  
}  
```  
  
 <span data-ttu-id="93931-126">這個範例會使用自訂 UserNamePasswordValidator 來驗證使用者名稱/密碼組。</span><span class="sxs-lookup"><span data-stu-id="93931-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="93931-127">此範例會實作衍生自 `CustomUserNamePasswordValidator` 的 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>。</span><span class="sxs-lookup"><span data-stu-id="93931-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="93931-128">如需詳細資訊，請參閱有關 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的文件。</span><span class="sxs-lookup"><span data-stu-id="93931-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="93931-129">這個特定自訂驗證程式範例會實作 `Validate` 方法，以接受兩組特定使用者名稱/密碼組，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="93931-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>  
  
```  
public class CustomUserNameValidator : UserNamePasswordValidator  
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
   throw new FaultException("Unknown Username or Incorrect Password");  
   }  
  }  
 }  
```  
  
 <span data-ttu-id="93931-130">一旦驗證程式在服務程式碼中實作，服務主機就必須收到要使用的驗證程式執行個體的相關通知。</span><span class="sxs-lookup"><span data-stu-id="93931-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="93931-131">這個動作是使用下列程式碼完成。</span><span class="sxs-lookup"><span data-stu-id="93931-131">This is done using the following code.</span></span>  
  
```  
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();  
```  
  
 <span data-ttu-id="93931-132">或者，您可以在組態中執行如下所示的動作。</span><span class="sxs-lookup"><span data-stu-id="93931-132">Or you can do the same thing in configuration as follows.</span></span>  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="CalculatorServiceBehavior">  
  ...  
   <serviceCredentials>  
    <!--   
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.  
    -->  
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="93931-133">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="93931-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="93931-134">用戶端應該會成功呼叫所有方法。</span><span class="sxs-lookup"><span data-stu-id="93931-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="93931-135">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="93931-135">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="93931-136">設定批次檔</span><span class="sxs-lookup"><span data-stu-id="93931-136">Setup Batch File</span></span>  
 <span data-ttu-id="93931-137">本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="93931-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="93931-138">這個批次檔必須經過修改才能跨機器運作，或在非自動裝載的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="93931-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>  
  
 <span data-ttu-id="93931-139">下面提供批次檔的各區段簡要概觀，讓將批次檔得以修改為在適當的組態下執行。</span><span class="sxs-lookup"><span data-stu-id="93931-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="93931-140">建立伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="93931-140">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="93931-141">下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="93931-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="93931-142">%SERVER_NAME% 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="93931-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="93931-143">您可以變更這個變數來指定自己的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="93931-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="93931-144">預設值為 localhost。</span><span class="sxs-lookup"><span data-stu-id="93931-144">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="93931-145">將伺服器憑證安裝至用戶端的受信任憑證存放區中：</span><span class="sxs-lookup"><span data-stu-id="93931-145">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="93931-146">Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="93931-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="93931-147">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="93931-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="93931-148">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。</span><span class="sxs-lookup"><span data-stu-id="93931-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="93931-149">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="93931-149">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="93931-150">若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="93931-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="93931-151">若要在單一或跨電腦的組態中執行本範例，請使用下列指示。</span><span class="sxs-lookup"><span data-stu-id="93931-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="93931-152">若要在同一部機器上執行範例</span><span class="sxs-lookup"><span data-stu-id="93931-152">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="93931-153">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元內部，執行範例安裝資料夾中的 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="93931-153">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt.</span></span> <span data-ttu-id="93931-154">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="93931-154">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93931-155">Setup.bat 批次檔是設計用來從 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="93931-155">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="93931-156">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元中設定的 PATH 環境變數會指向包含 Setup.bat 指令碼所需之可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="93931-156">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="93931-157">從 service\bin 啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="93931-157">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="93931-158">從 \client\bin 啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="93931-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="93931-159">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="93931-159">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="93931-160">如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="93931-160">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="93931-161">若要跨機器執行範例</span><span class="sxs-lookup"><span data-stu-id="93931-161">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="93931-162">在服務機器上為服務二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="93931-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="93931-163">將服務程式檔複製到服務機器的服務目錄上。</span><span class="sxs-lookup"><span data-stu-id="93931-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="93931-164">同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務機器中。</span><span class="sxs-lookup"><span data-stu-id="93931-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="93931-165">您伺服器憑證的主體名稱必須包含機器的完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="93931-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="93931-166">伺服器的組態檔必須更新以反映這個新憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="93931-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4.  <span data-ttu-id="93931-167">將伺服器憑證複製到用戶端的 CurrentUser-TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="93931-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="93931-168">只有在伺服器憑證不是由受信任的簽發者發行時才需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="93931-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="93931-169">在服務機器的 App.config 檔中變更基底位址的值，以指定完整機器名稱而不要指定 localhost。</span><span class="sxs-lookup"><span data-stu-id="93931-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="93931-170">在服務機器上，從命令提示視窗啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="93931-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7.  <span data-ttu-id="93931-171">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端機器中。</span><span class="sxs-lookup"><span data-stu-id="93931-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8.  <span data-ttu-id="93931-172">在用戶端機器上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="93931-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="93931-173">在用戶端機器上，從命令提示字元視窗啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="93931-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="93931-174">如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="93931-174">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="93931-175">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="93931-175">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="93931-176">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="93931-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="93931-177">這樣會從憑證存放區中移除伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="93931-177">This removes the server certificate from the certificate store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93931-178">請參閱</span><span class="sxs-lookup"><span data-stu-id="93931-178">See Also</span></span>
