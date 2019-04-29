---
title: WF 中的基本活動
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: d87125d8d85fa33a49651dfabb840881b0e216ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780701"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="22830-102">WF 中的基本活動</span><span class="sxs-lookup"><span data-stu-id="22830-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="22830-103">提供數個系統供應式活動，這些活動會提供一個方便的機制來執行一般工作。</span><span class="sxs-lookup"><span data-stu-id="22830-103">provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="22830-104">活動</span><span class="sxs-lookup"><span data-stu-id="22830-104">Activity</span></span>|<span data-ttu-id="22830-105">描述</span><span class="sxs-lookup"><span data-stu-id="22830-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="22830-106">指派值給目前範圍中的變數。</span><span class="sxs-lookup"><span data-stu-id="22830-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="22830-107">使一個執行路徑進入閒置狀態，或許可讓工作流程卸載。</span><span class="sxs-lookup"><span data-stu-id="22830-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="22830-108">執行衍生自 <xref:System.Activities.ActivityDelegate> 且公開為屬性的委派。</span><span class="sxs-lookup"><span data-stu-id="22830-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="22830-109">執行 CLR 物件的公用方法。</span><span class="sxs-lookup"><span data-stu-id="22830-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="22830-110">將指定的字串寫入主控台或指定的 <xref:System.IO.TextWriter> 物件。</span><span class="sxs-lookup"><span data-stu-id="22830-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
