---
title: HOW TO：將摘要同時公開為 Atom 和 RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 6b26dabb9ed5c2c7bb2410dc1e844add6a69bdf3
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842719"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="427e4-102">HOW TO：將摘要同時公開為 Atom 和 RSS</span><span class="sxs-lookup"><span data-stu-id="427e4-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="427e4-103">Windows Communication Foundation (WCF) 可讓您建立公開新聞訂閱摘要的服務。</span><span class="sxs-lookup"><span data-stu-id="427e4-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="427e4-104">本主題討論如何同時使用 Atom 1.0 和 RSS 2.0，建立可公開新聞訂閱摘要的新聞訂閱服務。</span><span class="sxs-lookup"><span data-stu-id="427e4-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="427e4-105">此服務會公開可傳回任何一種新聞訂閱格式的端點。</span><span class="sxs-lookup"><span data-stu-id="427e4-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="427e4-106">為了簡要說明，此範例中使用的服務為自我裝載。</span><span class="sxs-lookup"><span data-stu-id="427e4-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="427e4-107">在實際執行環境中，此類型的服務會在 IIS 或 WAS 下裝載。</span><span class="sxs-lookup"><span data-stu-id="427e4-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="427e4-108">如需有關不同的 WCF 裝載選項的詳細資訊，請參閱[Hosting](../../../../docs/framework/wcf/feature-details/hosting.md)。</span><span class="sxs-lookup"><span data-stu-id="427e4-108">For more information about the different WCF hosting options, see [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="427e4-109">若要建立基本新聞訂閱服務</span><span class="sxs-lookup"><span data-stu-id="427e4-109">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="427e4-110">使用以 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性標記的介面來定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="427e4-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="427e4-111">每個公開為新聞訂閱摘要的作業，都會傳回 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 物件。</span><span class="sxs-lookup"><span data-stu-id="427e4-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="427e4-112">請注意 <xref:System.ServiceModel.Web.WebGetAttribute> 的參數。</span><span class="sxs-lookup"><span data-stu-id="427e4-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="427e4-113">`UriTemplate` 會指定用來叫用此服務作業的 URL。</span><span class="sxs-lookup"><span data-stu-id="427e4-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="427e4-114">此參數的字串包含常值和變數，以大括號 ({*格式*})。</span><span class="sxs-lookup"><span data-stu-id="427e4-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="427e4-115">此變數對應至服務作業的 `format` 參數。</span><span class="sxs-lookup"><span data-stu-id="427e4-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="427e4-116">如需詳細資訊，請參閱<xref:System.UriTemplate>。</span><span class="sxs-lookup"><span data-stu-id="427e4-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="427e4-117">`BodyStyle` 會影響此服務作業所傳送與接收之訊息的寫入方式。</span><span class="sxs-lookup"><span data-stu-id="427e4-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="427e4-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> 會指定傳送至此服務作業，以及來自此服務作業的資料都不得透過基礎結構定義的 XML 元素來包裝。</span><span class="sxs-lookup"><span data-stu-id="427e4-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="427e4-119">如需詳細資訊，請參閱<xref:System.ServiceModel.Web.WebMessageBodyStyle>。</span><span class="sxs-lookup"><span data-stu-id="427e4-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="427e4-120">請使用 <xref:System.ServiceModel.ServiceKnownTypeAttribute> 來指定此介面中由服務作業所傳回的型別。</span><span class="sxs-lookup"><span data-stu-id="427e4-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2.  <span data-ttu-id="427e4-121">實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="427e4-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  <span data-ttu-id="427e4-122">建立 <xref:System.ServiceModel.Syndication.SyndicationFeed> 物件並新增作者、分類和描述。</span><span class="sxs-lookup"><span data-stu-id="427e4-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  <span data-ttu-id="427e4-123">建立幾個 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件。</span><span class="sxs-lookup"><span data-stu-id="427e4-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  <span data-ttu-id="427e4-124">新增 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件至摘要。</span><span class="sxs-lookup"><span data-stu-id="427e4-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  <span data-ttu-id="427e4-125">使用格式參數來傳回要求的格式。</span><span class="sxs-lookup"><span data-stu-id="427e4-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="427e4-126">若要裝載服務</span><span class="sxs-lookup"><span data-stu-id="427e4-126">To host the service</span></span>  
  
1.  <span data-ttu-id="427e4-127">建立 <xref:System.ServiceModel.Web.WebServiceHost> 物件。</span><span class="sxs-lookup"><span data-stu-id="427e4-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="427e4-128">除非在程式碼或組態中指定端點，否則 <xref:System.ServiceModel.Web.WebServiceHost> 類別會在服務的基底位址上自動加入端點。</span><span class="sxs-lookup"><span data-stu-id="427e4-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="427e4-129">在這個範例中，沒有指定端點，因此會公開預設端點。</span><span class="sxs-lookup"><span data-stu-id="427e4-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  <span data-ttu-id="427e4-130">開啟服務主機、從服務載入摘要、顯示摘要，並等候使用者按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="427e4-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="427e4-131">若要使用 HTTP GET 呼叫 GetBlog</span><span class="sxs-lookup"><span data-stu-id="427e4-131">To call GetBlog with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="427e4-132">開啟 Internet Explorer 中，輸入下列 URL，然後按 ENTER: `http://localhost:8000/BlogService/GetBlog`。</span><span class="sxs-lookup"><span data-stu-id="427e4-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="427e4-133">URL 包含服務的基底位址 (`http://localhost:8000/BlogService`)，端點，並呼叫服務作業的相對位址。</span><span class="sxs-lookup"><span data-stu-id="427e4-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="427e4-134">若要從程式碼呼叫 GetBlog()</span><span class="sxs-lookup"><span data-stu-id="427e4-134">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="427e4-135">使用基底位址與您要呼叫的方法建立 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="427e4-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="427e4-136">呼叫靜態 <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> 方法，傳入剛才建立的 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="427e4-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="427e4-137">這會叫用服務作業，並在新的 <xref:System.ServiceModel.Syndication.SyndicationFeed> 中填入服務作業所傳回的格式器。</span><span class="sxs-lookup"><span data-stu-id="427e4-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="427e4-138">存取摘要物件。</span><span class="sxs-lookup"><span data-stu-id="427e4-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="427e4-139">範例</span><span class="sxs-lookup"><span data-stu-id="427e4-139">Example</span></span>  
 <span data-ttu-id="427e4-140">以下是這個範例的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="427e4-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="427e4-141">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="427e4-141">Compiling the Code</span></span>  
 <span data-ttu-id="427e4-142">在編譯先前的程式碼時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。</span><span class="sxs-lookup"><span data-stu-id="427e4-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="427e4-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="427e4-143">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
