---
title: 重新裝載工作流程設計工具
description: Windows 工作流程設計工具可以在 Visual Studio 以外的環境中重新裝載，以建立、修改和監視工作流程。
ms.date: 03/30/2017
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
ms.openlocfilehash: 34709b84d445b2bb07e32bfd3f34d06072f125bf
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421419"
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="0312a-103">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="0312a-103">Rehosting the Workflow Designer</span></span>
<span data-ttu-id="0312a-104">Windows 工作流程設計工具可以在 Visual Studio 2012 以外的環境中重新裝載，以建立、修改和監視工作流程。</span><span class="sxs-lookup"><span data-stu-id="0312a-104">The Windows Workflow Designer can be rehosted in environments outside of Visual Studio 2012 for the purposes of creating, modifying, and monitoring workflows.</span></span>

 <span data-ttu-id="0312a-105"><xref:System.Activities.Presentation.WorkflowDesigner> 型別是畫布、屬性方格與其他項目的包裝函式，並公開基本程式設計模型以處理大部分的設計工具重新裝載實例。</span><span class="sxs-lookup"><span data-stu-id="0312a-105">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="0312a-106">在 <xref:System.Activities.Presentation.WorkflowDesigner> Windows Presentation Foundation （WPF）應用程式內裝載，是工作流程設計工具常見的重新裝載案例。</span><span class="sxs-lookup"><span data-stu-id="0312a-106">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a Windows Presentation Foundation (WPF) application is a common rehosting scenario for Workflow Designer.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0312a-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="0312a-107">In This Section</span></span>
 [<span data-ttu-id="0312a-108">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="0312a-108">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)

 [<span data-ttu-id="0312a-109">工作 2：裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="0312a-109">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)

 [<span data-ttu-id="0312a-110">工作 3：建立工具箱與 PropertyGrid 窗格</span><span class="sxs-lookup"><span data-stu-id="0312a-110">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)

 [<span data-ttu-id="0312a-111">重新裝載之工作流程設計工具中新 Workflow Foundation 4.5 功能的支援</span><span class="sxs-lookup"><span data-stu-id="0312a-111">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](wf-features-in-the-rehosted-workflow-designer.md)

## <a name="see-also"></a><span data-ttu-id="0312a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0312a-112">See also</span></span>

- [<span data-ttu-id="0312a-113">自訂工作流程設計體驗</span><span class="sxs-lookup"><span data-stu-id="0312a-113">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
