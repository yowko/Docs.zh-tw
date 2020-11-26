---
title: WF 中的基本活動
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: 4f2c20c109d67a35ccc9c363c0a3631922161d2c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246071"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="fa5a6-102">WF 中的基本活動</span><span class="sxs-lookup"><span data-stu-id="fa5a6-102">Primitives Activities in WF</span></span>

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="fa5a6-103">提供數個系統供應式活動，這些活動會提供一個方便的機制來執行一般工作。</span><span class="sxs-lookup"><span data-stu-id="fa5a6-103">provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="fa5a6-104">活動</span><span class="sxs-lookup"><span data-stu-id="fa5a6-104">Activity</span></span>|<span data-ttu-id="fa5a6-105">描述</span><span class="sxs-lookup"><span data-stu-id="fa5a6-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="fa5a6-106">指派值給目前範圍中的變數。</span><span class="sxs-lookup"><span data-stu-id="fa5a6-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="fa5a6-107">使一個執行路徑進入閒置狀態，或許可讓工作流程卸載。</span><span class="sxs-lookup"><span data-stu-id="fa5a6-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="fa5a6-108">執行衍生自 <xref:System.Activities.ActivityDelegate> 且公開為屬性的委派。</span><span class="sxs-lookup"><span data-stu-id="fa5a6-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="fa5a6-109">執行 CLR 物件的公用方法。</span><span class="sxs-lookup"><span data-stu-id="fa5a6-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="fa5a6-110">將指定的字串寫入主控台或指定的 <xref:System.IO.TextWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="fa5a6-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
