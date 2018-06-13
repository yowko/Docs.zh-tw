---
title: 探索路由器服務
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: b98568dd00841b3f2e86ee1fd69390b690e2bf73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500330"
---
# <a name="discovery-router-service"></a><span data-ttu-id="61cec-102">探索路由器服務</span><span class="sxs-lookup"><span data-stu-id="61cec-102">Discovery Router Service</span></span>
<span data-ttu-id="61cec-103">此範例示範如何將探索訊息轉送到其他端點。</span><span class="sxs-lookup"><span data-stu-id="61cec-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="61cec-104">示範</span><span class="sxs-lookup"><span data-stu-id="61cec-104">Demonstrates</span></span>  
 <span data-ttu-id="61cec-105">探索路由</span><span class="sxs-lookup"><span data-stu-id="61cec-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="61cec-106">討論</span><span class="sxs-lookup"><span data-stu-id="61cec-106">Discussion</span></span>  
 <span data-ttu-id="61cec-107">如果用戶端要使用 Proxy 尋找服務，而且 Proxy 不知道此種服務，但知道其他 Proxy，則探索路由相當實用。</span><span class="sxs-lookup"><span data-stu-id="61cec-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="61cec-108">這個 Proxy 可以將探索封包從此用戶端轉送到第二個 Proxy。</span><span class="sxs-lookup"><span data-stu-id="61cec-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="61cec-109">第二個 Proxy 可以尋找服務，並將回應傳回原始用戶端。</span><span class="sxs-lookup"><span data-stu-id="61cec-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="61cec-110">在此範例中，用戶端會將訊息傳送到探索路由元件。</span><span class="sxs-lookup"><span data-stu-id="61cec-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="61cec-111">此訊息會傳送到探索路由器中的特定端點。</span><span class="sxs-lookup"><span data-stu-id="61cec-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="61cec-112">接著，路由器會將訊息轉送至 UDP 多點傳送端點。</span><span class="sxs-lookup"><span data-stu-id="61cec-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="61cec-113">探查訊息會傳出多點傳送端點，而在 UDP 多點傳送位址上接聽的服務，則會回應該探索路由器。</span><span class="sxs-lookup"><span data-stu-id="61cec-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="61cec-114">探索路由器會收集回應，並將其傳送回用戶端。</span><span class="sxs-lookup"><span data-stu-id="61cec-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="61cec-115">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="61cec-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="61cec-116">建置 (Build) 範例。</span><span class="sxs-lookup"><span data-stu-id="61cec-116">Build the sample.</span></span>  
  
2.  <span data-ttu-id="61cec-117">執行 DiscoveryRouter 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="61cec-117">Run the DiscoveryRouter executable.</span></span>  
  
3.  <span data-ttu-id="61cec-118">從組建目錄執行服務的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="61cec-118">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="61cec-119">執行用戶端可執行檔。</span><span class="sxs-lookup"><span data-stu-id="61cec-119">Run the client executable.</span></span> <span data-ttu-id="61cec-120">請注意，用戶端會尋找服務。</span><span class="sxs-lookup"><span data-stu-id="61cec-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="61cec-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="61cec-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="61cec-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="61cec-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="61cec-123">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="61cec-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="61cec-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="61cec-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
