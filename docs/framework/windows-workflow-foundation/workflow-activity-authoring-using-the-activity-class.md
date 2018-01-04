---
title: "使用活動類別撰寫工作流程活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 52d29f9cbed65932b3f9e97f0e9275861953b5d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="be005-102">使用活動類別撰寫工作流程活動</span><span class="sxs-lookup"><span data-stu-id="be005-102">Workflow Activity Authoring Using the Activity Class</span></span>
<span data-ttu-id="be005-103">建立活動使用的最基本方式[!INCLUDE[wf](../../../includes/wf-md.md)]中[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]是建立繼承自一個類別<xref:System.Activities.Activity>，會建立功能藉由組裝來自訂活動或活動與[內建活動程式庫](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span><span class="sxs-lookup"><span data-stu-id="be005-103">The most basic way to create an activity using [!INCLUDE[wf](../../../includes/wf-md.md)] in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="be005-104">本主題示範如何建立會寫入兩個訊息至主控台的活動。</span><span class="sxs-lookup"><span data-stu-id="be005-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="be005-105">若要使用活動設計工具建立自訂活動</span><span class="sxs-lookup"><span data-stu-id="be005-105">To create a custom Activity using the activity designer</span></span>  
  
1.  <span data-ttu-id="be005-106">開啟 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="be005-106">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="be005-107">依序選取 [檔案]、[新增]、[專案]。</span><span class="sxs-lookup"><span data-stu-id="be005-107">Select File, New, Project.</span></span> <span data-ttu-id="be005-108">選取**Workflow 4.0**下**Visual C#**中**專案類型**視窗，並選取**v2010**節點。</span><span class="sxs-lookup"><span data-stu-id="be005-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="be005-109">選取**活動程式庫**中**範本**視窗。</span><span class="sxs-lookup"><span data-stu-id="be005-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="be005-110">將新專案命名為 HelloActivity。</span><span class="sxs-lookup"><span data-stu-id="be005-110">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="be005-111">開啟新活動。</span><span class="sxs-lookup"><span data-stu-id="be005-111">Open the new activity.</span></span>  <span data-ttu-id="be005-112">將 <xref:System.Activities.Statements.Sequence> 活動從工具箱拖曳至設計工具介面上。</span><span class="sxs-lookup"><span data-stu-id="be005-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>  
  
4.  <span data-ttu-id="be005-113">將 <xref:System.Activities.Statements.WriteLine> 活動拖曳至 <xref:System.Activities.Statements.Sequence> 活動中。</span><span class="sxs-lookup"><span data-stu-id="be005-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="be005-114">輸入`"Hello World"`（含引號） 到**文字**欄位。</span><span class="sxs-lookup"><span data-stu-id="be005-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>  
  
5.  <span data-ttu-id="be005-115">將第二個 <xref:System.Activities.Statements.WriteLine> 活動拖曳至 <xref:System.Activities.Statements.Sequence> 活動，放在第一個活動下方。</span><span class="sxs-lookup"><span data-stu-id="be005-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="be005-116">輸入`"Goodbye"`（含引號） 到**文字**欄位。</span><span class="sxs-lookup"><span data-stu-id="be005-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
