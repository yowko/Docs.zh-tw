---
title: WCF 新聞訂閱
ms.date: 03/30/2017
helpviewer_keywords:
- syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
ms.openlocfilehash: 677e8a4b00b36c2f11b27eb65d57be8abf75d6d2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600642"
---
# <a name="wcf-syndication"></a><span data-ttu-id="54a20-102">WCF 新聞訂閱</span><span class="sxs-lookup"><span data-stu-id="54a20-102">WCF Syndication</span></span>
<span data-ttu-id="54a20-103">Windows Communication Foundation （WCF）提供的支援可讓您輕鬆地使用 Atom、RSS 或其他自訂格式的新聞訂閱摘要，其可讓您讀取和建立這些摘要，以及在服務端點上加以公開。</span><span class="sxs-lookup"><span data-stu-id="54a20-103">Windows Communication Foundation (WCF) provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="54a20-104">本節的各主題會詳細描述新聞訂閱的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="54a20-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54a20-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="54a20-105">In This Section</span></span>  
 [<span data-ttu-id="54a20-106">WCF 新聞訂閱概觀</span><span class="sxs-lookup"><span data-stu-id="54a20-106">WCF Syndication Overview</span></span>](wcf-syndication-overview.md)  
 <span data-ttu-id="54a20-107">提供 WCF 提供之新聞訂閱支援的總覽。</span><span class="sxs-lookup"><span data-stu-id="54a20-107">Provides an overview of syndication support provided by WCF.</span></span>  
  
 [<span data-ttu-id="54a20-108">摘要整合架構</span><span class="sxs-lookup"><span data-stu-id="54a20-108">Architecture of Syndication</span></span>](architecture-of-syndication.md)  
 <span data-ttu-id="54a20-109">描述物件模型中的類別以及新聞訂閱的可擴充性。</span><span class="sxs-lookup"><span data-stu-id="54a20-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="54a20-110">WCF 新聞訂閱物件模型對應到 Atom 和 RSS 的方式</span><span class="sxs-lookup"><span data-stu-id="54a20-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="54a20-111">描述摘要在 WCF 新聞訂閱物件模型中的呈現方式，以及轉換至 RSS 和 Atom 摘要的方法。</span><span class="sxs-lookup"><span data-stu-id="54a20-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="54a20-112">HOW TO：建立基本 RSS 摘要</span><span class="sxs-lookup"><span data-stu-id="54a20-112">How to: Create a Basic RSS Feed</span></span>](how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="54a20-113">顯示如何建立可產生基本 RSS 摘要的服務。</span><span class="sxs-lookup"><span data-stu-id="54a20-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="54a20-114">HOW TO：建立基本 Atom 摘要</span><span class="sxs-lookup"><span data-stu-id="54a20-114">How to: Create a Basic Atom Feed</span></span>](how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="54a20-115">顯示如何建立可產生基本 ATOM 摘要的服務。</span><span class="sxs-lookup"><span data-stu-id="54a20-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="54a20-116">HOW TO：將摘要同時公開為 Atom 和 RSS</span><span class="sxs-lookup"><span data-stu-id="54a20-116">How to: Expose a Feed as Both Atom and RSS</span></span>](how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="54a20-117">顯示如何建立可產生 ATOM 和 RSS 相同摘要的服務。</span><span class="sxs-lookup"><span data-stu-id="54a20-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="54a20-118">摘要整合擴充性</span><span class="sxs-lookup"><span data-stu-id="54a20-118">Syndication Extensibility</span></span>](syndication-extensibility.md)  
 <span data-ttu-id="54a20-119">說明將自訂項目和屬性加入至新聞訂閱摘要的方法。</span><span class="sxs-lookup"><span data-stu-id="54a20-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="54a20-120">參考</span><span class="sxs-lookup"><span data-stu-id="54a20-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="54a20-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="54a20-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a20-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="54a20-122">See also</span></span>

- [<span data-ttu-id="54a20-123">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="54a20-123">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="54a20-124">部分信任</span><span class="sxs-lookup"><span data-stu-id="54a20-124">Partial Trust</span></span>](partial-trust.md)
