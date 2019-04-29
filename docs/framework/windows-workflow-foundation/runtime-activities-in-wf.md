---
title: WF 中的執行階段活動
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938095"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="07b10-102">WF 中的執行階段活動</span><span class="sxs-lookup"><span data-stu-id="07b10-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="07b10-103">提供幾種系統供應的活動以存取工作流程執行階段的功能，例如持續性和終止。</span><span class="sxs-lookup"><span data-stu-id="07b10-103">provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="07b10-104">活動</span><span class="sxs-lookup"><span data-stu-id="07b10-104">Activity</span></span>|<span data-ttu-id="07b10-105">描述</span><span class="sxs-lookup"><span data-stu-id="07b10-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="07b10-106">明確要求工作流程保存其狀態。</span><span class="sxs-lookup"><span data-stu-id="07b10-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="07b10-107">終止執行中的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="07b10-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="07b10-108">會防止任何子活動保存的容器活動。</span><span class="sxs-lookup"><span data-stu-id="07b10-108">A container activity that prevents child activities from persisting.</span></span>|
