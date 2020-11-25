---
title: 移轉指引
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: b9b90aedc06fb4a4564596d61aa0ac2dc4c6143f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733590"
---
# <a name="migration-guidance"></a><span data-ttu-id="3b117-102">移轉指引</span><span class="sxs-lookup"><span data-stu-id="3b117-102">Migration Guidance</span></span>

<span data-ttu-id="3b117-103">在 .NET Framework 4 中，Microsoft 會發行 Windows Workflow Foundation (WF) 的第二個主要版本。</span><span class="sxs-lookup"><span data-stu-id="3b117-103">In the .NET Framework 4, Microsoft is releasing the second major version of Windows Workflow Foundation (WF).</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="3b117-104">已在 WinFX 中發行 (這包含了系統中的類型。 \* 命名現在稱為 WF3) ，並在 .NET Framework 3.5 中增強。</span><span class="sxs-lookup"><span data-stu-id="3b117-104">was released in WinFX (this included the types in the System.Workflow.\* namespaces; now referred to as WF3) and enhanced in .NET Framework 3.5.</span></span> <span data-ttu-id="3b117-105">WF3 也是 .NET Framework 4 的一部分，但是存在於新的工作流程技術 (系統中的類型。 \* 命名稱為 WF4) 。</span><span class="sxs-lookup"><span data-stu-id="3b117-105">WF3 is also part of the .NET Framework 4, but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="3b117-106">在考量何時採用 WF4 時，重要的是要先了解到：您必須控制時機。</span><span class="sxs-lookup"><span data-stu-id="3b117-106">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>

- <span data-ttu-id="3b117-107">WF3 是 .NET Framework 4 的完整支援部分。</span><span class="sxs-lookup"><span data-stu-id="3b117-107">WF3 is a fully supported part of the .NET Framework 4.</span></span>

- <span data-ttu-id="3b117-108">WF3 應用程式不需修改即可在 .NET Framework 4 上執行，而且會繼續受到完整支援。</span><span class="sxs-lookup"><span data-stu-id="3b117-108">WF3 applications run on the .NET Framework 4 without modification and continue to be fully supported.</span></span>

- <span data-ttu-id="3b117-109">您可以建立新的 WF3 應用程式，而且您可以在 Visual Studio 2012 中編輯現有的應用程式，並受到完整支援。</span><span class="sxs-lookup"><span data-stu-id="3b117-109">New WF3 applications can be created and your existing applications can be edited in Visual Studio 2012 and are fully supported.</span></span>

 <span data-ttu-id="3b117-110">因此，採用 .NET Framework 4 的決策會與您的決策分離，以移至 WF4 (系統。 \*) 從 WF3 (System.object。 \*) 。</span><span class="sxs-lookup"><span data-stu-id="3b117-110">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.\*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="3b117-111">這個主題會提供 WF 移轉指引的連結，此連結中提供使用 WF3 與 WF4 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3b117-111">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>

## <a name="wf-migration-white-papers-and-cookbooks"></a><span data-ttu-id="3b117-112">WF 遷移白皮書和操作手冊</span><span class="sxs-lookup"><span data-stu-id="3b117-112">WF migration white papers and cookbooks</span></span>

 <span data-ttu-id="3b117-113">[WF 遷移總覽](/previous-versions/appfabric/ff383417(v=azure.10))主題提供 WF3 與 WF4 與遷移策略之間關聯性的廣泛總覽。</span><span class="sxs-lookup"><span data-stu-id="3b117-113">The [WF Migration Overview](/previous-versions/appfabric/ff383417(v=azure.10)) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="3b117-114">附隨的主題會深入查看特定主題。</span><span class="sxs-lookup"><span data-stu-id="3b117-114">Companion topics drill into specific topics.</span></span>

 <span data-ttu-id="3b117-115">[WF 遷移總覽](/previous-versions/appfabric/ff383417(v=azure.10)) 描述 WF3 和 WF4 之間的關聯性，以及您在 .NET Framework 4 中作為使用者或工作流程技術潛在使用者的選擇。</span><span class="sxs-lookup"><span data-stu-id="3b117-115">[WF Migration Overview](/previous-versions/appfabric/ff383417(v=azure.10)) Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET Framework 4.</span></span>

 <span data-ttu-id="3b117-116">[WF 遷移： WF3 開發的最佳作法](/previous-versions/appfabric/ff383417(v=azure.10)) 討論如何設計 WF3 構件，以便更輕鬆地將它們遷移至 WF4。</span><span class="sxs-lookup"><span data-stu-id="3b117-116">[WF Migration: Best Practices for WF3 Development](/previous-versions/appfabric/ff383417(v=azure.10)) Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>

 <span data-ttu-id="3b117-117">[WF 指引：規則](/previous-versions/appfabric/ff383417(v=azure.10)) 討論如何將規則相關投資帶到 .NET Framework 4 解決方案中。</span><span class="sxs-lookup"><span data-stu-id="3b117-117">[WF Guidance: Rules](/previous-versions/appfabric/ff383417(v=azure.10)) Discusses how to bring rules-related investments forward into .NET Framework 4 solutions.</span></span>

 <span data-ttu-id="3b117-118">[WF 指引：狀態機器](/previous-versions/appfabric/ff383417(v=azure.10)) 討論 WF4 的控制流程模型（如果沒有 State-Machine 活動）。</span><span class="sxs-lookup"><span data-stu-id="3b117-118">[WF Guidance: State Machine](/previous-versions/appfabric/ff383417(v=azure.10)) Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>

 <span data-ttu-id="3b117-119">請注意，此指引只適用於以 .NET Framework 4 為目標的工作流程專案。</span><span class="sxs-lookup"><span data-stu-id="3b117-119">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="3b117-120">狀態機器工作流程已新增至 4.0.1 Platform Update 1 版本的 .NET Framework，並包含在 .NET Framework 4.5 中。</span><span class="sxs-lookup"><span data-stu-id="3b117-120">State Machine workflows were added in .NET Framework 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> <span data-ttu-id="3b117-121">如需有關 .NET Framework 4.0.1-4.0.3 和 .NET Framework 4.5 中狀態機器工作流程的詳細資訊，請參閱 [Microsoft .NET Framework 4 功能](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) 和 [狀態機器工作流程](state-machine-workflows.md)的更新4.0.1。</span><span class="sxs-lookup"><span data-stu-id="3b117-121">For more information about state machine workflows in .NET Framework 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) and [State Machine Workflows](state-machine-workflows.md).</span></span>

 <span data-ttu-id="3b117-122">[WF 遷移手冊：自訂活動](/previous-versions/appfabric/ff383417(v=azure.10)) 提供在 WF4 上重新設計 WF3 自訂活動的範例和指示。</span><span class="sxs-lookup"><span data-stu-id="3b117-122">[WF Migration Cookbook: Custom Activities](/previous-versions/appfabric/ff383417(v=azure.10)) Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>

 <span data-ttu-id="3b117-123">[WF 遷移操作手冊： Advanced Custom 活動](/previous-versions/appfabric/ff383417(v=azure.10)) 提供重新設計 WF3 自訂活動的指導方針，這些活動會使用 WF3 佇列，並將子活動排程為 WF4 的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="3b117-123">[WF Migration Cookbook: Advanced Custom Activities](/previous-versions/appfabric/ff383417(v=azure.10)) Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>

 <span data-ttu-id="3b117-124">[WF 遷移操作手冊：工作流程](/previous-versions/appfabric/ff383417(v=azure.10)) 提供在 WF4 上重新設計 WF3 工作流程的範例和指示。</span><span class="sxs-lookup"><span data-stu-id="3b117-124">[WF Migration Cookbook: Workflows](/previous-versions/appfabric/ff383417(v=azure.10)) Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>

 <span data-ttu-id="3b117-125">[WF 遷移操作手冊：工作流程裝載](/previous-versions/appfabric/ff383417(v=azure.10)) 提供將 WF3 裝載程式碼重新設計為 WF4 裝載程式碼的指引。</span><span class="sxs-lookup"><span data-stu-id="3b117-125">[WF Migration Cookbook: Workflow Hosting](/previous-versions/appfabric/ff383417(v=azure.10)) Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="3b117-126">目標是要彌補在工作流程中裝載 WF3 和 WF4 之間的主要差異。</span><span class="sxs-lookup"><span data-stu-id="3b117-126">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>

 <span data-ttu-id="3b117-127">[WF 遷移操作手冊：工作流程追蹤](/previous-versions/appfabric/ff383417(v=azure.10)) 提供使用對等 WF4 追蹤程式碼和設定來重新設計 WF3 追蹤程式碼和設定的指導方針。</span><span class="sxs-lookup"><span data-stu-id="3b117-127">[WF Migration Cookbook: Workflow Tracking](/previous-versions/appfabric/ff383417(v=azure.10)) Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>

 <span data-ttu-id="3b117-128">[WF 指引：工作流程服務](/previous-versions/appfabric/ff383417(v=azure.10)) 提供以範例為導向的逐步指示，可讓您重新設計 Windows Communication Foundation (WCF) web 服務的工作流程， (通常稱為工作流程服務) 在 WF3 中建立以使用 WF4，適用于現成活動的常見案例。</span><span class="sxs-lookup"><span data-stu-id="3b117-128">[WF Guidance: Workflow Services](/previous-versions/appfabric/ff383417(v=azure.10)) Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b117-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b117-129">See also</span></span>

- <xref:System.Activities.Statements.Interop>
