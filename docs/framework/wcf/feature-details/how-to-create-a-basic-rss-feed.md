---
title: "HOW TO：建立基本 RSS 摘要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54b9932e081ab5f35b3c15c9e7d4025dfbb3703b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-basic-rss-feed"></a><span data-ttu-id="fa56c-102">HOW TO：建立基本 RSS 摘要</span><span class="sxs-lookup"><span data-stu-id="fa56c-102">How to: Create a Basic RSS Feed</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="fa56c-103"> 可以讓您建立公開新聞訂閱摘要的服務。</span><span class="sxs-lookup"><span data-stu-id="fa56c-103"> allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="fa56c-104">本主題討論如何建立可公開 RSS 新聞訂閱摘要的新聞訂閱服務。</span><span class="sxs-lookup"><span data-stu-id="fa56c-104">This topic discusses how to create a syndication service that exposes an RSS syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="fa56c-105">若要建立基本新聞訂閱服務</span><span class="sxs-lookup"><span data-stu-id="fa56c-105">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="fa56c-106">使用以 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性標記的介面來定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="fa56c-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="fa56c-107">每個公開為新聞訂閱摘要的作業都應該傳回 <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> 物件。</span><span class="sxs-lookup"><span data-stu-id="fa56c-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> object.</span></span>  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="fa56c-108">所有套用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性的服務作業都會對應至 HTTP GET 要求。</span><span class="sxs-lookup"><span data-stu-id="fa56c-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> attribute are mapped to HTTP GET requests.</span></span> <span data-ttu-id="fa56c-109">若要將您的作業對應至不同的 HTTP 方法，請改用 <xref:System.ServiceModel.Web.WebInvokeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="fa56c-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="fa56c-110">[How to： 建立基本 WCF Web HTTP 服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)。</span><span class="sxs-lookup"><span data-stu-id="fa56c-110"> [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2.  <span data-ttu-id="fa56c-111">實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="fa56c-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3.  <span data-ttu-id="fa56c-112">建立 <xref:System.ServiceModel.Syndication.SyndicationFeed> 物件並新增作者、分類和描述。</span><span class="sxs-lookup"><span data-stu-id="fa56c-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4.  <span data-ttu-id="fa56c-113">建立幾個 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件。</span><span class="sxs-lookup"><span data-stu-id="fa56c-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5.  <span data-ttu-id="fa56c-114">將 <xref:System.ServiceModel.Syndication.SyndicationItem> 加入至摘要。</span><span class="sxs-lookup"><span data-stu-id="fa56c-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> to the feed.</span></span>  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6.  <span data-ttu-id="fa56c-115">傳回摘要。</span><span class="sxs-lookup"><span data-stu-id="fa56c-115">Return the feed.</span></span>  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a><span data-ttu-id="fa56c-116">若要裝載服務</span><span class="sxs-lookup"><span data-stu-id="fa56c-116">To host a service</span></span>  
  
1.  <span data-ttu-id="fa56c-117">建立 <xref:System.ServiceModel.Web.WebServiceHost> 物件。</span><span class="sxs-lookup"><span data-stu-id="fa56c-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2.  <span data-ttu-id="fa56c-118">開啟服務主機並等候使用者按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="fa56c-118">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="fa56c-119">若要使用 HTTP GET 呼叫 GetBlog()</span><span class="sxs-lookup"><span data-stu-id="fa56c-119">To call GetBlog() with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="fa56c-120">開啟 Internet Explorer 並輸入下列 URL，然後按下 ENTER：http://localhost:8000/BlogService/GetBlog。</span><span class="sxs-lookup"><span data-stu-id="fa56c-120">Open Internet Explorer, type the following URL, and press ENTER: http://localhost:8000/BlogService/GetBlog.</span></span> <span data-ttu-id="fa56c-121">URL 包含服務的基底位址 (http://localhost:8000/BlogService)、端點的相對位址，以及要呼叫的服務作業。</span><span class="sxs-lookup"><span data-stu-id="fa56c-121">The URL contains the base address of the service (http://localhost:8000/BlogService), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="fa56c-122">若要從程式碼呼叫 GetBlog()</span><span class="sxs-lookup"><span data-stu-id="fa56c-122">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="fa56c-123">使用基底位址與您要呼叫的方法建立 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="fa56c-123">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="fa56c-124">呼叫靜態 <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> 方法，傳入剛才建立的 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="fa56c-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="fa56c-125">這會叫用服務作業，並在新的 <xref:System.ServiceModel.Syndication.SyndicationFeed> 中填入服務作業所傳回的格式器。</span><span class="sxs-lookup"><span data-stu-id="fa56c-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="fa56c-126">存取摘要物件。</span><span class="sxs-lookup"><span data-stu-id="fa56c-126">Access the feed object.</span></span>  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="fa56c-127">範例</span><span class="sxs-lookup"><span data-stu-id="fa56c-127">Example</span></span>  
 <span data-ttu-id="fa56c-128">以下是這個範例的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="fa56c-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa56c-129">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fa56c-129">Compiling the Code</span></span>  
 <span data-ttu-id="fa56c-130">在編譯先前的程式碼時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。</span><span class="sxs-lookup"><span data-stu-id="fa56c-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa56c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa56c-131">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
