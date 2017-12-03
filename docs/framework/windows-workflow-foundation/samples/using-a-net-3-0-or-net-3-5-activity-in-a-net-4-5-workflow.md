---
title: "在 .NET Framework 4.5 工作流程中使用 .NET Framework 3.0 或 .NET Framework 3.5 活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 227c4e6ee566cd88982456d0045ab59221b26664
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a><span data-ttu-id="14241-102">在 .NET Framework 4.5 工作流程中使用 .NET Framework 3.0 或 .NET Framework 3.5 活動</span><span class="sxs-lookup"><span data-stu-id="14241-102">Using a .NET Framework 3.0 or .NET Framework 3.5 Activity in a .NET Framework 4.5 Workflow</span></span>
<span data-ttu-id="14241-103"><xref:System.Activities.Statements.Interop> 活動可讓您在 [!INCLUDE[wf](../../../../includes/wf-md.md)] 工作流程中執行 .NET Framework 3.0 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 活動。</span><span class="sxs-lookup"><span data-stu-id="14241-103">The <xref:System.Activities.Statements.Interop> activity allows you to run a .NET Framework 3.0 [!INCLUDE[wf](../../../../includes/wf-md.md)] activity within a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="14241-104">這個範例示範如何使用 <xref:System.Activities.Statements.Interop> 活動，將字串當做引數傳遞至自訂 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 活動。</span><span class="sxs-lookup"><span data-stu-id="14241-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Interop> activity to pass a string as an argument to a custom [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] activity.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="14241-105">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="14241-105">To use this sample</span></span>  
  
1.  <span data-ttu-id="14241-106">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 SimpleInterop.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="14241-106">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the SimpleInterop.sln solution file.</span></span>  
  
2.  <span data-ttu-id="14241-107">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="14241-107">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="14241-108">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="14241-108">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14241-109">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="14241-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14241-110">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="14241-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="14241-111">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="14241-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14241-112">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="14241-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a><span data-ttu-id="14241-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14241-113">See Also</span></span>
