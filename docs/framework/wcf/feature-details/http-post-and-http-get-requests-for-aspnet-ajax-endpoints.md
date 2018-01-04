---
title: "HOW TO：在 ASP.NET AJAX 端點的 HTTP POST 和 HTTP GET 要求之間進行選擇"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa8aceace03d1abb3bb83de1262331485f12ded3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="e5e8d-102">HOW TO：在 ASP.NET AJAX 端點的 HTTP POST 和 HTTP GET 要求之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="e5e8d-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="e5e8d-103"> 可讓您建立服務以公開啟用 ASP.NET AJAX 的端點，並可在用戶端網站上透過 JavaScript 來呼叫此端點。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="e5e8d-104">建置這類服務的基本程序會討論[How to： 使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)和[如何： 加入 ASP.NET AJAX 端點而不使用組態](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="e5e8d-105">ASP.NET AJAX 支援使用 HTTP POST 和 HTTP GET 動詞 (預設為 HTTP POST) 的作業。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="e5e8d-106">若要建立沒有任何副作用並傳回不常或永不變更的資料時，請改用 HTTP GET。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="e5e8d-107">您可以快取 GET 作業的結果，也就是說，對相同作業的多次呼叫可能只需要對服務提出一次要求。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="e5e8d-108">快取並不是由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 完成，而是可能發生在任何層級 (透過使用者的瀏覽器、Proxy 伺服器與其他層級)。如果您想要增加服務效能，使用快取是比較有利的方式，但是假如資料常常變更，或是作業會執行某些動作時，可能就不適合使用快取。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-108">The caching is not done by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="e5e8d-109">例如，如果您正在設計服務來管理使用者的音樂資料庫，負責依據專輯標題來查詢音樂創作者的作業就可以利用 GET 輕鬆得到想要的資料，但是將專輯新增至使用者個人收藏的作業則必須使用 POST 才行。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="e5e8d-110">若要控制快取的存留期，請使用 <xref:System.ServiceModel.Web.OutgoingWebResponseContext> 型別。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="e5e8d-111">例如，在設計可傳回每小時更新的氣象預報服務時，可以使用 GET 並將快取範圍限制在一小時以內，以避免服務的使用者存取到過時資料。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="e5e8d-112">當您使用來自 ASP.NET AJAX 頁面 (使用指令碼管理員控制項) 的服務時，不論作業是使用 GET 或 POST，指令碼管理員機制都會確保發出正確的要求類型。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="e5e8d-113">HTTP GET 作業會使用 POST 作業支援的所有輸入參數，包括複雜資料合約型別。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="e5e8d-114">但是，在大部分情況下，建議您不要在 GET 作業中使用太多或太複雜的參數，因為這樣會降低快取效率。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="e5e8d-115">本主題說明如何藉由將 <xref:System.ServiceModel.Web.WebGetAttribute> 或 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性新增至服務合約內的相關作業中，以便在 GET 和 POST 間進行選取。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="e5e8d-116">讓服務順利執行所需的其他步驟 (實作、設定與裝載服務) 與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中任何 ASP.NET AJAX 服務所使用的步驟很類似。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="e5e8d-117">加上 <xref:System.ServiceModel.Web.WebGetAttribute> 標示的作業一律使用 GET 要求。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="e5e8d-118">加上 <xref:System.ServiceModel.Web.WebInvokeAttribute> 標示，或是未加上任何這兩個屬性的作業，則會使用 POST 要求。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="e5e8d-119"><xref:System.ServiceModel.Web.WebInvokeAttribute> 允許透過 <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> 屬性使用 GET 和 POST 以外的其他 HTTP 動詞 (例如 PUT 和 DELETE 等等)。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="e5e8d-120">但是，ASP.NET AJAX 並不支援這些動詞。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="e5e8d-121">如果您想要透過指令碼管理員控制項使用來自 ASP.NET 頁面的服務，請勿使用 <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="e5e8d-122">切換至 GET 的實用範例，請參閱[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="e5e8d-123">如需使用 POST 的範例，請參閱[AJAX 服務使用 HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)範例。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="e5e8d-124">若要建立回應 HTTP GET 或 HTTP POST 要求的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="e5e8d-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>  
  
1.  <span data-ttu-id="e5e8d-125">使用以 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 屬性標記的介面來定義基本的 <xref:System.ServiceModel.ServiceContractAttribute> 服務合約。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-125">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="e5e8d-126">以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="e5e8d-127">新增 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性，以指定回應 HTTP GET 要求的作業。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="e5e8d-128">您也可以新增 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性，明確地指定 HTTP POST，或不指定屬性 (如此將預設為 HTTP POST)。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>  
  
    ```  
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="e5e8d-129">使用 `IMusicService` 來實作 `MusicService` 服務合約。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>  
  
    ```  
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3.  <span data-ttu-id="e5e8d-130">在應用程式中建立名為 service 且包含 .svc 副檔名的新檔案。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="e5e8d-131">藉由新增適當的編輯此檔案[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-131">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="e5e8d-132">指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>到用於在[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞，以自動設定 ASP.NET AJAX 端點。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a><span data-ttu-id="e5e8d-133">若要呼叫服務</span><span class="sxs-lookup"><span data-stu-id="e5e8d-133">To call the service</span></span>  
  
1.  <span data-ttu-id="e5e8d-134">您可以透過瀏覽器，測試不包含任何用戶端程式碼的服務 GET 作業。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="e5e8d-135">例如，如果您的服務是設定在 "http://example.com/service.svc" 位址上，則將 "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" 輸入瀏覽器網址列中會叫用服務並導致下載或顯示回應。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-135">For example, if your service is configured at the "http://example.com/service.svc" address, then typing "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>  
  
2.  <span data-ttu-id="e5e8d-136">您可以使用包含 GET 作業的服務，方法就像您使用其他任何 ASP.NET AJAX 服務一樣，亦即在 ASP.NET AJAX 指令碼管理員控制項的指令碼集合中輸入服務 URL。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="e5e8d-137">如需範例，請參閱[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e8d-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e8d-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5e8d-138">See Also</span></span>  
 [<span data-ttu-id="e5e8d-139">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="e5e8d-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="e5e8d-140">如何：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="e5e8d-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
