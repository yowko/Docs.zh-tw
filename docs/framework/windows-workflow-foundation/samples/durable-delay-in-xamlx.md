---
title: XAMLX 中的永久性延遲
ms.date: 03/30/2017
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
ms.openlocfilehash: 1eef9211c67d190ecb5f329c481fa2e3d1763353
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708677"
---
# <a name="durable-delay-in-xamlx"></a><span data-ttu-id="fc258-102">XAMLX 中的永久性延遲</span><span class="sxs-lookup"><span data-stu-id="fc258-102">Durable Delay in XAMLX</span></span>
<span data-ttu-id="fc258-103">這個範例示範如何使用永久性延遲，此延遲會在延遲期間將工作流程保存至永久性裝置。</span><span class="sxs-lookup"><span data-stu-id="fc258-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc258-104">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="fc258-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fc258-105">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="fc258-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fc258-106">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="fc258-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc258-107">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="fc258-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a><span data-ttu-id="fc258-108">討論</span><span class="sxs-lookup"><span data-stu-id="fc258-108">Discussion</span></span>  
 <span data-ttu-id="fc258-109">此範例工作流程包含兩個本機檔案訊息，兩者之間會以延遲區隔。</span><span class="sxs-lookup"><span data-stu-id="fc258-109">The sample workflow contains two messages to a local file that are separated by a delay.</span></span> <span data-ttu-id="fc258-110">當延遲觸發時，工作流程便會卸載，並且在工作流程執行個體存放區中等待 5 秒鐘，再重新載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="fc258-110">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
 <span data-ttu-id="fc258-111">.Xamlx 檔案是裝載於 Visual Studio 中的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="fc258-111">The .xamlx file is a workflow service that is hosted in Visual Studio.</span></span> <span data-ttu-id="fc258-112">Visual Studio 會使用 Cassini，使用工作流程服務主機來裝載工作流程。</span><span class="sxs-lookup"><span data-stu-id="fc258-112">Visual Studio uses Cassini that uses a workflow service host to host the workflow.</span></span>  
  
 <span data-ttu-id="fc258-113">除了裝載工作流程以外，工作流程服務主機也會透過載入和卸載的方式來管理工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc258-113">In addition to hosting the workflow, the workflow service host manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="fc258-114">若要啟動的 Windows Workflow Foundation (WF) 上的定義 （工作流程服務主機上） 執行個體，設定 傳送訊息給用戶端<xref:System.ServiceModel.Activities.Receive>工作流程中的活動。</span><span class="sxs-lookup"><span data-stu-id="fc258-114">To start an instance of the Windows Workflow Foundation (WF) definition (on the workflow service host), set a client that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="fc258-115">這個 <xref:System.ServiceModel.Activities.Receive> 會將它的 <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> 屬性設定為 `true`，以便在收到訊息時，建立新的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc258-115">This <xref:System.ServiceModel.Activities.Receive> has its <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="fc258-116">在初始化期間，卸載執行個體的行為會加入至組態檔中，這個組態檔會指定工作流程服務主機應將執行個體卸載至持續性存放區 (資料庫) 的情況。</span><span class="sxs-lookup"><span data-stu-id="fc258-116">During initialization, an unload instance behavior is added to the configuration file that specifies to the workflow service host under which it should unload an instance to the persistence store (database).</span></span> <span data-ttu-id="fc258-117">在這個範例中，它會在工作流程閒置後 (觸發延遲時) 立即卸載執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc258-117">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="fc258-118">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="fc258-118">To use this sample</span></span>  
  
1.  <span data-ttu-id="fc258-119">開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="fc258-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="fc258-120">巡覽至 DurableDelayXamlx\CS 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fc258-120">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="fc258-121">執行 Setup.cmd。</span><span class="sxs-lookup"><span data-stu-id="fc258-121">Run Setup.cmd.</span></span>  
  
4.  <span data-ttu-id="fc258-122">以系統管理員身分執行 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fc258-122">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an administrator.</span></span>  
  
5.  <span data-ttu-id="fc258-123">開啟 DurableDelayXamlx.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="fc258-123">Open the DurableDelayXamlx.sln solution file.</span></span>  
  
6.  <span data-ttu-id="fc258-124">在 **方案總管**，以滑鼠右鍵按一下方案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="fc258-124">In **Solution Explorer**, right-click the solution and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="fc258-125">選取 **多個啟始專案**並將這兩個專案設定為**開始**。</span><span class="sxs-lookup"><span data-stu-id="fc258-125">Select **Multiple startup projects** and set both projects to **Start**.</span></span>  
  
8.  <span data-ttu-id="fc258-126">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="fc258-126">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
9. <span data-ttu-id="fc258-127">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="fc258-127">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="fc258-128">若要解除安裝這個範例</span><span class="sxs-lookup"><span data-stu-id="fc258-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="fc258-129">開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="fc258-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="fc258-130">巡覽至 DurableDelayXamlx\CS 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fc258-130">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="fc258-131">執行 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="fc258-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc258-132">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="fc258-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fc258-133">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="fc258-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fc258-134">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="fc258-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc258-135">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="fc258-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
