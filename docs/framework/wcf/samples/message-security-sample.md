---
title: "訊息安全性範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
caps.latest.revision: "33"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: efad1940def2c27d57bb1e9da28e51362de5b237
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="message-security-sample"></a><span data-ttu-id="c7757-102">訊息安全性範例</span><span class="sxs-lookup"><span data-stu-id="c7757-102">Message Security Sample</span></span>
<span data-ttu-id="c7757-103">這個範例會示範如何實作一個使用 `basicHttpBinding` 和訊息安全性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7757-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="c7757-104">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，用來實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="c7757-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7757-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="c7757-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c7757-106">`basicHttpBinding` 的安全性模式可以設定為下列值：`Message`、`Transport`、`TransportWithMessageCredential`、`TransportCredentialOnly` 和 `None`。</span><span class="sxs-lookup"><span data-stu-id="c7757-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="c7757-107">在下列範例服務 App.config 檔中，端點定義會指定 `basicHttpBinding`，並參考名為 `Binding1` 的繫結組態，如下列範例組態所示：</span><span class="sxs-lookup"><span data-stu-id="c7757-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>   …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="c7757-108">繫結組態集`mode`屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)至`Message`並設定`clientCredentialType`屬性[\<訊息 >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)至`Certificate`如下列範例組態所示：</span><span class="sxs-lookup"><span data-stu-id="c7757-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="c7757-109">服務對用戶端驗證它自己時所使用的憑證是在組態檔案行為區段中的 `serviceCredentials` 項目下設定。</span><span class="sxs-lookup"><span data-stu-id="c7757-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="c7757-110">用戶端用來對服務驗證本身之憑證所套用的驗證模式也是在 `clientCertificate` 項目下的行為區段中設定。</span><span class="sxs-lookup"><span data-stu-id="c7757-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="c7757-111">相同的繫結和安全性詳細資訊是在用戶端組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="c7757-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="c7757-112">呼叫者的身分識別會透過下列程式碼顯示在服務主控台視窗中：</span><span class="sxs-lookup"><span data-stu-id="c7757-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  
  
```  
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```  
  
 <span data-ttu-id="c7757-113">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="c7757-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c7757-114">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="c7757-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="c7757-115">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="c7757-115">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="c7757-116">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c7757-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c7757-117">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="c7757-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="c7757-118">若要在同一部機器上執行範例</span><span class="sxs-lookup"><span data-stu-id="c7757-118">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="c7757-119">從範例安裝資料夾執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="c7757-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="c7757-120">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="c7757-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7757-121">Setup.bat 批次檔是設計用來從 Windows SDK 命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="c7757-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="c7757-122">它要求 MSSDK 環境變數指向安裝 SDK 的目錄。</span><span class="sxs-lookup"><span data-stu-id="c7757-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="c7757-123">這個環境變數是自動在 Windows SDK 命令提示字元中設定。</span><span class="sxs-lookup"><span data-stu-id="c7757-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2.  <span data-ttu-id="c7757-124">從 \service\bin 執行服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7757-124">Run the service application from \service\bin.</span></span>  
  
3.  <span data-ttu-id="c7757-125">從 \client\bin 執行用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7757-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="c7757-126">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="c7757-126">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="c7757-127">如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="c7757-127">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
5.  <span data-ttu-id="c7757-128">當您完成範例時，請執行 Cleanup.bat 以移除憑證。</span><span class="sxs-lookup"><span data-stu-id="c7757-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="c7757-129">其他安全性範例使用相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="c7757-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="c7757-130">若要跨機器執行範例</span><span class="sxs-lookup"><span data-stu-id="c7757-130">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="c7757-131">在服務機器上為服務二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="c7757-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="c7757-132">將服務程式檔複製到伺服器的服務目錄上。</span><span class="sxs-lookup"><span data-stu-id="c7757-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="c7757-133">同時，將 Setup.bat、Cleanup.bat 和 ImportClientCert.bat 檔案複製到伺服器。</span><span class="sxs-lookup"><span data-stu-id="c7757-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3.  <span data-ttu-id="c7757-134">在用戶端機器上為用戶端二進位碼檔案建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="c7757-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="c7757-135">將用戶端程式檔複製到用戶端機器上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="c7757-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="c7757-136">同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。</span><span class="sxs-lookup"><span data-stu-id="c7757-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="c7757-137">在伺服器上執行 `setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="c7757-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="c7757-138">執行`setup.bat`與`service`引數會建立具有機器完整網域名稱的服務憑證，並將服務憑證匯出為名為 Service.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="c7757-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="c7757-139">編輯以反映新的憑證名稱 Service.exe.config (在`findValue`屬性[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)項目) 的電腦完整網域名稱相同。</span><span class="sxs-lookup"><span data-stu-id="c7757-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="c7757-140">同時將基底位址的值變更成指定完整機器名稱，而不要指定 localhost`.`。</span><span class="sxs-lookup"><span data-stu-id="c7757-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7.  <span data-ttu-id="c7757-141">從服務目錄中將 Service.cer 檔案複製至用戶端機器上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="c7757-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="c7757-142">在用戶端上執行 `setup.bat client`。</span><span class="sxs-lookup"><span data-stu-id="c7757-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="c7757-143">使用 `setup.bat` 引數來執行 `client`，就會建立名稱為 client.com 的用戶端憑證，並且會將用戶端憑證匯出為名為 Client.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="c7757-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="c7757-144">在用戶端機器上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="c7757-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="c7757-145">您可以藉由使用伺服器的完整網域名稱取代 localhost，完成這個動作。</span><span class="sxs-lookup"><span data-stu-id="c7757-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="c7757-146">也會變更`findValue`屬性[ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)為新的服務憑證名稱也就是伺服器的完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="c7757-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="c7757-147">從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。</span><span class="sxs-lookup"><span data-stu-id="c7757-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="c7757-148">在用戶端上執行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="c7757-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="c7757-149">這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="c7757-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="c7757-150">在伺服器上執行 ImportClientCert.bat，這樣會從 Client.cer 檔案中將用戶端憑證匯入至 LocalMachine - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="c7757-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="c7757-151">在服務機器上，從命令提示字元執行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="c7757-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="c7757-152">在用戶端機器上，從命令提示字元視窗啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="c7757-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1.  <span data-ttu-id="c7757-153">如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="c7757-153">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c7757-154">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="c7757-154">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="c7757-155">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="c7757-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7757-156">跨機器執行此範例時，這個指令碼不會移除用戶端上的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="c7757-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="c7757-157">如果您已執行跨機器使用憑證的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 範例，請確定清除安裝在 CurrentUser - TrustedPeople 存放區中的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="c7757-157">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="c7757-158">若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="c7757-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7757-159">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c7757-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7757-160">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="c7757-160">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c7757-161">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="c7757-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7757-162">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="c7757-162">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## <a name="see-also"></a><span data-ttu-id="c7757-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7757-163">See Also</span></span>
