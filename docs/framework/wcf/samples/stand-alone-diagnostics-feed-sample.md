---
title: 獨立診斷摘要範例
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 2737621a98f6a7e89ef3aee01fd1ad7a2a60f9b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007816"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="5bba6-102">獨立診斷摘要範例</span><span class="sxs-lookup"><span data-stu-id="5bba6-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="5bba6-103">此範例示範如何建立 RSS/Atom 摘要的新聞訂閱與 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="5bba6-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="5bba6-104">它會顯示物件模型的基本概念以及如何設定 Windows Communication Foundation (WCF) 服務上的基本"Hello World"程式。</span><span class="sxs-lookup"><span data-stu-id="5bba6-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="5bba6-105">WCF 新聞訂閱摘要製作為服務作業傳回特殊資料型別的<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>。</span><span class="sxs-lookup"><span data-stu-id="5bba6-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="5bba6-106"><xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 的執行個體可將摘要序列化至 RSS 2.0 和 Atom 1.0 格式。</span><span class="sxs-lookup"><span data-stu-id="5bba6-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="5bba6-107">下列範例程式碼會顯示使用的合約。</span><span class="sxs-lookup"><span data-stu-id="5bba6-107">The following sample code shows the contract used.</span></span>  
  
```  
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
  
 <span data-ttu-id="5bba6-108">`GetProcesses`作業註解<xref:System.ServiceModel.Web.WebGetAttribute>屬性，可讓您控制 WCF 分派 HTTP GET 要求至服務作業，並指定傳送的訊息格式。</span><span class="sxs-lookup"><span data-stu-id="5bba6-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="5bba6-109">如同任何 WCF 服務，新聞訂閱摘要，也可以是自我裝載於任何 managed 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5bba6-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="5bba6-110">新聞訂閱服務需要指定的繫結 (<xref:System.ServiceModel.WebHttpBinding>) 和指定的端點行為 (<xref:System.ServiceModel.Description.WebHttpBehavior>) 才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="5bba6-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="5bba6-111">新的 <xref:System.ServiceModel.Web.WebServiceHost> 類別提供方便的 API，不需特定的組態即可建立這類端點。</span><span class="sxs-lookup"><span data-stu-id="5bba6-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="5bba6-112">或者，您可以使用 IIS 裝載 .svc 檔案內的 <xref:System.ServiceModel.Activation.WebServiceHostFactory>，提供等同的功能 (本範例程式碼中未示範這項技術)。</span><span class="sxs-lookup"><span data-stu-id="5bba6-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="5bba6-113">因為這個服務使用標準 HTTP GET 接收要求，所以您可以使用任何 RSS 或 ATOM 感知用戶端來存取服務。</span><span class="sxs-lookup"><span data-stu-id="5bba6-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="5bba6-114">比方說，您可以檢視此服務的輸出，瀏覽至`http://localhost:8000/diagnostics/feed/?format=atom`或`http://localhost:8000/diagnostics/feed/?format=rss`RSS 感知瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="5bba6-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="5bba6-115">您也可以使用[如何 WCF 新聞訂閱物件模型對應到 Atom 和 RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)讀取新聞訂閱方式的資料，並使用命令式程式碼進行處理。</span><span class="sxs-lookup"><span data-stu-id="5bba6-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5bba6-116">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5bba6-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5bba6-117">請確定您已正確位址註冊權限 HTTP 與 HTTPS 在電腦上的，安裝指示中所述[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5bba6-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5bba6-118">建置方案。</span><span class="sxs-lookup"><span data-stu-id="5bba6-118">Build the solution.</span></span>  
  
3. <span data-ttu-id="5bba6-119">執行主控台應用程式 (Console Application)。</span><span class="sxs-lookup"><span data-stu-id="5bba6-119">Run the console application.</span></span>  
  
4. <span data-ttu-id="5bba6-120">執行主控台應用程式時，瀏覽至 `http://localhost:8000/diagnostics/feed/?format=atom` 或 `http://localhost:8000/diagnostics/feed/?format=rss` 使用 RSS 感知瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="5bba6-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5bba6-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5bba6-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5bba6-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5bba6-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5bba6-123">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="5bba6-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5bba6-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5bba6-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="5bba6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bba6-125">See also</span></span>

- [<span data-ttu-id="5bba6-126">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="5bba6-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="5bba6-127">WCF 摘要整合</span><span class="sxs-lookup"><span data-stu-id="5bba6-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
