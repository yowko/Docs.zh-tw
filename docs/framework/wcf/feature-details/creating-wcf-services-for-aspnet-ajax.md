---
title: "建立 ASP.NET AJAX 的 WCF 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f13fffcfb6094b56f1cbfdffca52a1b24f437b4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a><span data-ttu-id="b9d1b-102">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="b9d1b-102">Creating WCF Services for ASP.NET AJAX</span></span>
<span data-ttu-id="b9d1b-103">Microsoft ASP.NET AJAX 可讓您使用反應靈敏和熟悉的使用者介面項目，快速建立包含豐富使用者經驗的 Web 網頁。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-103">Microsoft ASP.NET AJAX enables you to quickly create Web pages that include a rich user experience with responsive and familiar user interface elements.</span></span> <span data-ttu-id="b9d1b-104">ASP.NET AJAX 提供用戶端指令碼的程式庫，其中加入跨平台的 ECMAScript (JavaScript) 和動態 HTML (DHTML) 技術，並將它們與 ASP.NET 2.0 伺服器基礎的開發平台整合。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-104">ASP.NET AJAX provides client-script libraries that incorporate cross-browser ECMAScript (JavaScript) and dynamic HTML (DHTML) technologies, and it integrates them with the ASP.NET 2.0 server-based development platform.</span></span> <span data-ttu-id="b9d1b-105">您可以使用 ASP.NET AJAX 功能來改善使用者經驗和 Web 應用程式的效率。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-105">By using ASP.NET AJAX, you can improve the user experience and the efficiency of your Web applications.</span></span>  
  
 <span data-ttu-id="b9d1b-106">ASP.NET AJAX 包含內建的用戶端指令碼程式庫與伺服器元件，以提供您穩固的開發架構。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-106">ASP.NET AJAX consists of client-script libraries and of server components that are integrated to provide a robust development framework.</span></span> <span data-ttu-id="b9d1b-107">若要從 ASP.NET 頁面存取服務：一旦服務 URL 新增至頁面上的 ASP.NET 指令碼管理員控制項，服務作業可能會透過看起來與正常 JavaScript 函式呼叫沒兩樣的 JavaScript 程式碼來叫用。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-107">To access a service from an ASP.NET page: once the service URL is added to the ASP.NET Script Manager control on the page, service operations may be invoked using JavaScript code that looks exactly like a regular JavaScript function call.</span></span> <span data-ttu-id="b9d1b-108">請參閱[深入了解 ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=186475) AJAX 架構 Web 服務使用的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-108">See [Learn ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=186475) about the use of Web services within the AJAX framework.</span></span>  
  
 <span data-ttu-id="b9d1b-109">您可以新增適當的 ASP.NET AJAX 端點，將 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務公開為與 ASP.NET AJAX 相容的服務。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-109">Most [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services may be exposed as a service compatible with ASP.NET AJAX by adding an appropriate ASP.NET AJAX endpoint.</span></span>  
  
 <span data-ttu-id="b9d1b-110">如果您使用 Visual Studio，您可能會使用預先建立的範本中可用的啟用 AJAX 的 WCF 服務的**加入新項目**對話方塊時使用的 ASP.NET 網站或 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-110">If you are using Visual Studio, you may use a pre-built template for AJAX-enabled WCF services, available in the **Add New Item** dialog when working with ASP.NET Web Sites or Web Applications.</span></span>  
  
 <span data-ttu-id="b9d1b-111">如果您不是使用 Visual Studio 範本，則您可以透過下列兩種方法來建立 ASP.NET AJAX 端點：</span><span class="sxs-lookup"><span data-stu-id="b9d1b-111">If you are not using the Visual Studio templates, there are two ways to create an ASP.NET AJAX endpoint:</span></span>  
  
-   <span data-ttu-id="b9d1b-112">使用動態主機啟動 (而不是透過任何組態) 來建立端點。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-112">Create the endpoint using dynamic host activation without using any configuration.</span></span> <span data-ttu-id="b9d1b-113">如果您不熟悉 WCF 組態系統的話，這是最基本的操作方式。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-113">This is the most basic approach if you are unfamiliar with the WCF configuration system.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b9d1b-114">[How to： 不使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-114"> [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
-   <span data-ttu-id="b9d1b-115">透過組態將啟用 AJAX 的端點新增至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-115">Add an AJAX-enabled endpoint to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service using configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b9d1b-116">[How to： 使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-116"> [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
 <span data-ttu-id="b9d1b-117">Web 程式設計模型中所述[WCF Web HTTP 程式設計模型概觀](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)可搭配 ASP.NET AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-117">The Web Programming Model described in the [WCF Web HTTP Programming Model Overview](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) may be used with ASP.NET AJAX services.</span></span> <span data-ttu-id="b9d1b-118">尤其是：</span><span class="sxs-lookup"><span data-stu-id="b9d1b-118">Specifically:</span></span>  
  
-   <span data-ttu-id="b9d1b-119">您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性，在 HTTP GET 和 HTTP POST 動詞之間進行選擇。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-119">You can use the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to select between HTTP GET and HTTP POST verbs.</span></span> <span data-ttu-id="b9d1b-120">如果使用方式正確的話，可能會大幅改善應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-120">If used correctly, this may significantly improve your application’s performance.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b9d1b-121">[How to： 選擇 HTTP POST 和 HTTP GET 要求的 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-121"> [How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).</span></span>  
  
-   <span data-ttu-id="b9d1b-122">您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> 屬性，讓您的服務傳回 XML 資料，而不是預設的 JavaScript Object Notation (JSON)。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-122">You can use the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> and <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> properties to cause your service to return XML data instead of the default JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="b9d1b-123">使用 ASP.NET AJAX 架構來執行這項作業會導致 JavaScript 用戶端接收 XML DOM 物件。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-123">Doing this with the ASP.NET AJAX framework causes the JavaScript client to receive an XML DOM object.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="b9d1b-124">您的作業必須將內容類型設定為文字/xml，才能讓此作業運作。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-124">Your operation must set the content type to text/xml for this to work.</span></span> <span data-ttu-id="b9d1b-125">否則，JavaScript 用戶端將收到包含 XML 物件 (而非 XML DOM 物件) 的字串。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-125">Otherwise, the JavaScript client will receive a string containing the XML instead of an XML DOM object.</span></span>  
  
     <span data-ttu-id="b9d1b-126">以下是內容類型設定正確時，傳回 XML 資料的範例：</span><span class="sxs-lookup"><span data-stu-id="b9d1b-126">The following is an example of an operation that returns XML data with the content type set appropriately:</span></span>  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   <span data-ttu-id="b9d1b-127">如需與 ASP.NET AJAX 相容，則 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性 (Attribute) 上的其他屬性 (Property) 都將無法變更。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-127">No other properties on the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes can be changed if compatibility with ASP.NET AJAX is required.</span></span> <span data-ttu-id="b9d1b-128">只要不違反 ASP.NET AJAX 呼叫慣例的話，就可以一直使用其他的 Web 程式設計模型方式。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-128">Other aspects of the Web Programming Model can be used as long as the ASP.NET AJAX calling conventions are not violated.</span></span>  
  
 <span data-ttu-id="b9d1b-129">如果是更進階的案例，則您需要了解 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的其他 AJAX 支援詳細資料：</span><span class="sxs-lookup"><span data-stu-id="b9d1b-129">More advanced scenarios require some additional details of AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] be understood:</span></span>  
  
-   <span data-ttu-id="b9d1b-130">若要了解 AJAX 網頁用戶端之間傳送資料的方式和[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務使用 JavaScript 和.NET Framework 型別如何對應至 JavaScript 類型的詳細資訊，請參閱[for JSON 和其他資料傳輸格式的支援](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).</span><span class="sxs-lookup"><span data-stu-id="b9d1b-130">To understand how data is transferred between an AJAX page client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service using JavaScript, and for details on how .NET Framework types map to JavaScript types, see [Support for JSON and Other Data Transfer Formats](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).</span></span>  
  
-   <span data-ttu-id="b9d1b-131">為了善加利用各項 ASP.NET 功能，例如 URL 驗證與存取 ASP.NET 工作階段資訊，您可能會想要透過組態來啟用 ASP.NET 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-131">To take advantage of ASP.NET features, for example, URL-based authentication and accessing the ASP.NET session information, you may want to enable the ASP.NET Compatibility Mode through configuration.</span></span>  
  
 <span data-ttu-id="b9d1b-132">您甚至不需要透過 ASP.NET AJAX 架構，就可以取用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 AJAX 端點。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-132">AJAX endpoints in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] may even be consumed without the ASP.NET AJAX framework.</span></span> <span data-ttu-id="b9d1b-133">要進行這項作業之前，您必須先了解 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 對 AJAX 支援的支援架構。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-133">Doing so requires an understanding of the support architecture of AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="b9d1b-134">如需這個架構的討論，請參閱[WCF Web HTTP 程式設計物件模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-134">For a discussion of this architecture, see [WCF Web HTTP Programming Object Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md).</span></span> <span data-ttu-id="b9d1b-135">如需示範這種方法的程式碼範例，請參閱[含 JSON 和 XML 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-135">For a code sample demonstrating this approach, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d1b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9d1b-136">See Also</span></span>  
 [<span data-ttu-id="b9d1b-137">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="b9d1b-137">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="b9d1b-138">如何： 不使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="b9d1b-138">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [<span data-ttu-id="b9d1b-139">如何： 使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="b9d1b-139">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [<span data-ttu-id="b9d1b-140">如何： 選擇 HTTP POST 和 HTTP GET 要求的 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="b9d1b-140">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
