---
title: 訊息安全性使用者名稱
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 11cf225ca30117484cdc3bbcb6910e615e91f5ef
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423130"
---
# <a name="message-security-user-name"></a><span data-ttu-id="5c8e8-102">訊息安全性使用者名稱</span><span class="sxs-lookup"><span data-stu-id="5c8e8-102">Message Security User Name</span></span>
<span data-ttu-id="5c8e8-103">這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配使用者名稱驗證的 WS-Security，並要求使用伺服器之 X.509v3 憑證進行驗證的伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="5c8e8-104">用戶端與伺服器之間的所有應用程式訊息都會經過簽署及加密。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="5c8e8-105">根據預設，用戶端提供的使用者名稱與密碼會用來登入有效的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="5c8e8-106">此樣本根據[WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="5c8e8-107">這個範例是由用戶端主控台程式 (Client.exe) 和網際網路資訊服務 (IIS) 所裝載的服務程式庫 (Service.dll) 所組成。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="5c8e8-108">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c8e8-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5c8e8-110">這個範例也會示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="5c8e8-110">This sample also demonstrates:</span></span>  
  
-   <span data-ttu-id="5c8e8-111">預設的 Windows 帳戶對應，所以能夠執行額外的授權。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
-   <span data-ttu-id="5c8e8-112">如何從服務程式碼存取呼叫者的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="5c8e8-113">服務會公開 (Expose) 單一的端點來與已使用組態檔 Web.config 定義之服務進行通訊。端點是由位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="5c8e8-114">繫結設定的標準[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)，預設為使用訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="5c8e8-115">這個範例會設定標準[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)使用用戶端使用者名稱驗證。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="5c8e8-116">此行為會指定用來進行服務驗證的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="5c8e8-117">伺服器憑證必須包含相同的值做為主體名稱`findValue`屬性中[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5c8e8-118">用戶端端點組態是由服務端點的絕對位址、繫結及合約所組成。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="5c8e8-119">用戶端繫結是透過適當的 `securityMode` 和 `authenticationMode` 所設定。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="5c8e8-120">在跨電腦案例中執行時，服務端點位址必須隨同變更。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5c8e8-121">用戶端實作會設定要使用的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-121">The client implementation sets the user name and password to use.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 <span data-ttu-id="5c8e8-122">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5c8e8-123">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="5c8e8-124">訊息安全性範例所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要憑證安全性的裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="5c8e8-125">此批次檔可以在兩種模式中執行。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="5c8e8-126">若要在單一電腦模式中執行此批次檔，請在命令列中輸入 `setup.bat`。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="5c8e8-127">若要在服務模式中執行此批次檔，請輸入 `setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="5c8e8-128">您可以在跨電腦執行範例時使用這個模式。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="5c8e8-129">如需詳細資訊，請參閱本主題結尾的安裝程序。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="5c8e8-130">下面會提供批次檔之不同區段的簡短概觀。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="5c8e8-131">建立伺服器憑證</span><span class="sxs-lookup"><span data-stu-id="5c8e8-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="5c8e8-132">下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="5c8e8-133">%SERVER_NAME% 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="5c8e8-134">憑證是儲存在 LocalMachine 存放區中。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="5c8e8-135">如果使用 service 引數執行 Setup.bat 批次檔 (例如，`setup.bat service`)，%SERVER_NAME% 就會包含電腦的完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="5c8e8-136">否則，預設為 localhost。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-136">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="5c8e8-137">將伺服器憑證安裝至用戶端的受信任憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="5c8e8-138">下列程式行會將伺服器憑證複製到用戶端受信任人的存放區中。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="5c8e8-139">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="5c8e8-140">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證的步驟。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="5c8e8-141">授與憑證私密金鑰的權限</span><span class="sxs-lookup"><span data-stu-id="5c8e8-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="5c8e8-142">在 Setup.bat 批次檔中的下列程式行，會讓儲存在 LocalMachine 存放區的伺服器憑證可由 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 背景工作處理序帳戶存取。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5c8e8-143">如果您使用的是非美式英文版的 Windows，則必須編輯 Setup.bat 檔案，並以適用您所在地區的對等帳戶取代 `NT AUTHORITY\NETWORK SERVICE` 帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5c8e8-144">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5c8e8-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5c8e8-145">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5c8e8-146">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="5c8e8-147">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="5c8e8-147">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="5c8e8-148">確認路徑中包含 Makecert.exe 和 FindPrivateKey.exe 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="5c8e8-149">在使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行範例安裝資料夾中的 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-149">Run Setup.bat from the sample install folder in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="5c8e8-150">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c8e8-151">Setup.bat 批次檔是設計用來從 Visual Studio 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-151">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt.</span></span> <span data-ttu-id="5c8e8-152">它要求 path 環境變數指向安裝 SDK 的目錄。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="5c8e8-153">這個環境變數是自動在 Visual Studio 命令提示字元中設定。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-153">This environment variable is automatically set within a Visual Studio Command Prompt.</span></span>  
  
3.  <span data-ttu-id="5c8e8-154">驗證的存取權的服務使用瀏覽器輸入位址 http://localhost/servicemodelsamples/service.svc 。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-154">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="5c8e8-155">從 \client\bin 啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="5c8e8-156">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-156">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="5c8e8-157">如果用戶端和服務能夠進行通訊，請參閱[疑難排解祕訣](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-157">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5c8e8-158">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="5c8e8-158">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="5c8e8-159">在服務電腦上建立目錄。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-159">Create a directory on the service computer.</span></span> <span data-ttu-id="5c8e8-160">使用 Internet Information Services 管理工具，為這個目錄建立名為 servicemodelsamples 的虛擬應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2.  <span data-ttu-id="5c8e8-161">將 \inetpub\wwwroot\servicemodelsamples 中的服務程式檔複製至服務電腦上的虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="5c8e8-162">確定複製 \bin 子目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="5c8e8-163">同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="5c8e8-164">在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="5c8e8-165">將用戶端程式檔複製到用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="5c8e8-166">同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="5c8e8-167">在伺服器上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 `setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-167">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="5c8e8-168">執行`setup.bat`與`service`引數會建立具有電腦完整網域名稱的服務憑證，並將服務憑證匯出為名為 Service.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="5c8e8-169">編輯 Web.config 以反映新的憑證名稱 (在 serviceCertificate 項目的 findValue 屬性中)，這個名稱與電腦的完整網域名稱相同`.`</span><span class="sxs-lookup"><span data-stu-id="5c8e8-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7.  <span data-ttu-id="5c8e8-170">從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="5c8e8-171">在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="5c8e8-172">在用戶端上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-172">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="5c8e8-173">這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="5c8e8-174">在用戶端電腦上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="5c8e8-175">如果用戶端和服務能夠進行通訊，請參閱[疑難排解祕訣](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-175">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5c8e8-176">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="5c8e8-176">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="5c8e8-177">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c8e8-178">跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="5c8e8-179">如果您已執行跨電腦使用憑證的 Windows Communication Foundation (WCF) 範例，請務必清除已安裝在 CurrentUser-TrustedPeople 存放區的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="5c8e8-180">若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="5c8e8-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8e8-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c8e8-181">See Also</span></span>
