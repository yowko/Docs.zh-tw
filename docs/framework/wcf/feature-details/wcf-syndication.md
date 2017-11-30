---
title: "WCF 新聞訂閱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 51cf7c6e4db1ee0ff68bcc7fccb46fd643f04bf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-syndication"></a><span data-ttu-id="2abbc-102">WCF 新聞訂閱</span><span class="sxs-lookup"><span data-stu-id="2abbc-102">WCF Syndication</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="2abbc-103"> 提供的支援可讓您輕鬆使用 Atom、RSS 或其他自訂格式的新聞訂閱摘要，並且可讓您讀取和建立這些摘要，以及在服務端點上公開 (Expose) 這些摘要。</span><span class="sxs-lookup"><span data-stu-id="2abbc-103"> provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="2abbc-104">本節的各主題會詳細描述新聞訂閱的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="2abbc-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2abbc-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="2abbc-105">In This Section</span></span>  
 [<span data-ttu-id="2abbc-106">WCF 新聞訂閱概觀</span><span class="sxs-lookup"><span data-stu-id="2abbc-106">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 <span data-ttu-id="2abbc-107">提供 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供之新聞訂閱支援的概觀。</span><span class="sxs-lookup"><span data-stu-id="2abbc-107">Provides an overview of syndication support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="2abbc-108">新聞訂閱架構</span><span class="sxs-lookup"><span data-stu-id="2abbc-108">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 <span data-ttu-id="2abbc-109">描述物件模型中的類別以及新聞訂閱的可擴充性。</span><span class="sxs-lookup"><span data-stu-id="2abbc-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="2abbc-110">WCF 新聞訂閱物件模型如何對應至 Atom 和 RSS</span><span class="sxs-lookup"><span data-stu-id="2abbc-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="2abbc-111">描述摘要在 WCF 新聞訂閱物件模型中的呈現方式，以及轉換至 RSS 和 Atom 摘要的方法。</span><span class="sxs-lookup"><span data-stu-id="2abbc-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="2abbc-112">如何： 建立基本 RSS 摘要</span><span class="sxs-lookup"><span data-stu-id="2abbc-112">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="2abbc-113">顯示如何建立可產生基本 RSS 摘要的服務。</span><span class="sxs-lookup"><span data-stu-id="2abbc-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="2abbc-114">如何： 建立基本 Atom 摘要</span><span class="sxs-lookup"><span data-stu-id="2abbc-114">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="2abbc-115">顯示如何建立可產生基本 ATOM 摘要的服務。</span><span class="sxs-lookup"><span data-stu-id="2abbc-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="2abbc-116">如何： 公開的摘要為這兩個 Atom 和 RSS</span><span class="sxs-lookup"><span data-stu-id="2abbc-116">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="2abbc-117">顯示如何建立可產生 ATOM 和 RSS 相同摘要的服務。</span><span class="sxs-lookup"><span data-stu-id="2abbc-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="2abbc-118">新聞訂閱擴充性</span><span class="sxs-lookup"><span data-stu-id="2abbc-118">Syndication Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md)  
 <span data-ttu-id="2abbc-119">說明將自訂項目和屬性加入至新聞訂閱摘要的方法。</span><span class="sxs-lookup"><span data-stu-id="2abbc-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2abbc-120">參考資料</span><span class="sxs-lookup"><span data-stu-id="2abbc-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2abbc-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="2abbc-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abbc-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2abbc-122">See Also</span></span>  
 [<span data-ttu-id="2abbc-123">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="2abbc-123">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="2abbc-124">部分信任</span><span class="sxs-lookup"><span data-stu-id="2abbc-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)
