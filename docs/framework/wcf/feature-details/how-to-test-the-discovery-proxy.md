---
title: "HOW TO：測試探索 Proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55a7fe72b34fc8c099d921e7e295c184817825a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="2266e-102">HOW TO：測試探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="2266e-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="2266e-103">本主題是四個主題中的第四個，示範如何實作探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="2266e-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="2266e-104">在先前的主題， [How to： 實作使用探索 Proxy 來尋找服務的用戶端應用程式](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)，實作您[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]使用探索 proxy 來尋找服務，然後呼叫的用戶端應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="2266e-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="2266e-105">本主題描述如何確認探索 Proxy、服務以及用戶端應用程式如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="2266e-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="2266e-106">執行探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="2266e-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="2266e-107">以系統管理員身分開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="2266e-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="2266e-108">您可能會看見一個對話方塊顯示：Windows 防火牆已封鎖此程式的部分功能。</span><span class="sxs-lookup"><span data-stu-id="2266e-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="2266e-109">如果您看到此訊息，按一下**解除封鎖** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2266e-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="2266e-110">在命令提示字元內執行探索 Proxy：DiscoveryProxy.exe。</span><span class="sxs-lookup"><span data-stu-id="2266e-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="2266e-111">應用程式應該會顯示下列文字：`Proxy started. Hit Enter to exit`。</span><span class="sxs-lookup"><span data-stu-id="2266e-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="2266e-112">執行可探索的服務</span><span class="sxs-lookup"><span data-stu-id="2266e-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="2266e-113">以系統管理員身分開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="2266e-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="2266e-114">在命令提示字元內執行可探索的服務 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="2266e-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="2266e-115">DiscoveryProxy.exe 應該會顯示下列文字： `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` 。</span><span class="sxs-lookup"><span data-stu-id="2266e-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="2266e-116">執行用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="2266e-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="2266e-117">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="2266e-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="2266e-118">在命令提示字元內執行 client.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2266e-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="2266e-119">經過幾秒之後，用戶端應用程式會顯示下列文字：Connecting to [Service-Endpoint]。</span><span class="sxs-lookup"><span data-stu-id="2266e-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="2266e-120">接著，service.exe 應該會顯示下列文字：Greeting request received, I will respond。</span><span class="sxs-lookup"><span data-stu-id="2266e-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="2266e-121">然後，client.exe 應該會顯示下列文字：Hello Client!</span><span class="sxs-lookup"><span data-stu-id="2266e-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="2266e-122">關閉應用程式</span><span class="sxs-lookup"><span data-stu-id="2266e-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="2266e-123">關閉用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="2266e-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="2266e-124">關閉服務。</span><span class="sxs-lookup"><span data-stu-id="2266e-124">Shut down the service.</span></span> <span data-ttu-id="2266e-125">探索 Proxy 會顯示下列文字：`******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`。</span><span class="sxs-lookup"><span data-stu-id="2266e-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="2266e-126">關閉探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="2266e-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2266e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2266e-127">See Also</span></span>  
 [<span data-ttu-id="2266e-128">WCF 探索概觀</span><span class="sxs-lookup"><span data-stu-id="2266e-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="2266e-129">如何： 實作探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="2266e-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="2266e-130">如何： 實作使用探索 Proxy 註冊的可探索服務</span><span class="sxs-lookup"><span data-stu-id="2266e-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="2266e-131">如何： 實作使用探索 Proxy 來尋找服務的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="2266e-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
