---
title: 在 WF 中移轉活動
ms.date: 03/30/2017
ms.assetid: 4ad46db7-5744-410e-8fac-6c3b325b1dd0
ms.openlocfilehash: 38d57223f8703a0ca971cf1d532f82b2e131056a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275020"
---
# <a name="migration-activity-in-wf"></a><span data-ttu-id="a5b01-102">在 WF 中移轉活動</span><span class="sxs-lookup"><span data-stu-id="a5b01-102">Migration Activity in WF</span></span>

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a5b01-103">提供 <xref:System.Activities.Statements.Interop> 用來執行活動的活動，這些活動是根據的工作流程內的活動所衍生 <xref:System.Activities.Activity> 。</span><span class="sxs-lookup"><span data-stu-id="a5b01-103">provides the <xref:System.Activities.Statements.Interop> activity for executing activities that derive from Activity within a workflow that is based on <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="a5b01-104">如需詳細資訊，請參閱 [遷移指引](migration-guidance.md) 一節。</span><span class="sxs-lookup"><span data-stu-id="a5b01-104">For more information, see the [Migration Guidance](migration-guidance.md) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5b01-105"><xref:System.Activities.Statements.Interop>除非工作流程的專案將 **目標 Framework** 設定設為 **.net Framework 4** 或更高版本，否則活動不會出現在工作流程設計工具工具箱中。</span><span class="sxs-lookup"><span data-stu-id="a5b01-105">The <xref:System.Activities.Statements.Interop> activity does not appear in the workflow designer toolbox unless the workflow's project has its **Target Framework** setting set to **.Net Framework 4** or higher.</span></span>
