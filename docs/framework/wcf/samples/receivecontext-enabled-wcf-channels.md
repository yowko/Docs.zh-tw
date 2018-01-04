---
title: "已啟用 ReceiveContext 的 WCF 通道"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765efb43efc0ea60ebb71bc8cdb5bd8edf973c2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="99388-102">已啟用 ReceiveContext 的 WCF 通道</span><span class="sxs-lookup"><span data-stu-id="99388-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="99388-103">這個範例示範具備 <xref:System.ServiceModel.Channels.ReceiveContext> 能力之 WCF 通道的用處。</span><span class="sxs-lookup"><span data-stu-id="99388-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="99388-104">這個範例會實作服務，以使用 NetMSMQ 通道尋找兩個數字的乘積。</span><span class="sxs-lookup"><span data-stu-id="99388-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="99388-105"><xref:System.ServiceModel.Channels.ReceiveContext> 類別可讓應用程式決定要存取訊息，或是將訊息留在佇列中做進一步處理 (即使是在已檢查過訊息的內容之後)。</span><span class="sxs-lookup"><span data-stu-id="99388-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="99388-106">在這個範例中，用戶端會將隨機整數傳送至交易式佇列。</span><span class="sxs-lookup"><span data-stu-id="99388-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="99388-107">`ProductCalculator` 服務會接收訊息並檢查訊息內容 (也就是整數)，以判斷是否可以計算乘積。</span><span class="sxs-lookup"><span data-stu-id="99388-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="99388-108">如果服務作業未計算乘積，則訊息會放回佇列中，並且可以由接聽佇列的服務再次接收。</span><span class="sxs-lookup"><span data-stu-id="99388-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99388-109">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="99388-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="99388-110">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="99388-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="99388-111">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="99388-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="99388-112">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="99388-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="99388-113">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="99388-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="99388-114">請確定已安裝 Microsoft Message Queuing (MSMQ)。</span><span class="sxs-lookup"><span data-stu-id="99388-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="99388-115">若要在 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上安裝 MSMQ：</span><span class="sxs-lookup"><span data-stu-id="99388-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="99388-116">在**伺服器管理員**，按一下 **功能**。</span><span class="sxs-lookup"><span data-stu-id="99388-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="99388-117">在底下的右窗格中**功能摘要**，按一下 **新增功能**。</span><span class="sxs-lookup"><span data-stu-id="99388-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="99388-118">在結果視窗中，依序展開**訊息佇列**。</span><span class="sxs-lookup"><span data-stu-id="99388-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="99388-119">展開**訊息佇列服務**。</span><span class="sxs-lookup"><span data-stu-id="99388-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="99388-120">按一下**目錄服務整合**（針對加入網域電腦），然後按一下  **HTTP 支援**。</span><span class="sxs-lookup"><span data-stu-id="99388-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="99388-121">按一下**下一步**，然後按一下 **安裝**。</span><span class="sxs-lookup"><span data-stu-id="99388-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="99388-122">若要在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上安裝 MSMQ：</span><span class="sxs-lookup"><span data-stu-id="99388-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="99388-123">開啟**控制台**。</span><span class="sxs-lookup"><span data-stu-id="99388-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="99388-124">按一下**程式**然後在**程式和功能**，按一下 **開啟或關閉 Windows 功能**。</span><span class="sxs-lookup"><span data-stu-id="99388-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="99388-125">展開**Microsoft Message Queue (MSMQ) 伺服器**，依序展開**Microsoft Message Queue (MSMQ) 伺服器核心**，然後選取要安裝的下列訊息佇列功能的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="99388-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="99388-126">訊息佇列伺服器</span><span class="sxs-lookup"><span data-stu-id="99388-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="99388-127">MSMQ Active Directory 網域服務整合 (針對加入網域的電腦)</span><span class="sxs-lookup"><span data-stu-id="99388-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="99388-128">MSMQ HTTP 支援</span><span class="sxs-lookup"><span data-stu-id="99388-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="99388-129">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="99388-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="99388-130">如果提示您重新啟動電腦時，請按一下**確定**以完成安裝。</span><span class="sxs-lookup"><span data-stu-id="99388-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="99388-131">請確定電腦上已安裝 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="99388-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="99388-132">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 ReceiveContextProductGenerator.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="99388-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="99388-133">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="99388-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="99388-134">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="99388-134">To run the solution, press CTRL+F5.</span></span>
