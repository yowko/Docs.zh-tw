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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9c721a0ef357feeb4df540cb5b7b74d067dc807
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="baeff-102">HOW TO：測試探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="baeff-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="baeff-103">本主題是四個主題中的第四個，示範如何實作探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="baeff-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="baeff-104">在先前的主題， [How to： 實作使用探索 Proxy 來尋找服務的用戶端應用程式](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)，實作您[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]使用探索 proxy 來尋找服務，然後呼叫的用戶端應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="baeff-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="baeff-105">本主題描述如何確認探索 Proxy、服務以及用戶端應用程式如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="baeff-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="baeff-106">執行探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="baeff-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="baeff-107">以系統管理員身分開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="baeff-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="baeff-108">您可能會看見一個對話方塊顯示：Windows 防火牆已封鎖此程式的部分功能。</span><span class="sxs-lookup"><span data-stu-id="baeff-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="baeff-109">如果您看到此訊息，按一下**解除封鎖** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="baeff-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="baeff-110">在命令提示字元內執行探索 Proxy：DiscoveryProxy.exe。</span><span class="sxs-lookup"><span data-stu-id="baeff-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="baeff-111">應用程式應該會顯示下列文字：`Proxy started. Hit Enter to exit`。</span><span class="sxs-lookup"><span data-stu-id="baeff-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="baeff-112">執行可探索的服務</span><span class="sxs-lookup"><span data-stu-id="baeff-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="baeff-113">以系統管理員身分開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="baeff-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="baeff-114">在命令提示字元內執行可探索的服務 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="baeff-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="baeff-115">DiscoveryProxy.exe 應該會顯示下列文字： `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` 。</span><span class="sxs-lookup"><span data-stu-id="baeff-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="baeff-116">執行用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="baeff-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="baeff-117">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="baeff-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="baeff-118">在命令提示字元內執行 client.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="baeff-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="baeff-119">經過幾秒之後，用戶端應用程式會顯示下列文字：Connecting to [Service-Endpoint]。</span><span class="sxs-lookup"><span data-stu-id="baeff-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="baeff-120">接著，service.exe 應該會顯示下列文字：Greeting request received, I will respond。</span><span class="sxs-lookup"><span data-stu-id="baeff-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="baeff-121">然後，client.exe 應該會顯示下列文字：Hello Client!</span><span class="sxs-lookup"><span data-stu-id="baeff-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="baeff-122">關閉應用程式</span><span class="sxs-lookup"><span data-stu-id="baeff-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="baeff-123">關閉用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="baeff-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="baeff-124">關閉服務。</span><span class="sxs-lookup"><span data-stu-id="baeff-124">Shut down the service.</span></span> <span data-ttu-id="baeff-125">探索 Proxy 會顯示下列文字：`******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`。</span><span class="sxs-lookup"><span data-stu-id="baeff-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="baeff-126">關閉探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="baeff-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baeff-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baeff-127">See Also</span></span>  
 [<span data-ttu-id="baeff-128">WCF 探索概觀</span><span class="sxs-lookup"><span data-stu-id="baeff-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="baeff-129">如何： 實作探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="baeff-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="baeff-130">如何： 實作使用探索 Proxy 註冊的可探索服務</span><span class="sxs-lookup"><span data-stu-id="baeff-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="baeff-131">如何： 實作使用探索 Proxy 來尋找服務的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="baeff-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
