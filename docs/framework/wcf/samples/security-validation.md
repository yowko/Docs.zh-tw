---
title: 安全性驗證
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 17e6e250c6b345477f7c9b377eb8e16ff4331ca7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183374"
---
# <a name="security-validation"></a><span data-ttu-id="6775e-102">安全性驗證</span><span class="sxs-lookup"><span data-stu-id="6775e-102">Security Validation</span></span>
<span data-ttu-id="6775e-103">這個範例示範如何使用自訂行為驗證電腦上的服務，以確定服務符合特定條件。</span><span class="sxs-lookup"><span data-stu-id="6775e-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="6775e-104">在這個範例中，服務會經過驗證，其方式是自訂行為掃描服務上的每個端點，並檢查這些端點是否包含安全繫結項目。</span><span class="sxs-lookup"><span data-stu-id="6775e-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="6775e-105">此示例基於[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6775e-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6775e-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="6775e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="6775e-107">端點驗證自訂行為</span><span class="sxs-lookup"><span data-stu-id="6775e-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="6775e-108">將使用者程式碼新增至包含在 `Validate` 介面中的 <xref:System.ServiceModel.Description.IServiceBehavior> 方法，可以提供自訂行為給服務或端點用來執行使用者定義的動作。</span><span class="sxs-lookup"><span data-stu-id="6775e-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="6775e-109">下列程式碼是用來對服務中包含的每個端點執行迴圈，以搜尋整個繫結集合中的安全繫結。</span><span class="sxs-lookup"><span data-stu-id="6775e-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="6775e-110">將下列程式碼新增至 Web.config 檔案，就可以為所要辨認的服務新增 `serviceValidate` 行為延伸。</span><span class="sxs-lookup"><span data-stu-id="6775e-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="6775e-111">一旦將行為延伸新增至服務，就會立即將 `endpointValidate` 行為新增至 Web.config 檔案中的行為清單，從而新增至服務。</span><span class="sxs-lookup"><span data-stu-id="6775e-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="6775e-112">新增至 Web.config 檔案的行為及其延伸會將行為套用至個別服務；然而，當新增至 Machine.config 檔案時，則會將行為套用至電腦上所有在作用中的服務。</span><span class="sxs-lookup"><span data-stu-id="6775e-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6775e-113">將行為新增至所有服務時，建議您最好在進行任何變更前先備份 Machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="6775e-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="6775e-114">現在，請執行本範例 client\bin 目錄中提供的用戶端。</span><span class="sxs-lookup"><span data-stu-id="6775e-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="6775e-115">以下消息出現異常："無法啟動請求的服務"。'"。http://localhost/servicemodelsamples/service.svc</span><span class="sxs-lookup"><span data-stu-id="6775e-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="6775e-116">這是預料中的事，因為端點驗證行為認為該端點不安全，所以不讓服務啟動。</span><span class="sxs-lookup"><span data-stu-id="6775e-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="6775e-117">這個行為還會擲回內部例外狀況，以描述哪個端點不安全，並且在系統「事件檢視器」中的 [System.ServiceModel 4.0.0.0] 來源與 [WebHost] 類別下方寫入訊息。</span><span class="sxs-lookup"><span data-stu-id="6775e-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="6775e-118">此外，您也可以在這個範例中的服務上開啟追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="6775e-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="6775e-119">這將允許使用者使用「服務追蹤檢視器」工具開啟產生的服務追蹤，以檢視端點驗證行為擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6775e-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="6775e-120">在事件檢視器中檢視失敗的端點驗證例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="6775e-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="6775e-121">按一下"**開始"** 功能表並選擇 **"運行..."**</span><span class="sxs-lookup"><span data-stu-id="6775e-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="6775e-122">輸入 `eventvwr` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6775e-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="6775e-123">在"事件檢視器"視窗中，按一下"**應用程式**"。</span><span class="sxs-lookup"><span data-stu-id="6775e-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="6775e-124">按兩下**應用程式**視窗中的"WebHost"類別下最近添加的"System.ServiceModel 4.0.0.0"事件，以查看不安全的終結點消息。</span><span class="sxs-lookup"><span data-stu-id="6775e-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6775e-125">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="6775e-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6775e-126">確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6775e-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6775e-127">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="6775e-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6775e-128">要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。</span><span class="sxs-lookup"><span data-stu-id="6775e-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6775e-129">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6775e-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6775e-130">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6775e-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6775e-131">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="6775e-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6775e-132">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6775e-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="6775e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6775e-133">See also</span></span>

- <span data-ttu-id="6775e-134">[AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6775e-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
