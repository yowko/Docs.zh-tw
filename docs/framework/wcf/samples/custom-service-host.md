---
title: 自訂服務裝載
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 80b2642fa202500aa22dc7d045476cb36677d47c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928857"
---
# <a name="custom-service-host"></a><span data-ttu-id="827ca-102">自訂服務裝載</span><span class="sxs-lookup"><span data-stu-id="827ca-102">Custom Service Host</span></span>
<span data-ttu-id="827ca-103">這個範例會示範如何使用 <xref:System.ServiceModel.ServiceHost> 類別的自訂衍生，以變更服務的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="827ca-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="827ca-104">這個方法會提供可重複使用替代方案，以便透過常用方法來設定大量服務。</span><span class="sxs-lookup"><span data-stu-id="827ca-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="827ca-105">此範例也會示範如何使用 <xref:System.ServiceModel.Activation.ServiceHostFactory> 類別，以便在網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 裝載環境中使用自訂 ServiceHost。</span><span class="sxs-lookup"><span data-stu-id="827ca-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="827ca-106">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="827ca-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="827ca-107">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="827ca-107">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="827ca-108">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="827ca-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="827ca-109">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="827ca-109">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="827ca-110">關於案例</span><span class="sxs-lookup"><span data-stu-id="827ca-110">About the Scenario</span></span>  
 <span data-ttu-id="827ca-111">為避免不慎洩漏可能的敏感性服務中繼資料，Windows Communication Foundation （WCF）服務的預設設定會停用中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="827ca-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="827ca-112">這個行為依預設為安全行為，但也表示您無法使用中繼資料匯入工具 (例如 Svcutil.exe) 來產生呼叫服務所需的用戶端程式碼，除非組態中已明確啟用服務的中繼發行行為。</span><span class="sxs-lookup"><span data-stu-id="827ca-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="827ca-113">啟用大量服務的中繼資料發行，需要將相同的組態項目加入至每個個別服務，而這會產生大量組態資訊，這些資訊基本上都是相同的。</span><span class="sxs-lookup"><span data-stu-id="827ca-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="827ca-114">除了個別設定每個服務，也撰寫命令式程式碼，讓中繼資料一次發行，然後在數個不同的服務中重複使用該程式碼。</span><span class="sxs-lookup"><span data-stu-id="827ca-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="827ca-115">這是藉由建立衍生自 <xref:System.ServiceModel.ServiceHost> 並覆寫 `ApplyConfiguration`() 方法，以命令方式新增中繼資料發行行為的新類別來達成。</span><span class="sxs-lookup"><span data-stu-id="827ca-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="827ca-116">為了清楚說明，這個範例示範如何建立不安全的中繼資料發行端點。</span><span class="sxs-lookup"><span data-stu-id="827ca-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="827ca-117">未經驗證的匿名使用者可能可以使用這類端點，所以部署前必須小心謹慎，才能確保公開服務中繼資料是否適切。</span><span class="sxs-lookup"><span data-stu-id="827ca-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="827ca-118">實作自訂 ServiceHost</span><span class="sxs-lookup"><span data-stu-id="827ca-118">Implementing a Custom ServiceHost</span></span>  
 <span data-ttu-id="827ca-119"><xref:System.ServiceModel.ServiceHost> 類別會公開數個繼承者可覆寫以變更服務之執行階段行為的有用虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="827ca-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="827ca-120">例如，`ApplyConfiguration`() 方法會從組態存放區讀取服務組態資訊，並因此變更主機的 <xref:System.ServiceModel.Description.ServiceDescription>。</span><span class="sxs-lookup"><span data-stu-id="827ca-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="827ca-121">預設實作會從應用程式的組態檔讀取組態。</span><span class="sxs-lookup"><span data-stu-id="827ca-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="827ca-122">自訂實作可以覆寫 `ApplyConfiguration`()，以進一步使用命令式程式碼變更 <xref:System.ServiceModel.Description.ServiceDescription>，或甚至完全取代預設組態存放區。</span><span class="sxs-lookup"><span data-stu-id="827ca-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="827ca-123">例如，從資料庫而不是從應用程式的組態檔讀取服務的端點組態。</span><span class="sxs-lookup"><span data-stu-id="827ca-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="827ca-124">在此範例中，會希望建置新增 ServiceMetadataBehavior 的自訂 ServiceHost (可啟用中繼資料發行)，即使此行為未明確新增在服務的組態檔中也一樣。</span><span class="sxs-lookup"><span data-stu-id="827ca-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="827ca-125">若要達到此目的，可建立繼承自 <xref:System.ServiceModel.ServiceHost> 的新類別，並覆寫 `ApplyConfiguration`()。</span><span class="sxs-lookup"><span data-stu-id="827ca-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```csharp  
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to   
    //alter the ServiceDescription prior to opening  
    //the service host.   
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();       
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 <span data-ttu-id="827ca-126">由於不想要忽略應用程式組態檔中已提供的任何組態，覆寫 `ApplyConfiguration`() 時所執行的第一個動做為呼叫基底實作。</span><span class="sxs-lookup"><span data-stu-id="827ca-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="827ca-127">完成此方法時，就可以使用下列命令式程式碼，以命令方式將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 新增至描述。</span><span class="sxs-lookup"><span data-stu-id="827ca-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```csharp  
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,   
    //so we do not have any work to do.  
    return;  
}  
```  
  
 <span data-ttu-id="827ca-128">覆寫 `ApplyConfiguration`() 必須執行的最後一個動作為新增預設中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="827ca-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="827ca-129">一般來說，會在服務主機的 BaseAddresses 集合中，對每個 URI 建立一個中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="827ca-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
```csharp  
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="827ca-130">在自我裝載案例中使用自訂 ServiceHost</span><span class="sxs-lookup"><span data-stu-id="827ca-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="827ca-131">現在您已完成自訂 ServiceHost 實作，可以透過在 `SelfDescribingServiceHost` 的執行個體內裝載服務，即可使用此實作將中繼資料發行行為新增至該服務。</span><span class="sxs-lookup"><span data-stu-id="827ca-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="827ca-132">下列程式碼會顯示如何在自我裝載案例中使用該服務。</span><span class="sxs-lookup"><span data-stu-id="827ca-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="827ca-133">自訂主機仍會從應用程式的組態檔中讀取服務的端點組態，就如使用預設 <xref:System.ServiceModel.ServiceHost> 類別裝載服務一樣。</span><span class="sxs-lookup"><span data-stu-id="827ca-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="827ca-134">不過，由於新增邏輯以在自訂主機內啟用中繼資料發行，就不再需要於組態中明確啟用中繼資料發行行為。</span><span class="sxs-lookup"><span data-stu-id="827ca-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="827ca-135">當您建置其中包含多個服務的應用程式，而且想要在每個服務上啟用中繼資料發行，但不想要重複撰寫相同的組態項目時，這個方法特別有用。</span><span class="sxs-lookup"><span data-stu-id="827ca-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="827ca-136">在 IIS 或 WAS 中使用自訂 ServiceHost</span><span class="sxs-lookup"><span data-stu-id="827ca-136">Using a Custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="827ca-137">在自我裝載案例中使用自訂服務主機很簡單，因為這是您的應用程式程式碼，而且主要負責建立及開啟服務主機執行個體。</span><span class="sxs-lookup"><span data-stu-id="827ca-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="827ca-138">不過，在 IIS 或 WAS 裝載環境中，WCF 基礎結構會動態具現化服務的主機，以回應傳入的訊息。</span><span class="sxs-lookup"><span data-stu-id="827ca-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="827ca-139">自訂服務主機也可以在此裝載環境中使用，但形式上在 ServiceHostFactory 中需要額外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="827ca-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="827ca-140">下列程式碼會顯示 <xref:System.ServiceModel.Activation.ServiceHostFactory> 衍生，而這個衍生會傳回自訂 `SelfDescribingServiceHost` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="827ca-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```csharp  
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,   
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)   
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,     
                                             baseAddresses);  
    }  
}  
```  
  
 <span data-ttu-id="827ca-141">如您所見，實作自訂 ServiceHostFactory 非常簡單。</span><span class="sxs-lookup"><span data-stu-id="827ca-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="827ca-142">所有自訂邏輯都在 ServiceHost 實作內部，而處理站會傳回衍生類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="827ca-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="827ca-143">若要搭配使用自訂處理站和服務實作，必須將一些額外的中繼資料新增至服務的 .svc 檔。</span><span class="sxs-lookup"><span data-stu-id="827ca-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 <span data-ttu-id="827ca-144">在這裡會將額外的 `Factory` 屬性新增至 `@ServiceHost` 指示詞，並傳遞自訂處理站的 CLR 型別名稱做為屬性值。</span><span class="sxs-lookup"><span data-stu-id="827ca-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="827ca-145">當 IIS 或 WAS 收到此服務的訊息時，WCF 裝載基礎結構會先建立 ServiceHostFactory 的實例，然後藉由呼叫`ServiceHostFactory.CreateServiceHost()`來具現化服務主機本身。</span><span class="sxs-lookup"><span data-stu-id="827ca-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="827ca-146">執行範例</span><span class="sxs-lookup"><span data-stu-id="827ca-146">Running the Sample</span></span>  
 <span data-ttu-id="827ca-147">雖然此範例確實提供了完整功能的用戶端和服務實作，但此範例的目的為說明如何使用自訂主機，變更服務的執行個體行為。請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="827ca-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a><span data-ttu-id="827ca-148">若要觀察自訂主機的作用</span><span class="sxs-lookup"><span data-stu-id="827ca-148">To observe the effect of the custom host</span></span>  
  
1. <span data-ttu-id="827ca-149">開啟服務的 Web.config 檔，並觀察沒有組態已明確啟用服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="827ca-149">Open the service’s Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="827ca-150">開啟服務的 .svc 檔案，並觀察其@ServiceHost指示詞是否包含指定自訂 ServiceHostFactory 名稱的 Factory 屬性。</span><span class="sxs-lookup"><span data-stu-id="827ca-150">Open the service’s .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="827ca-151">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="827ca-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="827ca-152">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="827ca-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="827ca-153">若要建立方案，請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="827ca-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="827ca-154">建立解決方案之後，請執行 Setup .bat 來設定 IIS 7.0 中的 ServiceModelSamples 應用程式。</span><span class="sxs-lookup"><span data-stu-id="827ca-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="827ca-155">ServiceModelSamples 目錄現在應該會顯示為 IIS 7.0 應用程式。</span><span class="sxs-lookup"><span data-stu-id="827ca-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>  
  
4. <span data-ttu-id="827ca-156">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="827ca-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="827ca-157">若要移除 IIS 7.0 應用程式，請執行清除 .bat。</span><span class="sxs-lookup"><span data-stu-id="827ca-157">To remove the IIS 7.0 application, run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="827ca-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="827ca-158">See also</span></span>

- [<span data-ttu-id="827ca-159">如何：在 IIS 中裝載 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="827ca-159">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
