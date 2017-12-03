---
title: "非同步尋找範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 229e2ff6e630527e3735e3c48f698f582b0b60f8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="asynchronous-find-sample"></a><span data-ttu-id="329ba-102">非同步尋找範例</span><span class="sxs-lookup"><span data-stu-id="329ba-102">Asynchronous Find Sample</span></span>
<span data-ttu-id="329ba-103">此範例示範如何從用戶端應用程式使用非同步尋找作業。</span><span class="sxs-lookup"><span data-stu-id="329ba-103">This sample shows how to use the asynchronous find operation from a client application.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="329ba-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="329ba-104">Sample Details</span></span>  
 <span data-ttu-id="329ba-105">遵循此設計模式的優點在於，用戶端會以非同步方式，收到當做尋找要求結果搜尋之端點的通知。</span><span class="sxs-lookup"><span data-stu-id="329ba-105">The benefit of following this design pattern is that the client is notified asynchronously of the endpoints located as a result of the find request.</span></span> <span data-ttu-id="329ba-106">若要了解其運作方式，請開啟 Client.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="329ba-106">To see how this works, open the Client.cs file.</span></span> <span data-ttu-id="329ba-107">請注意，<xref:System.ServiceModel.Discovery.DiscoveryClient> 物件有兩個連接至其事件處理常式的委派。</span><span class="sxs-lookup"><span data-stu-id="329ba-107">Note the <xref:System.ServiceModel.Discovery.DiscoveryClient> object has two delegates attached to its event handlers.</span></span> <span data-ttu-id="329ba-108">其中一個委派會在引發 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 事件時呼叫，而另一個委派，則會在每次引發 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 事件時呼叫。</span><span class="sxs-lookup"><span data-stu-id="329ba-108">One delegate is called when a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is raised and another is called each time a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> event is raised.</span></span> <span data-ttu-id="329ba-109">此範例示範如何在應用程式中使用此模式。</span><span class="sxs-lookup"><span data-stu-id="329ba-109">The sample shows how you can utilize this pattern in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="329ba-110">這個範例使用 HTTP 端點，若要執行，則必須加入正確的 URL ACL。</span><span class="sxs-lookup"><span data-stu-id="329ba-110">This sample uses HTTP endpoints and to run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="329ba-111">[設定 HTTP 和 HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="329ba-111"> [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="329ba-112">以更高的權限執行下列命令應該就能加入適當的 ACL。</span><span class="sxs-lookup"><span data-stu-id="329ba-112">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="329ba-113">如果命令未正確執行，您可能要將 domain 和 username 替換成下列引數。</span><span class="sxs-lookup"><span data-stu-id="329ba-113">You may want to substitute your domain and username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="329ba-114">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="329ba-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="329ba-115">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 AsyncFind.sln。</span><span class="sxs-lookup"><span data-stu-id="329ba-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the AsyncFind.sln.</span></span>  
  
2.  <span data-ttu-id="329ba-116">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="329ba-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="329ba-117">開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元並巡覽至 \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug 或 \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug 目錄，然後執行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="329ba-117">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug or \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug directory and run Service.exe.</span></span>  
  
4.  <span data-ttu-id="329ba-118">服務啟動後，巡覽至 \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug 或 WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug 目錄，然後執行 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="329ba-118">After the service has started, navigate to the \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug or WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug directory and run Client.exe.</span></span>  
  
5.  <span data-ttu-id="329ba-119">請注意，用戶端可以尋找與呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="329ba-119">Observe the client is able to locate and call the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="329ba-120">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="329ba-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="329ba-121">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="329ba-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="329ba-122">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="329ba-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="329ba-123">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="329ba-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a><span data-ttu-id="329ba-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="329ba-124">See Also</span></span>
