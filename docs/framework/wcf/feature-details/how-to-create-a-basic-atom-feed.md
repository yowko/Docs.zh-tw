---
title: "HOW TO：建立基本 Atom 摘要"
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
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 937e879fc6104f06234ab5201eae8e330dbb68f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="386b6-102">HOW TO：建立基本 Atom 摘要</span><span class="sxs-lookup"><span data-stu-id="386b6-102">How to: Create a Basic Atom Feed</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="386b6-103"> 可以讓您建立公開新聞訂閱摘要的服務。</span><span class="sxs-lookup"><span data-stu-id="386b6-103"> allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="386b6-104">本主題討論如何建立可公開 Atom 新聞訂閱摘要的新聞訂閱服務。</span><span class="sxs-lookup"><span data-stu-id="386b6-104">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="386b6-105">若要建立基本新聞訂閱服務</span><span class="sxs-lookup"><span data-stu-id="386b6-105">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="386b6-106">使用以 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性標記的介面來定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="386b6-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="386b6-107">每個公開為新聞訂閱摘要的作業都應該傳回 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> 物件。</span><span class="sxs-lookup"><span data-stu-id="386b6-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="386b6-108">所有套用 <xref:System.ServiceModel.Web.WebGetAttribute> 的服務作業都會對應至 HTTP GET 要求。</span><span class="sxs-lookup"><span data-stu-id="386b6-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="386b6-109">若要將您的作業對應至不同的 HTTP 方法，請改用 <xref:System.ServiceModel.Web.WebInvokeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="386b6-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="386b6-110">[How to： 建立基本 WCF Web HTTP 服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)。</span><span class="sxs-lookup"><span data-stu-id="386b6-110"> [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2.  <span data-ttu-id="386b6-111">實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="386b6-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3.  <span data-ttu-id="386b6-112">建立 <xref:System.ServiceModel.Syndication.SyndicationFeed> 物件並新增作者、分類和描述。</span><span class="sxs-lookup"><span data-stu-id="386b6-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4.  <span data-ttu-id="386b6-113">建立幾個 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件。</span><span class="sxs-lookup"><span data-stu-id="386b6-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5.  <span data-ttu-id="386b6-114">新增 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件至摘要。</span><span class="sxs-lookup"><span data-stu-id="386b6-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6.  <span data-ttu-id="386b6-115">傳回摘要。</span><span class="sxs-lookup"><span data-stu-id="386b6-115">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="386b6-116">若要裝載服務</span><span class="sxs-lookup"><span data-stu-id="386b6-116">To host the service</span></span>  
  
1.  <span data-ttu-id="386b6-117">建立 <xref:System.ServiceModel.Web.WebServiceHost> 物件。</span><span class="sxs-lookup"><span data-stu-id="386b6-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2.  <span data-ttu-id="386b6-118">開啟服務主機、從服務載入摘要、顯示摘要，並等候使用者按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="386b6-118">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="386b6-119">若要使用 HTTP GET 呼叫 GetBlog()</span><span class="sxs-lookup"><span data-stu-id="386b6-119">To call GetBlog() with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="386b6-120">開啟 Internet Explorer 並輸入下列 URL，然後按下 ENTER：http://localhost:8000/BlogService/GetBlog</span><span class="sxs-lookup"><span data-stu-id="386b6-120">Open Internet Explorer, type the following URL, and press ENTER: http://localhost:8000/BlogService/GetBlog</span></span>  
  
     <span data-ttu-id="386b6-121">URL 包含服務的基底位址 (http://localhost:8000/BlogService)、端點的相對位址，以及要呼叫的服務作業。</span><span class="sxs-lookup"><span data-stu-id="386b6-121">The URL contains the base address of the service (http://localhost:8000/BlogService), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="386b6-122">若要從程式碼呼叫 GetBlog()</span><span class="sxs-lookup"><span data-stu-id="386b6-122">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="386b6-123">使用基底位址與您要呼叫的方法建立 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="386b6-123">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="386b6-124">呼叫靜態 <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> 方法，傳入剛才建立的 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="386b6-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="386b6-125">這會叫用服務作業，並在新的 <xref:System.ServiceModel.Syndication.SyndicationFeed> 中填入服務作業所傳回的格式器。</span><span class="sxs-lookup"><span data-stu-id="386b6-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="386b6-126">存取摘要物件。</span><span class="sxs-lookup"><span data-stu-id="386b6-126">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="386b6-127">範例</span><span class="sxs-lookup"><span data-stu-id="386b6-127">Example</span></span>  
 <span data-ttu-id="386b6-128">以下是這個範例的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="386b6-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="386b6-129">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="386b6-129">Compiling the Code</span></span>  
 <span data-ttu-id="386b6-130">在編譯先前的程式碼時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。</span><span class="sxs-lookup"><span data-stu-id="386b6-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="386b6-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="386b6-131">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
