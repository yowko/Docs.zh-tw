---
title: 獨立診斷摘要範例
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 29d8caee48925040db9f1812f015870e3a1272bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144002"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="93a5f-102">獨立診斷摘要範例</span><span class="sxs-lookup"><span data-stu-id="93a5f-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="93a5f-103">此示例演示如何創建 RSS/原子源，以便與 Windows 通信基礎 （WCF） 聯合使用。</span><span class="sxs-lookup"><span data-stu-id="93a5f-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="93a5f-104">它是一個基本的"Hello World"程式，它顯示了物件模型的基礎知識以及如何在 Windows 通信基礎 （WCF） 服務上設置它。</span><span class="sxs-lookup"><span data-stu-id="93a5f-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="93a5f-105">WCF 將聯合饋送建模為返回特殊資料類型的服務操作<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>。</span><span class="sxs-lookup"><span data-stu-id="93a5f-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="93a5f-106"><xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 的執行個體可將摘要序列化至 RSS 2.0 和 Atom 1.0 格式。</span><span class="sxs-lookup"><span data-stu-id="93a5f-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="93a5f-107">下列範例程式碼會顯示使用的合約。</span><span class="sxs-lookup"><span data-stu-id="93a5f-107">The following sample code shows the contract used.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="93a5f-108">該`GetProcesses`操作使用<xref:System.ServiceModel.Web.WebGetAttribute>屬性進行批號，該屬性使您能夠控制 WCF 如何向服務操作發送 HTTP GET 請求並指定所發送消息的格式。</span><span class="sxs-lookup"><span data-stu-id="93a5f-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="93a5f-109">與任何 WCF 服務一樣，聯合饋送可以在任何託管應用程式中自行託管。</span><span class="sxs-lookup"><span data-stu-id="93a5f-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="93a5f-110">新聞訂閱服務需要指定的繫結 (<xref:System.ServiceModel.WebHttpBinding>) 和指定的端點行為 (<xref:System.ServiceModel.Description.WebHttpBehavior>) 才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="93a5f-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="93a5f-111">新的 <xref:System.ServiceModel.Web.WebServiceHost> 類別提供方便的 API，不需特定的組態即可建立這類端點。</span><span class="sxs-lookup"><span data-stu-id="93a5f-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="93a5f-112">或者，您可以使用 IIS 裝載 .svc 檔案內的 <xref:System.ServiceModel.Activation.WebServiceHostFactory>，提供等同的功能 (本範例程式碼中未示範這項技術)。</span><span class="sxs-lookup"><span data-stu-id="93a5f-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```xml
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 <span data-ttu-id="93a5f-113">因為這個服務使用標準 HTTP GET 接收要求，所以您可以使用任何 RSS 或 ATOM 感知用戶端來存取服務。</span><span class="sxs-lookup"><span data-stu-id="93a5f-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="93a5f-114">例如，您可以通過導航到`http://localhost:8000/diagnostics/feed/?format=atom`RSS 感知瀏覽器或在`http://localhost:8000/diagnostics/feed/?format=rss`RSS 感知瀏覽器中查看此服務的輸出。</span><span class="sxs-lookup"><span data-stu-id="93a5f-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="93a5f-115">您還可以使用[WCF 聯合物件模型如何映射到 Atom 和 RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)來讀取聯合資料並使用命令代碼處理資料。</span><span class="sxs-lookup"><span data-stu-id="93a5f-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="93a5f-116">設置、生成和運行示例</span><span class="sxs-lookup"><span data-stu-id="93a5f-116">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="93a5f-117">確保電腦上具有 HTTP 和 HTTPS 的正確位址註冊許可權，如[Windows 通信基礎示例的一次性設置過程](one-time-setup-procedure-for-the-wcf-samples.md)中的設置說明中所述。</span><span class="sxs-lookup"><span data-stu-id="93a5f-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="93a5f-118">建置方案。</span><span class="sxs-lookup"><span data-stu-id="93a5f-118">Build the solution.</span></span>

3. <span data-ttu-id="93a5f-119">執行主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="93a5f-119">Run the console application.</span></span>

4. <span data-ttu-id="93a5f-120">在主控台應用程式運行時，導航到`http://localhost:8000/diagnostics/feed/?format=atom`或使用`http://localhost:8000/diagnostics/feed/?format=rss`RSS 感知瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="93a5f-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93a5f-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="93a5f-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="93a5f-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="93a5f-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="93a5f-123">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="93a5f-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93a5f-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="93a5f-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a><span data-ttu-id="93a5f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93a5f-125">See also</span></span>

- [<span data-ttu-id="93a5f-126">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="93a5f-126">WCF Web HTTP Programming Model</span></span>](../feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="93a5f-127">WCF 新聞訂閱</span><span class="sxs-lookup"><span data-stu-id="93a5f-127">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
