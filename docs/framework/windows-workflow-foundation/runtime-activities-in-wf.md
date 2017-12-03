---
title: "WF 中的執行階段活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 022f12448d697ba179fb3705f18962e6b0c44239
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="6f83d-102">WF 中的執行階段活動</span><span class="sxs-lookup"><span data-stu-id="6f83d-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="6f83d-103"> 提供幾種系統供應的活動以存取工作流程執行階段的功能，例如持續性和終止。</span><span class="sxs-lookup"><span data-stu-id="6f83d-103"> provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="6f83d-104">活動</span><span class="sxs-lookup"><span data-stu-id="6f83d-104">Activity</span></span>|<span data-ttu-id="6f83d-105">描述</span><span class="sxs-lookup"><span data-stu-id="6f83d-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="6f83d-106">明確要求工作流程保存其狀態。</span><span class="sxs-lookup"><span data-stu-id="6f83d-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="6f83d-107">終止執行中的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f83d-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="6f83d-108">會防止任何子活動保存的容器活動。</span><span class="sxs-lookup"><span data-stu-id="6f83d-108">A container activity that prevents child activities from persisting.</span></span>|
