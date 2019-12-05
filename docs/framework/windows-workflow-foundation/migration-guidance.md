---
title: 移轉指導方針
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 672ed1a93b4409f491d76ffeeaaac5f67a1c4b6e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802605"
---
# <a name="migration-guidance"></a><span data-ttu-id="969b4-102">移轉指導方針</span><span class="sxs-lookup"><span data-stu-id="969b4-102">Migration Guidance</span></span>

<span data-ttu-id="969b4-103">在 .NET Framework 4 中，Microsoft 會發行 Windows Workflow Foundation （WF）的第二個主要版本。</span><span class="sxs-lookup"><span data-stu-id="969b4-103">In the .NET Framework 4, Microsoft is releasing the second major version of Windows Workflow Foundation (WF).</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="969b4-104">已在 WinFX 中發行（這包括\* 命名空間中的類型，現在稱為 WF3），並在 .NET Framework 3.5 中增強。</span><span class="sxs-lookup"><span data-stu-id="969b4-104">was released in WinFX (this included the types in the System.Workflow.\* namespaces; now referred to as WF3) and enhanced in .NET Framework 3.5.</span></span> <span data-ttu-id="969b4-105">WF3 也是 .NET Framework 4 的一部分，但是存在於新的工作流程技術（WF4 命名空間\* 中的類型，稱為）。</span><span class="sxs-lookup"><span data-stu-id="969b4-105">WF3 is also part of the .NET Framework 4, but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="969b4-106">在考量何時採用 WF4 時，重要的是要先了解到：您必須控制時機。</span><span class="sxs-lookup"><span data-stu-id="969b4-106">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>  
  
- <span data-ttu-id="969b4-107">WF3 是 .NET Framework 4 中受到完整支援的部分。</span><span class="sxs-lookup"><span data-stu-id="969b4-107">WF3 is a fully supported part of the .NET Framework 4.</span></span>  
  
- <span data-ttu-id="969b4-108">WF3 應用程式會在 .NET Framework 4 上執行，而不需修改，並繼續受到完整支援。</span><span class="sxs-lookup"><span data-stu-id="969b4-108">WF3 applications run on the .NET Framework 4 without modification and continue to be fully supported.</span></span>  
  
- <span data-ttu-id="969b4-109">您可以建立新的 WF3 應用程式，而且您現有的應用程式可以在 Visual Studio 2012 中編輯，而且完全受到支援。</span><span class="sxs-lookup"><span data-stu-id="969b4-109">New WF3 applications can be created and your existing applications can be edited in Visual Studio 2012 and are fully supported.</span></span>  
  
 <span data-ttu-id="969b4-110">因此，採用 .NET Framework 4 的決策會與您的決策分離，以從 WF3 （\*System.object）移至 WF4 （\*）。</span><span class="sxs-lookup"><span data-stu-id="969b4-110">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.\*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="969b4-111">這個主題會提供 WF 移轉指引的連結，此連結中提供使用 WF3 與 WF4 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="969b4-111">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a><span data-ttu-id="969b4-112">WF 移轉白皮書與做法指南</span><span class="sxs-lookup"><span data-stu-id="969b4-112">WF Migration Whitepapers and Cookbooks</span></span>  
 <span data-ttu-id="969b4-113">[WF 遷移總覽](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))主題提供 WF3 與 WF4 之間的關聯性，以及遷移策略的大致總覽。</span><span class="sxs-lookup"><span data-stu-id="969b4-113">The [WF Migration Overview](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10)) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="969b4-114">附隨的主題會深入查看特定主題。</span><span class="sxs-lookup"><span data-stu-id="969b4-114">Companion topics drill into specific topics.</span></span>  
  
 <span data-ttu-id="969b4-115">[WF 遷移總覽](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-115">[WF Migration Overview](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-116">描述 WF3 與 WF4 之間的關係，以及您身為 .NET 4 工作流程技術之使用者或潛在使用者可做的選擇。</span><span class="sxs-lookup"><span data-stu-id="969b4-116">Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET 4.</span></span>  
  
 <span data-ttu-id="969b4-117">[WF 遷移： WF3 開發的最佳做法](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-117">[WF Migration: Best Practices for WF3 Development](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-118">討論如何設計 WF3 成品，以便更簡易地移轉為 WF4。</span><span class="sxs-lookup"><span data-stu-id="969b4-118">Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>  
  
 <span data-ttu-id="969b4-119">[WF 指引：規則](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-119">[WF Guidance: Rules](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-120">討論如何將規則相關投資帶往 .NET Framework 4 個解決方案。</span><span class="sxs-lookup"><span data-stu-id="969b4-120">Discusses how to bring rules-related investments forward into .NET Framework 4 solutions.</span></span>  
  
 <span data-ttu-id="969b4-121">[WF 指引：狀態機器](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-121">[WF Guidance: State Machine](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-122">討論在缺乏狀態機器活動的情況下如何建立 WF4 控制流程的模型。</span><span class="sxs-lookup"><span data-stu-id="969b4-122">Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>  
  
 <span data-ttu-id="969b4-123">請注意，此指引只適用於以 .NET Framework 4 為目標的工作流程專案。</span><span class="sxs-lookup"><span data-stu-id="969b4-123">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="969b4-124">狀態機器工作流程已加入在含有 Platform Update 1 版本的 .NET 4.0.1 中，並且包含在 .NET Framework 4.5 中。</span><span class="sxs-lookup"><span data-stu-id="969b4-124">State Machine workflows were added in .NET 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> <span data-ttu-id="969b4-125">如需 .NET 4.0.1-4.0.3 和 .NET Framework 4.5 中狀態機器工作流程的詳細資訊，請參閱[Update 4.0.1 For Microsoft .NET Framework 4 功能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100))和[狀態機器工作流程](state-machine-workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="969b4-125">For more information about state machine workflows in .NET 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) and [State Machine Workflows](state-machine-workflows.md).</span></span>  
  
 <span data-ttu-id="969b4-126">[WF 遷移操作手冊：自訂活動](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-126">[WF Migration Cookbook: Custom Activities](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-127">提供在 WF4 上重新設計 WF3 自訂活動的範例與指引。</span><span class="sxs-lookup"><span data-stu-id="969b4-127">Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>  
  
 <span data-ttu-id="969b4-128">[WF 遷移操作手冊：先進的自訂活動](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-128">[WF Migration Cookbook: Advanced Custom Activities](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-129">提供重新設計進階 WF3 自訂活動的指引，這些活動會使用 WF3 佇列，並排定子活動做為 WF4 自訂活動。</span><span class="sxs-lookup"><span data-stu-id="969b4-129">Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>  
  
 <span data-ttu-id="969b4-130">[WF 遷移操作手冊：工作流程](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-130">[WF Migration Cookbook: Workflows](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-131">提供在 WF4 上重新設計 WF3 的範例與指引。</span><span class="sxs-lookup"><span data-stu-id="969b4-131">Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>  
  
 <span data-ttu-id="969b4-132">[WF 遷移操作手冊：工作流程裝載](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-132">[WF Migration Cookbook: Workflow Hosting](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-133">提供將 WF3 裝載程式碼重新設計成 WF4 裝載程式碼的指引。</span><span class="sxs-lookup"><span data-stu-id="969b4-133">Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="969b4-134">目標是要彌補在工作流程中裝載 WF3 和 WF4 之間的主要差異。</span><span class="sxs-lookup"><span data-stu-id="969b4-134">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>  
  
 <span data-ttu-id="969b4-135">[WF 遷移操作手冊：工作流程追蹤](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-135">[WF Migration Cookbook: Workflow Tracking](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-136">提供使用對等 WF4 追蹤程式碼和組態，重新設計 WF3 追蹤程式碼和組態的指引。</span><span class="sxs-lookup"><span data-stu-id="969b4-136">Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>  
  
 <span data-ttu-id="969b4-137">[WF 指引：工作流程服務](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="969b4-137">[WF Guidance: Workflow Services](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="969b4-138">提供範例導向的逐步指示，示範如何針對全新活動的一般狀況，將實作 WF3 中建立之 Windows Communication Foundation (WCF) Web 服務 (通常稱為工作流程服務) 的工作流程，重新設計成使用 WF4。</span><span class="sxs-lookup"><span data-stu-id="969b4-138">Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969b4-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="969b4-139">See also</span></span>

- <xref:System.Activities.Statements.Interop>
