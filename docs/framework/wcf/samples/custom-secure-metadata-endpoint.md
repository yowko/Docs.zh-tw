---
title: 自訂安全中繼資料端點
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: c835cfecab38a76f285767f918dfc082915ffcfc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769683"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="6e7dd-102">自訂安全中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="6e7dd-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="6e7dd-103">這個範例會示範如何實作具有使用其中一個非中繼資料交換繫結，安全的中繼資料端點的服務以及如何設定[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)或用戶端從這類中繼端點的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="6e7dd-104">有兩個系統提供的繫結可用來公開中繼資料端點：mexHttpBinding 和 mexHttpsBinding。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="6e7dd-105">mexHttpBinding 可用來以不安全的方式，透過 HTTP 公開中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="6e7dd-106">mexHttpsBinding 可用來以安全的方式，透過 HTTPS 公開中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="6e7dd-107">此範例說明如何使用 <xref:System.ServiceModel.WSHttpBinding> 公開安全的中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="6e7dd-108">當您要變更繫結上的安全性設定時，您會想要這麼做，但是您不想使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="6e7dd-109">如果使用 mexHttpsBinding，您的中繼資料端點將是安全的，但是沒有方法可以修改繫結設定。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e7dd-110">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="6e7dd-111">服務</span><span class="sxs-lookup"><span data-stu-id="6e7dd-111">Service</span></span>  
 <span data-ttu-id="6e7dd-112">這個範例中的服務有兩個端點。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="6e7dd-113">應用程式端點可用於 `ICalculator` 上的 `WSHttpBinding` 合約 (已啟用 `ReliableSession`)，並可用於使用憑證的 `Message` 安全性。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="6e7dd-114">中繼資料端點也會使用 `WSHttpBinding`，它具有相同的安全性設定，但沒有 `ReliableSession`。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="6e7dd-115">此處為相關的組態：</span><span class="sxs-lookup"><span data-stu-id="6e7dd-115">Here is the relevant configuration:</span></span>  
  
```xml  
<services>   
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 <span data-ttu-id="6e7dd-116">在許多其他範例中，中繼資料端點會使用不安全的預設 `mexHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="6e7dd-117">在此處會使用 `WSHttpBinding` 搭配 `Message` 安全性來確認中繼資料的安全。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="6e7dd-118">為了讓中繼資料用戶端擷取此中繼資料，必須以相符的繫結來進行設定。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="6e7dd-119">這個範例會示範兩個這類的用戶端。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="6e7dd-120">第一個用戶端使用 Svcutil.exe 來擷取中繼資料，並在設計階段時產生用戶端程式碼和組態。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="6e7dd-121">由於服務會對中繼資料使用非預設繫結，您就必須明確地設定 Svcutil.exe 工具，讓它可使用該繫結從服務中取得中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="6e7dd-122">第二個用戶端會使用 `MetadataResolver` 以動態擷取已知合約的中繼資料，然後在動態產生的用戶端上叫用作業。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="6e7dd-123">Svcutil 用戶端</span><span class="sxs-lookup"><span data-stu-id="6e7dd-123">Svcutil client</span></span>  
 <span data-ttu-id="6e7dd-124">使用預設繫結裝載 `IMetadataExchange` 端點時，可以使用該端點的位址來執行 Svcutil.exe：</span><span class="sxs-lookup"><span data-stu-id="6e7dd-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="6e7dd-125">而這樣做確實有作用。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-125">and it works.</span></span> <span data-ttu-id="6e7dd-126">但在此範例中，伺服器會使用非預設端點來裝載中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="6e7dd-127">因此，必須指示 Svcutil.exe 使用正確的繫結。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="6e7dd-128">可以使用 Svcutil.exe.config 檔做到這點。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="6e7dd-129">Svcutil.exe.config 檔看起來就像一般的用戶端組態檔。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="6e7dd-130">唯一不尋常的方面為用戶端端點名稱和合約：</span><span class="sxs-lookup"><span data-stu-id="6e7dd-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="6e7dd-131">端點名稱必須是在此裝載中繼資料之位址配置的名稱，而端點合約必須為 `IMetadataExchange`。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="6e7dd-132">因此，使用命令列以下列方式執行 Svcutil.exe 時：</span><span class="sxs-lookup"><span data-stu-id="6e7dd-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="6e7dd-133">就會尋找名稱為 "http" 的端點和 `IMetadataExchange` 合約，以設定中繼資料端點通訊交換的繫結和行為。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="6e7dd-134">範例中的其他 Svcutil.exe.config 檔會指定繫結組態和行為認證，以比對中繼資料端點的伺服器組態。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="6e7dd-135">為了讓 Svcutil.exe 挑選 Svcutil.exe.config 中的組態，Svcutil.exe 的所在目錄必須和組態檔的目錄一樣。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="6e7dd-136">因此，您必須將 Svcutil.exe 從其安裝位置複製至包含 Svcutil.exe.config 檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="6e7dd-137">然後從該目錄執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="6e7dd-137">Then from that directory, run the following command:</span></span>  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="6e7dd-138">前置"。\\"可確保會執行此目錄 （具有相對應的 Svcutil.exe.config） 中的 Svcutil.exe 複本。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="6e7dd-139">MetadataResolver 用戶端</span><span class="sxs-lookup"><span data-stu-id="6e7dd-139">MetadataResolver client</span></span>  
 <span data-ttu-id="6e7dd-140">如果用戶端知道合約以及如何在設計階段與中繼資料互動，用戶端就可以使用 `MetadataResolver`，動態找出繫結和應用程式端點的位址。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="6e7dd-141">這個範例用戶端會示範如何藉由建立和設定 `MetadataResolver`，進而設定 `MetadataExchangeClient` 所使用的繫結和認證。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="6e7dd-142">您可以在 `MetadataExchangeClient` 上，以命令方式指定出現在 Svcutil.exe.config 中的相同繫結和憑證資訊。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="6e7dd-143">設定 `mexClient` 時，可以列舉感興趣的合約，並使用 `MetadataResolver` 來擷取具有這些合約的端點清單：</span><span class="sxs-lookup"><span data-stu-id="6e7dd-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="6e7dd-144">最後，使用來自這些端點的資訊來初始化 `ChannelFactory` 的繫結和位址，您可透過此繫結和位址建立通道以與應用程式端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="6e7dd-145">如果您正在使用 `MetadataResolver`，而且您必須對中繼資料交換通訊指定自訂繫結或行為，則此範例的重點在於示範使用 `MetadataExchangeClient` 來指定這些自訂設定。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="6e7dd-146">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="6e7dd-146">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="6e7dd-147">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6e7dd-148">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="6e7dd-149">若要在同一部機器上執行範例</span><span class="sxs-lookup"><span data-stu-id="6e7dd-149">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="6e7dd-150">從範例安裝資料夾執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="6e7dd-151">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="6e7dd-152">請注意，Setup.bat 會使用 FindPrivateKey.exe 工具，執行從 setupCertTool.bat 即可安裝[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6e7dd-153">從 \MetadataResolverClient\bin 或 \SvcutilClient\bin 執行用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="6e7dd-154">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-154">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="6e7dd-155">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-155">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="6e7dd-156">當您完成範例時，請執行 Cleanup.bat 以移除憑證。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="6e7dd-157">其他安全性範例使用相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="6e7dd-158">若要跨機器執行範例</span><span class="sxs-lookup"><span data-stu-id="6e7dd-158">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="6e7dd-159">在伺服器上執行 `setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="6e7dd-160">執行`setup.bat`與`service`引數會建立具有機器完整網域名稱的服務憑證，並將服務憑證匯出為名為 Service.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="6e7dd-161">在伺服器上編輯 Web.config，以反映新的憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="6e7dd-162">也就是變更`findValue`屬性中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)機器完整網域名稱的項目。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="6e7dd-163">從服務目錄中將 Service.cer 檔案複製至用戶端機器上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="6e7dd-164">在用戶端上執行 `setup.bat client`。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="6e7dd-165">執行`setup.bat`與`client`引數會建立名為 Client.com 的用戶端憑證，並將用戶端憑證匯出為名為 Client.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="6e7dd-166">在用戶端機器上之 `MetadataResolverClient` 的 App.config 檔案中，變更 MEX 端點的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="6e7dd-167">您可以藉由使用伺服器的完整網域名稱取代 localhost，完成這個動作。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="6e7dd-168">也請將 metadataResolverClient.cs 檔案中的其他 "localhost" 變更為新的服務憑證名稱 (伺服器的完整網域名稱)。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="6e7dd-169">對 SvcutilClient 專案的 App.config 執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="6e7dd-170">從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="6e7dd-171">在用戶端上執行 `ImportServiceCert.bat`。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="6e7dd-172">這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="6e7dd-173">在伺服器上執行 `ImportClientCert.bat`，這樣會從 Client.cer 檔案中將用戶端憑證匯入至 LocalMachine - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="6e7dd-174">在服務機器的 Visual Studio 中建置服務專案，並在 Web 瀏覽器中選取說明頁以驗證是否是在執行。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="6e7dd-175">在用戶端機器上，從 VS 執行 MetadataResolverClient 或 SvcutilClient。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1.  <span data-ttu-id="6e7dd-176">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-176">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="6e7dd-177">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="6e7dd-177">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="6e7dd-178">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e7dd-179">跨機器執行此範例時，這個指令碼不會移除用戶端上的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="6e7dd-180">如果您已執行跨機器使用憑證的 Windows Communication Foundation (WCF) 範例，請務必清除已安裝在 CurrentUser-TrustedPeople 存放區的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-180">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="6e7dd-181">若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="6e7dd-182">例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e7dd-183">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6e7dd-184">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-184">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6e7dd-185">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6e7dd-186">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6e7dd-186">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
