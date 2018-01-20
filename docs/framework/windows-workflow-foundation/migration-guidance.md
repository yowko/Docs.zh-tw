---
title: "移轉指引"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e04c63754960dca44558d888b8ce357220562ea7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="migration-guidance"></a><span data-ttu-id="1b22f-102">移轉指引</span><span class="sxs-lookup"><span data-stu-id="1b22f-102">Migration Guidance</span></span>
<span data-ttu-id="1b22f-103">在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中，Microsoft 發佈了 [!INCLUDE[wf](../../../includes/wf-md.md)] 的第二個主要版本。</span><span class="sxs-lookup"><span data-stu-id="1b22f-103">In the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Microsoft is releasing the second major version of [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="1b22f-104"> 是在 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 中發佈 (其中包含 System.Workflow.\* 命名空間中的型別；現在則是指 WF3)，並在 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 中增強。</span><span class="sxs-lookup"><span data-stu-id="1b22f-104"> was released in [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (this included the types in the System.Workflow.\* namespaces; now referred to as WF3) and enhanced in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="1b22f-105">WF3 也是屬於[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]，但有與新的工作流程技術 (System.Activities。 類型\*命名空間; 指 WF4)。</span><span class="sxs-lookup"><span data-stu-id="1b22f-105">WF3 is also part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="1b22f-106">在考量何時採用 WF4 時，重要的是要先了解到：您必須控制時機。</span><span class="sxs-lookup"><span data-stu-id="1b22f-106">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>  
  
-   <span data-ttu-id="1b22f-107">WF3 是 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中受到完整支援的一部分。</span><span class="sxs-lookup"><span data-stu-id="1b22f-107">WF3 is a fully supported part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="1b22f-108">WF3 應用程式在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 上執行而不必修改，並繼續受到完整支援。</span><span class="sxs-lookup"><span data-stu-id="1b22f-108">WF3 applications run on the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] without modification and continue to be fully supported.</span></span>  
  
-   <span data-ttu-id="1b22f-109">可建立新的 WF3 應用程式，且可在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中編輯您現有的應用程式，這些應用程式也受到完整支援。</span><span class="sxs-lookup"><span data-stu-id="1b22f-109">New WF3 applications can be created and your existing applications can be edited in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and are fully supported.</span></span>  
  
 <span data-ttu-id="1b22f-110">因此，採用.NET Framework 4 的決定就分開移至 WF4 （system.activities.*） 從 WF3 (System.Workflow。\*)。</span><span class="sxs-lookup"><span data-stu-id="1b22f-110">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="1b22f-111">這個主題會提供 WF 移轉指引的連結，此連結中提供使用 WF3 與 WF4 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1b22f-111">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a><span data-ttu-id="1b22f-112">WF 移轉白皮書與做法指南</span><span class="sxs-lookup"><span data-stu-id="1b22f-112">WF Migration Whitepapers and Cookbooks</span></span>  
 <span data-ttu-id="1b22f-113">[WF 移轉概觀](http://go.microsoft.com/fwlink/?LinkId=153873)主題提供 WF3 和 WF4 以及移轉策略之間的關聯性的概觀。</span><span class="sxs-lookup"><span data-stu-id="1b22f-113">The [WF Migration Overview](http://go.microsoft.com/fwlink/?LinkId=153873) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="1b22f-114">附隨的主題會深入查看特定主題。</span><span class="sxs-lookup"><span data-stu-id="1b22f-114">Companion topics drill into specific topics.</span></span>  
  
 [<span data-ttu-id="1b22f-115">WF 移轉概觀</span><span class="sxs-lookup"><span data-stu-id="1b22f-115">WF Migration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=153873)  
 <span data-ttu-id="1b22f-116">描述 WF3 與 WF4 之間的關係，以及您身為 .NET 4 工作流程技術之使用者或潛在使用者可做的選擇。</span><span class="sxs-lookup"><span data-stu-id="1b22f-116">Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET 4.</span></span>  
  
 [<span data-ttu-id="1b22f-117">WF 移轉： WF3 開發的最佳作法</span><span class="sxs-lookup"><span data-stu-id="1b22f-117">WF Migration: Best Practices for WF3 Development</span></span>](http://go.microsoft.com/fwlink/?LinkId=153852)  
 <span data-ttu-id="1b22f-118">討論如何設計 WF3 成品，以便更簡易地移轉為 WF4。</span><span class="sxs-lookup"><span data-stu-id="1b22f-118">Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>  
  
 [<span data-ttu-id="1b22f-119">WF 指引： 規則</span><span class="sxs-lookup"><span data-stu-id="1b22f-119">WF Guidance: Rules</span></span>](http://go.microsoft.com/fwlink/?LinkId=153854)  
 <span data-ttu-id="1b22f-120">討論如何進一步對 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 方案進行與規則相關的投資。</span><span class="sxs-lookup"><span data-stu-id="1b22f-120">Discusses how to bring rules-related investments forward into [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] solutions.</span></span>  
  
 [<span data-ttu-id="1b22f-121">WF 指引： 狀態機器</span><span class="sxs-lookup"><span data-stu-id="1b22f-121">WF Guidance: State Machine</span></span>](http://go.microsoft.com/fwlink/?LinkId=153855)  
 <span data-ttu-id="1b22f-122">討論在缺乏狀態機器活動的情況下如何建立 WF4 控制流程的模型。</span><span class="sxs-lookup"><span data-stu-id="1b22f-122">Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>  
  
 <span data-ttu-id="1b22f-123">請注意，此指引只適用於以 .NET Framework 4 為目標的工作流程專案。</span><span class="sxs-lookup"><span data-stu-id="1b22f-123">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="1b22f-124">狀態機器工作流程已加入在含有 Platform Update 1 版本的 .NET 4.0.1 中，並且包含在 .NET Framework 4.5 中。</span><span class="sxs-lookup"><span data-stu-id="1b22f-124">State Machine workflows were added in .NET 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="1b22f-125">狀態機器工作流程中.NET 4.0.1-4.0.3 和.NET Framework 4.5，請參閱[Update 4.0.1 for Microsoft.NET Framework 4 功能](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc)和[狀態機器工作流程](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="1b22f-125"> state machine workflows in .NET 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) and [State Machine Workflows](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).</span></span>  
  
 [<span data-ttu-id="1b22f-126">WF 移轉： 自訂活動</span><span class="sxs-lookup"><span data-stu-id="1b22f-126">WF Migration Cookbook: Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=153856)  
 <span data-ttu-id="1b22f-127">提供在 WF4 上重新設計 WF3 自訂活動的範例與指引。</span><span class="sxs-lookup"><span data-stu-id="1b22f-127">Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>  
  
 [<span data-ttu-id="1b22f-128">WF 移轉： 進階自訂活動</span><span class="sxs-lookup"><span data-stu-id="1b22f-128">WF Migration Cookbook: Advanced Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=275560)  
 <span data-ttu-id="1b22f-129">提供重新設計進階 WF3 自訂活動的指引，這些活動會使用 WF3 佇列，並排定子活動做為 WF4 自訂活動。</span><span class="sxs-lookup"><span data-stu-id="1b22f-129">Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>  
  
 [<span data-ttu-id="1b22f-130">WF 移轉操作手冊： 工作流程</span><span class="sxs-lookup"><span data-stu-id="1b22f-130">WF Migration Cookbook: Workflows</span></span>](http://go.microsoft.com/fwlink/?LinkId=153858)  
 <span data-ttu-id="1b22f-131">提供在 WF4 上重新設計 WF3 的範例與指引。</span><span class="sxs-lookup"><span data-stu-id="1b22f-131">Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>  
  
 [<span data-ttu-id="1b22f-132">WF 移轉： 工作流程裝載</span><span class="sxs-lookup"><span data-stu-id="1b22f-132">WF Migration Cookbook: Workflow Hosting</span></span>](http://go.microsoft.com/fwlink/?LinkId=275561)  
 <span data-ttu-id="1b22f-133">提供將 WF3 裝載程式碼重新設計成 WF4 裝載程式碼的指引。</span><span class="sxs-lookup"><span data-stu-id="1b22f-133">Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="1b22f-134">目標是要彌補在工作流程中裝載 WF3 和 WF4 之間的主要差異。</span><span class="sxs-lookup"><span data-stu-id="1b22f-134">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>  
  
 [<span data-ttu-id="1b22f-135">WF 移轉： 工作流程追蹤</span><span class="sxs-lookup"><span data-stu-id="1b22f-135">WF Migration Cookbook: Workflow Tracking</span></span>](http://go.microsoft.com/fwlink/?LinkId=275562)  
 <span data-ttu-id="1b22f-136">提供使用對等 WF4 追蹤程式碼和組態，重新設計 WF3 追蹤程式碼和組態的指引。</span><span class="sxs-lookup"><span data-stu-id="1b22f-136">Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>  
  
 [<span data-ttu-id="1b22f-137">WF 指引： 工作流程服務</span><span class="sxs-lookup"><span data-stu-id="1b22f-137">WF Guidance: Workflow Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=275564)  
 <span data-ttu-id="1b22f-138">提供範例導向的逐步指示，示範如何針對全新活動的一般狀況，將實作 WF3 中建立之 Windows Communication Foundation (WCF) Web 服務 (通常稱為工作流程服務) 的工作流程，重新設計成使用 WF4。</span><span class="sxs-lookup"><span data-stu-id="1b22f-138">Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b22f-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b22f-139">See Also</span></span>  
 <xref:System.Activities.Statements.Interop>
