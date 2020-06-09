---
title: 建立 ASP.NET AJAX 的 WCF 服務
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 8c82d4c61b32572fd1ad7d8f19e939273cc2280b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599304"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a><span data-ttu-id="d70c9-102">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="d70c9-102">Creating WCF Services for ASP.NET AJAX</span></span>

<span data-ttu-id="d70c9-103">Microsoft ASP.NET AJAX 可讓您使用反應靈敏和熟悉的使用者介面項目，快速建立包含豐富使用者經驗的 Web 網頁。</span><span class="sxs-lookup"><span data-stu-id="d70c9-103">Microsoft ASP.NET AJAX enables you to quickly create Web pages that include a rich user experience with responsive and familiar user interface elements.</span></span> <span data-ttu-id="d70c9-104">ASP.NET AJAX 提供用戶端指令碼的程式庫，其中加入跨平台的 ECMAScript (JavaScript) 和動態 HTML (DHTML) 技術，並將它們與 ASP.NET 2.0 伺服器基礎的開發平台整合。</span><span class="sxs-lookup"><span data-stu-id="d70c9-104">ASP.NET AJAX provides client-script libraries that incorporate cross-browser ECMAScript (JavaScript) and dynamic HTML (DHTML) technologies, and it integrates them with the ASP.NET 2.0 server-based development platform.</span></span> <span data-ttu-id="d70c9-105">您可以使用 ASP.NET AJAX 功能來改善使用者經驗和 Web 應用程式的效率。</span><span class="sxs-lookup"><span data-stu-id="d70c9-105">By using ASP.NET AJAX, you can improve the user experience and the efficiency of your Web applications.</span></span>

<span data-ttu-id="d70c9-106">ASP.NET AJAX 包含內建的用戶端指令碼程式庫與伺服器元件，以提供您穩固的開發架構。</span><span class="sxs-lookup"><span data-stu-id="d70c9-106">ASP.NET AJAX consists of client-script libraries and of server components that are integrated to provide a robust development framework.</span></span> <span data-ttu-id="d70c9-107">若要從 ASP.NET 頁面存取服務：一旦服務 URL 新增至頁面上的 ASP.NET 指令碼管理員控制項，服務作業可能會透過看起來與正常 JavaScript 函式呼叫沒兩樣的 JavaScript 程式碼來叫用。</span><span class="sxs-lookup"><span data-stu-id="d70c9-107">To access a service from an ASP.NET page: once the service URL is added to the ASP.NET Script Manager control on the page, service operations may be invoked using JavaScript code that looks exactly like a regular JavaScript function call.</span></span>

<span data-ttu-id="d70c9-108">大部分的 Windows Communication Foundation （WCF）服務可能會藉由新增適當的 ASP.NET AJAX 端點，公開為與 ASP.NET AJAX 相容的服務。</span><span class="sxs-lookup"><span data-stu-id="d70c9-108">Most Windows Communication Foundation (WCF) services may be exposed as a service compatible with ASP.NET AJAX by adding an appropriate ASP.NET AJAX endpoint.</span></span>

<span data-ttu-id="d70c9-109">如果您使用 Visual Studio，您可以針對啟用 AJAX 的 WCF 服務使用預先建立的範本，在使用 ASP.NET 網站或 Web 應用程式時，可以在 [**加入新專案**] 對話方塊中找到。</span><span class="sxs-lookup"><span data-stu-id="d70c9-109">If you are using Visual Studio, you may use a pre-built template for AJAX-enabled WCF services, available in the **Add New Item** dialog when working with ASP.NET Web Sites or Web Applications.</span></span>

<span data-ttu-id="d70c9-110">如果您不是使用 Visual Studio 範本，則您可以透過下列兩種方法來建立 ASP.NET AJAX 端點：</span><span class="sxs-lookup"><span data-stu-id="d70c9-110">If you are not using the Visual Studio templates, there are two ways to create an ASP.NET AJAX endpoint:</span></span>

- <span data-ttu-id="d70c9-111">使用動態主機啟動 (而不是透過任何組態) 來建立端點。</span><span class="sxs-lookup"><span data-stu-id="d70c9-111">Create the endpoint using dynamic host activation without using any configuration.</span></span> <span data-ttu-id="d70c9-112">如果您不熟悉 WCF 組態系統的話，這是最基本的操作方式。</span><span class="sxs-lookup"><span data-stu-id="d70c9-112">This is the most basic approach if you are unfamiliar with the WCF configuration system.</span></span> <span data-ttu-id="d70c9-113">如需詳細資訊，請參閱[如何：新增 ASP.NET AJAX 端點而不使用](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)設定。</span><span class="sxs-lookup"><span data-stu-id="d70c9-113">For more information, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>

- <span data-ttu-id="d70c9-114">使用設定，將啟用 AJAX 的端點新增至 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="d70c9-114">Add an AJAX-enabled endpoint to a WCF service using configuration.</span></span> <span data-ttu-id="d70c9-115">如需詳細資訊，請參閱[如何：使用設定來新增 ASP.NET AJAX 端點](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="d70c9-115">For more information, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>

<span data-ttu-id="d70c9-116">[WCF WEB HTTP 程式設計模型總覽](wcf-web-http-programming-model-overview.md)中所述的 Web 程式設計模型，可搭配 ASP.NET AJAX services 使用。</span><span class="sxs-lookup"><span data-stu-id="d70c9-116">The Web Programming Model described in the [WCF Web HTTP Programming Model Overview](wcf-web-http-programming-model-overview.md) may be used with ASP.NET AJAX services.</span></span> <span data-ttu-id="d70c9-117">具體來說：</span><span class="sxs-lookup"><span data-stu-id="d70c9-117">Specifically:</span></span>

- <span data-ttu-id="d70c9-118">您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性，在 HTTP GET 和 HTTP POST 動詞之間進行選擇。</span><span class="sxs-lookup"><span data-stu-id="d70c9-118">You can use the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to select between HTTP GET and HTTP POST verbs.</span></span> <span data-ttu-id="d70c9-119">如果使用方式正確的話，可能會大幅改善應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="d70c9-119">If used correctly, this may significantly improve your application’s performance.</span></span> <span data-ttu-id="d70c9-120">如需詳細資訊，請參閱 how [to：選擇 HTTP POST 和 HTTP GET 要求以 ASP.NET AJAX 端點](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="d70c9-120">For more information, see [How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).</span></span>

- <span data-ttu-id="d70c9-121">您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> 屬性，讓您的服務傳回 XML 資料，而不是預設的 JavaScript Object Notation (JSON)。</span><span class="sxs-lookup"><span data-stu-id="d70c9-121">You can use the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> and <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> properties to cause your service to return XML data instead of the default JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="d70c9-122">使用 ASP.NET AJAX 架構來執行這項作業會導致 JavaScript 用戶端接收 XML DOM 物件。</span><span class="sxs-lookup"><span data-stu-id="d70c9-122">Doing this with the ASP.NET AJAX framework causes the JavaScript client to receive an XML DOM object.</span></span>

  > [!WARNING]
  > <span data-ttu-id="d70c9-123">您的作業必須將內容類型設定為文字/xml，才能讓此作業運作。</span><span class="sxs-lookup"><span data-stu-id="d70c9-123">Your operation must set the content type to text/xml for this to work.</span></span> <span data-ttu-id="d70c9-124">否則，JavaScript 用戶端將收到包含 XML 物件 (而非 XML DOM 物件) 的字串。</span><span class="sxs-lookup"><span data-stu-id="d70c9-124">Otherwise, the JavaScript client will receive a string containing the XML instead of an XML DOM object.</span></span>

    <span data-ttu-id="d70c9-125">以下是內容類型設定正確時，傳回 XML 資料的範例：</span><span class="sxs-lookup"><span data-stu-id="d70c9-125">The following is an example of an operation that returns XML data with the content type set appropriately:</span></span>

  ```csharp
  [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]
  public XElement GetData()
  {
      XElement x;
      //Get some data here...

      WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";
      return x;
  }
  ```

- <span data-ttu-id="d70c9-126">如需與 ASP.NET AJAX 相容，則 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性 (Attribute) 上的其他屬性 (Property) 都將無法變更。</span><span class="sxs-lookup"><span data-stu-id="d70c9-126">No other properties on the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes can be changed if compatibility with ASP.NET AJAX is required.</span></span> <span data-ttu-id="d70c9-127">只要不違反 ASP.NET AJAX 呼叫慣例的話，就可以一直使用其他的 Web 程式設計模型方式。</span><span class="sxs-lookup"><span data-stu-id="d70c9-127">Other aspects of the Web Programming Model can be used as long as the ASP.NET AJAX calling conventions are not violated.</span></span>

 <span data-ttu-id="d70c9-128">更先進的案例需要瞭解 WCF 中的其他 AJAX 支援詳細資料：</span><span class="sxs-lookup"><span data-stu-id="d70c9-128">More advanced scenarios require some additional details of AJAX support in WCF be understood:</span></span>

- <span data-ttu-id="d70c9-129">若要瞭解如何使用 JavaScript 在 AJAX 頁面用戶端與 WCF 服務之間傳輸資料，以及有關 .NET Framework 類型如何對應至 JavaScript 類型的詳細資訊，請參閱[JSON 和其他資料傳輸格式的支援](support-for-json-and-other-data-transfer-formats.md)。</span><span class="sxs-lookup"><span data-stu-id="d70c9-129">To understand how data is transferred between an AJAX page client and a WCF service using JavaScript, and for details on how .NET Framework types map to JavaScript types, see [Support for JSON and Other Data Transfer Formats](support-for-json-and-other-data-transfer-formats.md).</span></span>

- <span data-ttu-id="d70c9-130">為了善加利用各項 ASP.NET 功能，例如 URL 驗證與存取 ASP.NET 工作階段資訊，您可能會想要透過組態來啟用 ASP.NET 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="d70c9-130">To take advantage of ASP.NET features, for example, URL-based authentication and accessing the ASP.NET session information, you may want to enable the ASP.NET Compatibility Mode through configuration.</span></span>

<span data-ttu-id="d70c9-131">WCF 中的 AJAX 端點甚至可能會在沒有 ASP.NET AJAX 架構的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="d70c9-131">AJAX endpoints in WCF may even be consumed without the ASP.NET AJAX framework.</span></span> <span data-ttu-id="d70c9-132">這麼做需要瞭解 WCF 中 AJAX 支援的支援架構。</span><span class="sxs-lookup"><span data-stu-id="d70c9-132">Doing so requires an understanding of the support architecture of AJAX support in WCF.</span></span> <span data-ttu-id="d70c9-133">如需此架構的討論，請參閱[WCF WEB HTTP 程式設計物件模型](wcf-web-http-programming-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d70c9-133">For a discussion of this architecture, see [WCF Web HTTP Programming Object Model](wcf-web-http-programming-object-model.md).</span></span> <span data-ttu-id="d70c9-134">如需示範此方法的程式碼範例，請參閱[使用 JSON 和 XML 的 AJAX 服務](../samples/ajax-service-with-json-and-xml-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="d70c9-134">For a code sample demonstrating this approach, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d70c9-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="d70c9-135">See also</span></span>

- [<span data-ttu-id="d70c9-136">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="d70c9-136">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="d70c9-137">如何：不使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="d70c9-137">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [<span data-ttu-id="d70c9-138">如何：使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="d70c9-138">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [<span data-ttu-id="d70c9-139">HOW TO：在 ASP.NET AJAX 端點的 HTTP POST 和 HTTP GET 要求之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="d70c9-139">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
