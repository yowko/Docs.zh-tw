---
title: "WF 中的基本活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e411d922577dcb9d3ca322d61c0e10911a006027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="e3a3c-102">WF 中的基本活動</span><span class="sxs-lookup"><span data-stu-id="e3a3c-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="e3a3c-103"> 提供數個系統供應式活動，這些活動會提供一個方便的機制來執行一般工作。</span><span class="sxs-lookup"><span data-stu-id="e3a3c-103"> provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="e3a3c-104">活動</span><span class="sxs-lookup"><span data-stu-id="e3a3c-104">Activity</span></span>|<span data-ttu-id="e3a3c-105">描述</span><span class="sxs-lookup"><span data-stu-id="e3a3c-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="e3a3c-106">指派值給目前範圍中的變數。</span><span class="sxs-lookup"><span data-stu-id="e3a3c-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="e3a3c-107">使一個執行路徑進入閒置狀態，或許可讓工作流程卸載。</span><span class="sxs-lookup"><span data-stu-id="e3a3c-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="e3a3c-108">執行衍生自 <xref:System.Activities.ActivityDelegate> 且公開為屬性的委派。</span><span class="sxs-lookup"><span data-stu-id="e3a3c-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="e3a3c-109">執行 CLR 物件的公用方法。</span><span class="sxs-lookup"><span data-stu-id="e3a3c-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="e3a3c-110">將指定的字串寫入主控台或指定的 <xref:System.IO.TextWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="e3a3c-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
