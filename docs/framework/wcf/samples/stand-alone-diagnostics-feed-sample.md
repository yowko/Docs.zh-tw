---
title: "獨立診斷摘要範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89de6bcbb44ca70592697ccf891099446b230ce6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="ad4b8-102">獨立診斷摘要範例</span><span class="sxs-lookup"><span data-stu-id="ad4b8-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="ad4b8-103">這個範例示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 建立新聞訂閱的 RSS/Atom 摘要。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-103">This sample demonstrates how to create an RSS/Atom feed for syndication with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="ad4b8-104">它是基本的 "Hello World" 程式，可顯示物件模型的基礎，以及在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務上的設定方式。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ad4b8-105"> 會將新聞訂閱摘要製作為可傳回特殊資料型別 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 的服務作業。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-105"> models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="ad4b8-106"><xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 的執行個體可將摘要序列化至 RSS 2.0 和 Atom 1.0 格式。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="ad4b8-107">下列範例程式碼會顯示使用的合約。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-107">The following sample code shows the contract used.</span></span>  
  
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
  
 <span data-ttu-id="ad4b8-108">`GetProcesses` 作業會以 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性來註解，這個屬性可讓您控制 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 將 HTTP GET 要求分派至服務作業的方式，以及指定所傳送訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="ad4b8-109">就像任何的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務一樣，新聞訂閱摘要可以自我裝載於任何 Managed 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-109">Like any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="ad4b8-110">新聞訂閱服務需要指定的繫結 (<xref:System.ServiceModel.WebHttpBinding>) 和指定的端點行為 (<xref:System.ServiceModel.Description.WebHttpBehavior>) 才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="ad4b8-111">新的 <xref:System.ServiceModel.Web.WebServiceHost> 類別提供方便的 API，不需特定的組態即可建立這類端點。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="ad4b8-112">或者，您可以使用 IIS 裝載 .svc 檔案內的 <xref:System.ServiceModel.Activation.WebServiceHostFactory>，提供等同的功能 (本範例程式碼中未示範這項技術)。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="ad4b8-113">因為這個服務使用標準 HTTP GET 接收要求，所以您可以使用任何 RSS 或 ATOM 感知用戶端來存取服務。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="ad4b8-114">例如，您可以透過使用 RSS 感知瀏覽器 (如 Internet Explorer 7) 巡覽至 http://localhost:8000/diagnostics/feed/?format=atom 或 http://localhost:8000/diagnostics/feed/?format=rss，來檢視這個服務的輸出。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-114">For example, you can view the output of this service by navigating to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss in an RSS-aware browser such as Internet Explorer 7.</span></span>  
  
 <span data-ttu-id="ad4b8-115">您也可以使用[如何 WCF 新聞訂閱物件模型對應到 Atom 和 RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)讀取新聞訂閱方式的資料，並使用命令式程式碼進行處理。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ad4b8-116">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ad4b8-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ad4b8-117">請確定您有正確的位址註冊權限的 HTTP 和 HTTPS 的電腦上，設定中的指示中所述[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ad4b8-118">建置方案。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-118">Build the solution.</span></span>  
  
3.  <span data-ttu-id="ad4b8-119">執行主控台應用程式 (Console Application)。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-119">Run the console application.</span></span>  
  
4.  <span data-ttu-id="ad4b8-120">執行主控台應用程式時，使用 RSS 感知瀏覽器巡覽至 http://localhost:8000/diagnostics/feed/?format=atom 或 http://localhost:8000/diagnostics/feed/?format=rss。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-120">While the console application is running, navigate to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ad4b8-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ad4b8-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ad4b8-123">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ad4b8-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ad4b8-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="ad4b8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad4b8-125">See Also</span></span>  
 [<span data-ttu-id="ad4b8-126">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="ad4b8-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="ad4b8-127">WCF 新聞訂閱</span><span class="sxs-lookup"><span data-stu-id="ad4b8-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
