---
title: 公開及叫用 ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 99207c33d82ec9028da2355cc792c366dc5e0cc6
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46479750"
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="bc93d-102">公開及叫用 ActivityActions</span><span class="sxs-lookup"><span data-stu-id="bc93d-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="bc93d-103">這個範例示範如何開發有 <xref:System.Activities.ActivityAction> 的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="bc93d-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="bc93d-104">此外，也示範如何提供 <xref:System.Activities.ActivityAction> 實作，使用此活動。</span><span class="sxs-lookup"><span data-stu-id="bc93d-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="bc93d-105"><xref:System.Activities.ActivityAction>可讓活動作者公開 「 洞孔 」 裡使用特定的簽章，活動使用者可以在這裡插入自訂行為。</span><span class="sxs-lookup"><span data-stu-id="bc93d-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="bc93d-106">例如，<xref:System.Activities.Statements.ForEach%601> 活動 (在項目集合上操作) 有 <xref:System.Activities.ActivityAction>，可讓活動使用者插入可在目前反覆運算項目上操作的行為。</span><span class="sxs-lookup"><span data-stu-id="bc93d-106">For example, the <xref:System.Activities.Statements.ForEach%601> activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bc93d-107">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="bc93d-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bc93d-108">開啟**ActivityAction.sln**範例方案中的[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bc93d-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="bc93d-109">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="bc93d-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc93d-110">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="bc93d-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bc93d-111">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="bc93d-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bc93d-112">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="bc93d-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bc93d-113">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="bc93d-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`