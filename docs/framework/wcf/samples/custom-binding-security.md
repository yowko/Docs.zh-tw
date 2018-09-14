---
title: 自訂繫結安全性
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 61e8be6f7f621340a684bff69ec5c9d64ab36c61
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45568471"
---
# <a name="custom-binding-security"></a><span data-ttu-id="b2add-102">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="b2add-102">Custom Binding Security</span></span>
<span data-ttu-id="b2add-103">這個範例會示範如何使用自訂繫結來設定安全性。</span><span class="sxs-lookup"><span data-stu-id="b2add-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="b2add-104">它會顯示如何使用自訂繫結同時啟用訊息層級安全性和安全傳輸。</span><span class="sxs-lookup"><span data-stu-id="b2add-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="b2add-105">當在用戶端和服務之間傳輸訊息需要安全傳輸，且同時必須保護訊息層級上訊息的安全時，這是相當有用的。</span><span class="sxs-lookup"><span data-stu-id="b2add-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="b2add-106">系統提供的繫結不支援這個組態。</span><span class="sxs-lookup"><span data-stu-id="b2add-106">This configuration is not supported by system-provided bindings.</span></span>  
  
 <span data-ttu-id="b2add-107">這個範例是由用戶端主控台程式 (EXE) 與服務主控台程式 (EXE) 所組成。</span><span class="sxs-lookup"><span data-stu-id="b2add-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="b2add-108">服務會實作雙工合約。</span><span class="sxs-lookup"><span data-stu-id="b2add-108">The service implements a duplex contract.</span></span> <span data-ttu-id="b2add-109">合約是由 `ICalculatorDuplex` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。</span><span class="sxs-lookup"><span data-stu-id="b2add-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="b2add-110">`ICalculatorDuplex` 介面允許用戶端執行數學運算，計算整個工作階段的執行結果。</span><span class="sxs-lookup"><span data-stu-id="b2add-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="b2add-111">服務可能會獨立地傳回 `ICalculatorDuplexCallback` 介面上的結果。</span><span class="sxs-lookup"><span data-stu-id="b2add-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="b2add-112">雙工合約需要一個工作階段，因為必須建立內容，將用戶端與服務之間傳送的訊息關聯在一起。</span><span class="sxs-lookup"><span data-stu-id="b2add-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="b2add-113">自訂繫結已定義成支援雙工通訊，而且具備安全性。</span><span class="sxs-lookup"><span data-stu-id="b2add-113">A custom binding is defined that supports duplex communication and is secure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2add-114">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="b2add-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b2add-115">服務組態會定義支援下列作業的自訂繫結：</span><span class="sxs-lookup"><span data-stu-id="b2add-115">The service configuration defines a custom binding that supports the following:</span></span>  
  
-   <span data-ttu-id="b2add-116">使用 TLS/SSL 通訊協定保護的 TCP 通訊。</span><span class="sxs-lookup"><span data-stu-id="b2add-116">TCP communication protected by using the TLS/SSL protocol.</span></span>  
  
-   <span data-ttu-id="b2add-117">Windows 訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="b2add-117">Windows message security.</span></span>  
  
 <span data-ttu-id="b2add-118">自訂繫結組態會同時啟用訊息層級安全性以啟用安全傳輸。</span><span class="sxs-lookup"><span data-stu-id="b2add-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="b2add-119">繫結項目的順序很重要定義自訂繫結，因為每個都代表通道堆疊中的圖層 (請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md))。</span><span class="sxs-lookup"><span data-stu-id="b2add-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="b2add-120">自訂繫結會定義在服務與用戶端組態檔中，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="b2add-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>  
  
```xml  
<bindings>  
  <!-- Configure a custom binding. -->  
  <customBinding>  
    <binding name="Binding1">  
      <security authenticationMode="SecureConversation"  
                 requireSecurityContextCancellation="true">  
      </security>  
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
      <sslStreamSecurity requireClientCertificate="false"/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="b2add-121">自訂繫結使用服務憑證來驗證傳輸層級上的服務，並在用戶端和服務之間進行傳輸時保護訊息。</span><span class="sxs-lookup"><span data-stu-id="b2add-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="b2add-122">這是由 `sslStreamSecurity` 繫結項目所完成。</span><span class="sxs-lookup"><span data-stu-id="b2add-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="b2add-123">服務的憑證會使用服務行為設定，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="b2add-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata />  
        <serviceDebug includeExceptionDetailInFaults="False" />  
        <serviceCredentials>  
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
        </serviceCredentials>  
    </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="b2add-124">此外，自訂繫結使用 Windows 認證類型 (預設認證類型) 的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="b2add-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="b2add-125">這是由 `security` 繫結項目所完成。</span><span class="sxs-lookup"><span data-stu-id="b2add-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="b2add-126">如果可以使用 Kerberos 驗證機制，則會使用訊息層級安全性來驗證用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="b2add-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="b2add-127">如果此範例是執行於 Active Directory 環境，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="b2add-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="b2add-128">如果 Kerberos 驗證機制無法使用，則使用 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="b2add-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="b2add-129">NTLM 會對服務驗證用戶端，但不會對用戶端驗證服務。</span><span class="sxs-lookup"><span data-stu-id="b2add-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="b2add-130">`security`繫結項目設定為使用`SecureConversation``authenticationType`，這會導致用戶端和服務上的安全性工作階段的建立。</span><span class="sxs-lookup"><span data-stu-id="b2add-130">The `security` binding element is configured to use `SecureConversation``authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="b2add-131">若要讓服務的雙工合約能運作，這是必要的。</span><span class="sxs-lookup"><span data-stu-id="b2add-131">This is required to enable the service's duplex contract to work.</span></span>  
  
 <span data-ttu-id="b2add-132">當您執行範例時，作業要求和回應會顯示在用戶端的主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="b2add-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="b2add-133">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="b2add-133">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="b2add-134">當執行範例時，您會看到訊息在回呼服務所傳送的介面時傳回到用戶端。</span><span class="sxs-lookup"><span data-stu-id="b2add-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="b2add-135">完成所有作業時，每個中繼結果都會顯示，並接著顯示整個方程式。</span><span class="sxs-lookup"><span data-stu-id="b2add-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="b2add-136">按 ENTER 鍵關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="b2add-136">Press ENTER to shut down the client.</span></span>  
  
 <span data-ttu-id="b2add-137">這個已包含的 Setup.bat 檔可讓您使用相關的服務憑證設定用戶端與伺服器，以執行需要憑證安全性的自我裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2add-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="b2add-138">這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="b2add-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="b2add-139">下面提供套用至此範例之批次檔的各區段的簡要概觀，讓批次檔得以修改為在適當的組態下執行：</span><span class="sxs-lookup"><span data-stu-id="b2add-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="b2add-140">建立伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="b2add-140">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="b2add-141">下列 Setup.bat 檔中的程式行會建立要使用的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="b2add-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="b2add-142">`%SERVER_NAME%` 變數會指定伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="b2add-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="b2add-143">您可以變更這個變數來指定自己的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="b2add-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="b2add-144">這個批次檔的名稱預設為伺服器名稱，localhost。</span><span class="sxs-lookup"><span data-stu-id="b2add-144">This batch file defaults the server name to localhost.</span></span>  
  
     <span data-ttu-id="b2add-145">憑證會儲存在 Web 裝載服務的 CurrentUser 存放區中。</span><span class="sxs-lookup"><span data-stu-id="b2add-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="b2add-146">將伺服器憑證安裝至用戶端的受信任憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="b2add-146">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="b2add-147">Setup.bat 檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。</span><span class="sxs-lookup"><span data-stu-id="b2add-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="b2add-148">這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。</span><span class="sxs-lookup"><span data-stu-id="b2add-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="b2add-149">如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證的步驟。</span><span class="sxs-lookup"><span data-stu-id="b2add-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b2add-150">Setup.bat 批次檔是設計用來從 Visual Studio 2010 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="b2add-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="b2add-151">它要求 MSSDK 環境變數指向安裝 SDK 的目錄。</span><span class="sxs-lookup"><span data-stu-id="b2add-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="b2add-152">這個環境變數是自動在 Visual Studio 2010 命令提示字元中設定。</span><span class="sxs-lookup"><span data-stu-id="b2add-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b2add-153">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="b2add-153">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b2add-154">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b2add-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b2add-155">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="b2add-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b2add-156">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b2add-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="b2add-157">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="b2add-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="b2add-158">使用系統管理員權限來開啟 Visual Studio 命令提示字元視窗，然後執行範例安裝資料夾中的 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="b2add-158">Open a Visual Studio Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="b2add-159">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="b2add-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2add-160">Setup.bat 批次檔是設計用來從 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="b2add-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="b2add-161">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元中設定的 PATH 環境變數會指向包含 Setup.bat 指令碼所需之可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="b2add-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="b2add-162">從 \service\bin 啟動 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="b2add-162">Launch Service.exe from \service\bin.</span></span>  
  
3.  <span data-ttu-id="b2add-163">從 \client\bin 啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="b2add-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="b2add-164">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="b2add-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="b2add-165">如果用戶端和服務能夠進行通訊，請參閱[疑難排解祕訣](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="b2add-165">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="b2add-166">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="b2add-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="b2add-167">在服務電腦上：</span><span class="sxs-lookup"><span data-stu-id="b2add-167">On the service computer:</span></span>  
  
    1.  <span data-ttu-id="b2add-168">在服務電腦上建立名為 servicemodelsamples 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="b2add-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2.  <span data-ttu-id="b2add-169">將 \inetpub\wwwroot\servicemodelsamples 中的服務程式檔複製至服務電腦上的虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="b2add-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="b2add-170">確定複製 \bin 子目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="b2add-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3.  <span data-ttu-id="b2add-171">將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。</span><span class="sxs-lookup"><span data-stu-id="b2add-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4.  <span data-ttu-id="b2add-172">執行下列命令在 Visual Studio 命令提示字元開啟系統管理員權限： `Setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="b2add-172">Run the following command in a Visual Studio command prompt opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="b2add-173">這會建立服務憑證，其主體名稱與批次檔執行於其中之電腦的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="b2add-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b2add-174">Setup.bat 批次檔是設計用來從 Visual Studio 2010 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="b2add-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="b2add-175">它要求 path 環境變數指向安裝 SDK 的目錄。</span><span class="sxs-lookup"><span data-stu-id="b2add-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="b2add-176">這個環境變數是自動在 Visual Studio 2010 命令提示字元中設定。</span><span class="sxs-lookup"><span data-stu-id="b2add-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
    5.  <span data-ttu-id="b2add-177">變更[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) Service.exe.config 檔以反映上一個步驟中產生的憑證的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="b2add-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>  
  
    6.  <span data-ttu-id="b2add-178">從命令提示字元執行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="b2add-178">Run Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="b2add-179">在用戶端電腦上：</span><span class="sxs-lookup"><span data-stu-id="b2add-179">On the client computer:</span></span>  
  
    1.  <span data-ttu-id="b2add-180">將用戶端程式檔案從 \client\bin\ 資料夾複製到用戶端電腦中。</span><span class="sxs-lookup"><span data-stu-id="b2add-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="b2add-181">同時複製 Cleanup.bat 檔。</span><span class="sxs-lookup"><span data-stu-id="b2add-181">Also copy the Cleanup.bat file.</span></span>  
  
    2.  <span data-ttu-id="b2add-182">執行 Cleanup.bat，移除先前範例的任何舊憑證。</span><span class="sxs-lookup"><span data-stu-id="b2add-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>  
  
    3.  <span data-ttu-id="b2add-183">匯出服務的憑證，方法是使用系統管理權限來開啟 Visual Studio 命令提示字元，然後在服務電腦上執行下列命令 (將 `%SERVER_NAME%` 取代成執行此服務之電腦的完整名稱)：</span><span class="sxs-lookup"><span data-stu-id="b2add-183">Export the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  <span data-ttu-id="b2add-184">將 %SERVER_NAME%.cer 複製到用戶端電腦 (將 %SERVER_NAME% 取代成執行此服務之電腦的完整名稱)。</span><span class="sxs-lookup"><span data-stu-id="b2add-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>  
  
    5.  <span data-ttu-id="b2add-185">匯入服務的憑證，方法是使用系統管理權限來開啟 Visual Studio 命令提示字元，然後在用戶端電腦上執行下列命令 (將 %SERVER_NAME% 取代成執行此服務之電腦的完整名稱)：</span><span class="sxs-lookup"><span data-stu-id="b2add-185">Import the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         <span data-ttu-id="b2add-186">如果憑證是由信任的簽發者發行，就不需要執行步驟 c、d 和 e。</span><span class="sxs-lookup"><span data-stu-id="b2add-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>  
  
    6.  <span data-ttu-id="b2add-187">修改用戶端的 App.config 檔，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2add-187">Modify the client’s App.config file as follows:</span></span>  
  
        ```xml  
        <client>  
            <endpoint name="default"  
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"   
                binding="customBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"  
        behaviorConfiguration="CalculatorClientBehavior" />  
        </client>  
        ```  
  
    7.  <span data-ttu-id="b2add-188">如果用於執行服務的帳戶有別於網域環境中的 NetworkService 或 LocalSystem 帳戶，您可能需要修改用戶端 App.config 檔中服務端點的端點身分識別，以根據用來執行服務之帳戶設定適當的 UPN 或 SPN。</span><span class="sxs-lookup"><span data-stu-id="b2add-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="b2add-189">如需端點身分識別的詳細資訊，請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)主題。</span><span class="sxs-lookup"><span data-stu-id="b2add-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>  
  
    8.  <span data-ttu-id="b2add-190">從命令提示字元執行 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="b2add-190">Run Client.exe from a command prompt.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="b2add-191">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="b2add-191">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="b2add-192">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="b2add-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2add-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2add-193">See Also</span></span>
