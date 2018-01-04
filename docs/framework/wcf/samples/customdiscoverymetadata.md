---
title: CustomDiscoveryMetadata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c2e13fde338075d9ef16c205efcfcb452235f0af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="903ba-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="903ba-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="903ba-103">這個範例示範如何將自訂 XML 中繼資料插入服務公開之可探索端點的探索中繼資料。</span><span class="sxs-lookup"><span data-stu-id="903ba-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="903ba-104">接著在範例中會示範用戶端如何搜尋服務及擷取這項自訂資料。</span><span class="sxs-lookup"><span data-stu-id="903ba-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="903ba-105">這個範例包含二個專案，也就是服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="903ba-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="903ba-106">服務</span><span class="sxs-lookup"><span data-stu-id="903ba-106">Service</span></span>  
 <span data-ttu-id="903ba-107">在 `main` 方法中，範例會示範填入 <xref:System.Xml.Linq.XElement> 型別的物件中必要的欄位，並且將該物件加入至 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>。</span><span class="sxs-lookup"><span data-stu-id="903ba-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="903ba-108">這個 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 會加入至特殊端點。</span><span class="sxs-lookup"><span data-stu-id="903ba-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="903ba-109">探索特殊端點時，探索中繼資料會包含加入此處的自訂資料。</span><span class="sxs-lookup"><span data-stu-id="903ba-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="903ba-110">用戶端</span><span class="sxs-lookup"><span data-stu-id="903ba-110">Client</span></span>  
 <span data-ttu-id="903ba-111">這個範例會示範在 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 上呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient> 方法。</span><span class="sxs-lookup"><span data-stu-id="903ba-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="903ba-112">接著會查詢產生的 <xref:System.ServiceModel.Discovery.FindResponse> 中適當的預期 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="903ba-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="903ba-113">然後會將這些項目列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="903ba-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="903ba-114">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="903ba-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="903ba-115">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中載入專案方案，然後建立專案。</span><span class="sxs-lookup"><span data-stu-id="903ba-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="903ba-116">首先執行 [方案基底目錄]\service\bin\debug 中產生的 Service 應用程式，然後執行 [方案基底目錄]\Client\bin\debug 中產生的 Client 應用程式。</span><span class="sxs-lookup"><span data-stu-id="903ba-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="903ba-117">請注意，服務會連線，用戶端則會尋找服務並且列印端點中發行的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="903ba-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="903ba-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="903ba-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="903ba-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="903ba-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="903ba-120">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="903ba-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="903ba-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="903ba-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="903ba-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="903ba-122">See Also</span></span>
