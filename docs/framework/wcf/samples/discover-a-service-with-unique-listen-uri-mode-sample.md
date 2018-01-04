---
title: "使用唯一的接聽 URI 模式探索服務範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 017a14794dfb2cb2c49cc32df038600a984acf3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a><span data-ttu-id="6b316-102">使用唯一的接聽 URI 模式探索服務範例</span><span class="sxs-lookup"><span data-stu-id="6b316-102">Discover a Service with Unique Listen Uri Mode Sample</span></span>
<span data-ttu-id="6b316-103">此範例示範如何探索其 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> 屬性設定為 <xref:System.ServiceModel.Description.ListenUriMode.Unique> 的服務。</span><span class="sxs-lookup"><span data-stu-id="6b316-103">This sample demonstrates how to discover a service that has the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span></span> <span data-ttu-id="6b316-104">當 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> 屬性設定為 <xref:System.ServiceModel.Description.ListenUriMode.Unique> 時，透過將連接埠設定成唯一的，或者透過附加 GUID 讓路徑變成唯一的，來確保 ListenUri 是唯一的。</span><span class="sxs-lookup"><span data-stu-id="6b316-104">When the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>, the ListenUri is ensured to be unique by either setting the port to be unique or for the path to be unique by appending a GUID.</span></span>  
  
### <a name="features-on-the-service"></a><span data-ttu-id="6b316-105">服務的功能</span><span class="sxs-lookup"><span data-stu-id="6b316-105">Features on the Service</span></span>  
 <span data-ttu-id="6b316-106"><xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> 屬性會針對 TCP 端點設定為 <xref:System.ServiceModel.Description.ListenUriMode.Unique>。</span><span class="sxs-lookup"><span data-stu-id="6b316-106">The <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique> for the TCP endpoint.</span></span> <span data-ttu-id="6b316-107">接著，服務就可以透過 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 端點搜尋。</span><span class="sxs-lookup"><span data-stu-id="6b316-107">The service is then made discoverable over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span>  
  
### <a name="features-on-the-client"></a><span data-ttu-id="6b316-108">用戶端的功能</span><span class="sxs-lookup"><span data-stu-id="6b316-108">Features on the Client</span></span>  
 <span data-ttu-id="6b316-109">此用戶端會使用正確的 `Via.Uri`，透過 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 方法連接至服務。</span><span class="sxs-lookup"><span data-stu-id="6b316-109">This client connects to the service using the correct `Via.Uri` by using the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method.</span></span> <span data-ttu-id="6b316-110">接著，系統會查詢從方法傳回的 <xref:System.ServiceModel.Discovery.FindResponse> 是否包含有效的 <xref:System.ServiceModel.Endpoint.ListenUri%2A>，以及是否不同於 `Address.Uri`。</span><span class="sxs-lookup"><span data-stu-id="6b316-110">The <xref:System.ServiceModel.Discovery.FindResponse> that is returned from the method is then queried for whether it contains a valid <xref:System.ServiceModel.Endpoint.ListenUri%2A> and whether it is different than `Address.Uri`.</span></span> <span data-ttu-id="6b316-111">然後，系統會將適當的資訊傳遞到 `InvokeCalculatorService` 方法。</span><span class="sxs-lookup"><span data-stu-id="6b316-111">The appropriate information is then passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="6b316-112">在 `InvokeCalculatorService` 方法中，呼叫者會傳入 <xref:System.ServiceModel.Endpoint.ListenUri%2A>，然後將具有正確 `ClientViaBehavior` 的 `Via.Uri` 加入至用戶端的端點中。</span><span class="sxs-lookup"><span data-stu-id="6b316-112">In the `InvokeCalculatorService` method, the <xref:System.ServiceModel.Endpoint.ListenUri%2A> was passed in by the caller, then a `ClientViaBehavior` with the correct `Via.Uri` is added to the client’s endpoint.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="6b316-113">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="6b316-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="6b316-114">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 UniqueListenUriMode.sln。</span><span class="sxs-lookup"><span data-stu-id="6b316-114">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open UniqueListenUriMode.sln.</span></span>  
  
2.  <span data-ttu-id="6b316-115">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="6b316-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6b316-116">執行服務應用程式，這通常在 [方案基底目錄]\service\bin\debug 資料夾下產生。</span><span class="sxs-lookup"><span data-stu-id="6b316-116">Run the service application, which is generated in the [solution base directory]\service\bin\debug folder.</span></span>  
  
4.  <span data-ttu-id="6b316-117">執行用戶端應用程式，這通常在 [方案基底目錄]\Client\bin\debug 資料夾下產生。</span><span class="sxs-lookup"><span data-stu-id="6b316-117">Run the client application, which is generated in the [solution base directory]\Client\bin\debug folder.</span></span>  
  
     <span data-ttu-id="6b316-118">用戶端會尋找執行中的服務，並寫入到服務端點所發行的主控台中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6b316-118">The client locates the running service and writes to the console the metadata published by the service’s endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6b316-119">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6b316-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b316-120">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6b316-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6b316-121">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="6b316-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b316-122">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6b316-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a><span data-ttu-id="6b316-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b316-123">See Also</span></span>
