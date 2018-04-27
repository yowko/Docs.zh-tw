---
title: 重新裝載工作流程設計工具
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a37c37aa34db8f04a354d3b6e323c414b4c0ee07
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="c7350-102">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="c7350-102">Rehosting the Workflow Designer</span></span>
<span data-ttu-id="c7350-103">[!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 可因建立、修改與監控工作流程等目的，在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 之外的環境重新裝載。</span><span class="sxs-lookup"><span data-stu-id="c7350-103">The [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] can be rehosted in environments outside of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] for the purposes of creating, modifying, and monitoring workflows.</span></span>  
  
 <span data-ttu-id="c7350-104"><xref:System.Activities.Presentation.WorkflowDesigner> 型別是畫布、屬性方格與其他項目的包裝函式，並公開基本程式設計模型以處理大部分的設計工具重新裝載實例。</span><span class="sxs-lookup"><span data-stu-id="c7350-104">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="c7350-105">裝載<xref:System.Activities.Presentation.WorkflowDesigner>內 Windows Presentation Foundation (WPF) 應用程式是針對一般重新裝載案例[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c7350-105">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a Windows Presentation Foundation (WPF) application is a common rehosting scenario for [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7350-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="c7350-106">In This Section</span></span>  
 [<span data-ttu-id="c7350-107">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="c7350-107">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
  
 [<span data-ttu-id="c7350-108">工作 2：裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="c7350-108">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)  
  
 [<span data-ttu-id="c7350-109">工作 3：建立工具箱與 PropertyGrid 窗格</span><span class="sxs-lookup"><span data-stu-id="c7350-109">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)  
  
 [<span data-ttu-id="c7350-110">重新裝載之工作流程設計工具中新 Workflow Foundation 4.5 功能的支援</span><span class="sxs-lookup"><span data-stu-id="c7350-110">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)  
  
## <a name="see-also"></a><span data-ttu-id="c7350-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7350-111">See Also</span></span>  
 [<span data-ttu-id="c7350-112">自訂工作流程設計體驗</span><span class="sxs-lookup"><span data-stu-id="c7350-112">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
