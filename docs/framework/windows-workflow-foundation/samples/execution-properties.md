---
title: "執行屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fed33544654e6929997567198c0f07346e715d1e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="execution-properties"></a><span data-ttu-id="96cc6-102">執行屬性</span><span class="sxs-lookup"><span data-stu-id="96cc6-102">Execution Properties</span></span>
<span data-ttu-id="96cc6-103">這個範例示範如何使用定義及使用自訂活動中的執行屬性。</span><span class="sxs-lookup"><span data-stu-id="96cc6-103">This sample shows how to define and use an execution property in a custom activity.</span></span> <span data-ttu-id="96cc6-104">在這個範例中，執行屬性決定主控台的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="96cc6-104">In this example, the execution property determines the console's foreground color.</span></span> <span data-ttu-id="96cc6-105">範例工作流程將示範不同的執行邏輯路徑 (<xref:System.Activities.Statements.Parallel> 活動的分支) 如何在活動交錯執行 (跨 <xref:System.Activities.Statements.Parallel> 活動的分支) 的情況下維持不同的主控台色彩。</span><span class="sxs-lookup"><span data-stu-id="96cc6-105">An example workflow shows how different logical paths of execution (branches of a <xref:System.Activities.Statements.Parallel> activity) can maintain different console colors despite interleaved execution of activities (across the branches of the <xref:System.Activities.Statements.Parallel> activity).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="96cc6-106">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="96cc6-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="96cc6-107">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [ExecutionProperties.sln] 範例方案。</span><span class="sxs-lookup"><span data-stu-id="96cc6-107">Open the ExecutionProperties.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="96cc6-108">在建置方案之前檢視 ThreeColors.xaml 會顯示錯誤，因為使用的自訂活動必須與方案同時建置。</span><span class="sxs-lookup"><span data-stu-id="96cc6-108">Viewing ThreeColors.xaml before building the solution displays an error, because the custom activities used must be built at the same time as the solution.</span></span>  
  
2.  <span data-ttu-id="96cc6-109">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="96cc6-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="96cc6-110">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="96cc6-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="96cc6-111">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="96cc6-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="96cc6-112">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="96cc6-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="96cc6-113">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="96cc6-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`