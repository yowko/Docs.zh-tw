---
title: 重新裝載工作流程設計工具
description: 您可以在 Visual Studio 以外的環境中重新裝載 Windows 工作流程設計工具，以建立、修改和監視工作流程。
ms.date: 03/30/2017
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
ms.openlocfilehash: 8c3a67d0beecdfcf4f99580bb6ec25fea6473718
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245896"
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="3e4b5-103">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="3e4b5-103">Rehosting the Workflow Designer</span></span>

<span data-ttu-id="3e4b5-104">Windows 工作流程設計工具可在 Visual Studio 2012 以外的環境中重新裝載，以建立、修改和監視工作流程。</span><span class="sxs-lookup"><span data-stu-id="3e4b5-104">The Windows Workflow Designer can be rehosted in environments outside of Visual Studio 2012 for the purposes of creating, modifying, and monitoring workflows.</span></span>

 <span data-ttu-id="3e4b5-105"><xref:System.Activities.Presentation.WorkflowDesigner> 型別是畫布、屬性方格與其他項目的包裝函式，並公開基本程式設計模型以處理大部分的設計工具重新裝載實例。</span><span class="sxs-lookup"><span data-stu-id="3e4b5-105">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="3e4b5-106">在 <xref:System.Activities.Presentation.WorkflowDesigner> Windows Presentation Foundation 中裝載 (WPF) 應用程式是工作流程設計工具常見的重新裝載案例。</span><span class="sxs-lookup"><span data-stu-id="3e4b5-106">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a Windows Presentation Foundation (WPF) application is a common rehosting scenario for Workflow Designer.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3e4b5-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="3e4b5-107">In This Section</span></span>

 [<span data-ttu-id="3e4b5-108">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="3e4b5-108">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)

 [<span data-ttu-id="3e4b5-109">工作 2：裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="3e4b5-109">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)

 [<span data-ttu-id="3e4b5-110">工作 3：建立工具箱與 PropertyGrid 窗格</span><span class="sxs-lookup"><span data-stu-id="3e4b5-110">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)

 [<span data-ttu-id="3e4b5-111">針對重新裝載之工作流程設計工具中的新 Workflow Foundation 4.5 功能提供的支援</span><span class="sxs-lookup"><span data-stu-id="3e4b5-111">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](wf-features-in-the-rehosted-workflow-designer.md)

## <a name="see-also"></a><span data-ttu-id="3e4b5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e4b5-112">See also</span></span>

- [<span data-ttu-id="3e4b5-113">自訂工作流程設計經驗</span><span class="sxs-lookup"><span data-stu-id="3e4b5-113">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
