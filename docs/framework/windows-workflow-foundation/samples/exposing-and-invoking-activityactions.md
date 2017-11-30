---
title: "公開及叫用 ActivityActions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 45920f913a1d7252858fd0e563da944c10fae75c
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="881e5-102">公開及叫用 ActivityActions</span><span class="sxs-lookup"><span data-stu-id="881e5-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="881e5-103">這個範例示範如何開發有 <xref:System.Activities.ActivityAction> 的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="881e5-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="881e5-104">此外，也示範如何提供 <xref:System.Activities.ActivityAction> 實作，使用此活動。</span><span class="sxs-lookup"><span data-stu-id="881e5-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="881e5-105"><xref:System.Activities.ActivityAction>允許活動作者公開 「 洞 」 特定的簽章與位置，活動使用者也可以插入自訂行為。</span><span class="sxs-lookup"><span data-stu-id="881e5-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="881e5-106">例如， <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach`活動，（項目集合），有<xref:System.Activities.ActivityAction>，可讓活動使用者插入目前的反覆項目項目運作的行為。</span><span class="sxs-lookup"><span data-stu-id="881e5-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="881e5-107">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="881e5-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="881e5-108">開啟**ActivityAction.sln**範例方案中的[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="881e5-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="881e5-109">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="881e5-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="881e5-110">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="881e5-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="881e5-111">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="881e5-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="881e5-112">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="881e5-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="881e5-113">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="881e5-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`