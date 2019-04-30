---
title: 重新裝載工作流程設計工具
ms.date: 03/30/2017
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
ms.openlocfilehash: 98048ca58bf635f4e87241befa083dc240deaecf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968177"
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="deb12-102">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="deb12-102">Rehosting the Workflow Designer</span></span>
<span data-ttu-id="deb12-103">[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]可以基於建立、 修改和監視工作流程的重新裝載在 Visual Studio 2012 外部的環境中。</span><span class="sxs-lookup"><span data-stu-id="deb12-103">The [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] can be rehosted in environments outside of Visual Studio 2012 for the purposes of creating, modifying, and monitoring workflows.</span></span>

 <span data-ttu-id="deb12-104"><xref:System.Activities.Presentation.WorkflowDesigner> 型別是畫布、屬性方格與其他項目的包裝函式，並公開基本程式設計模型以處理大部分的設計工具重新裝載實例。</span><span class="sxs-lookup"><span data-stu-id="deb12-104">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="deb12-105">裝載<xref:System.Activities.Presentation.WorkflowDesigner>內 Windows Presentation Foundation (WPF) 應用程式是針對一般重新裝載案例[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="deb12-105">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a Windows Presentation Foundation (WPF) application is a common rehosting scenario for [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span>

## <a name="in-this-section"></a><span data-ttu-id="deb12-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="deb12-106">In This Section</span></span>
 [<span data-ttu-id="deb12-107">工作 1:建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="deb12-107">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)

 [<span data-ttu-id="deb12-108">工作 2:裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="deb12-108">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)

 [<span data-ttu-id="deb12-109">工作 3:建立工具箱與 PropertyGrid 窗格</span><span class="sxs-lookup"><span data-stu-id="deb12-109">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)

 [<span data-ttu-id="deb12-110">重新裝載之工作流程設計工具中新 Workflow Foundation 4.5 功能的支援</span><span class="sxs-lookup"><span data-stu-id="deb12-110">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](wf-features-in-the-rehosted-workflow-designer.md)

## <a name="see-also"></a><span data-ttu-id="deb12-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deb12-111">See also</span></span>

- [<span data-ttu-id="deb12-112">自訂工作流程設計體驗</span><span class="sxs-lookup"><span data-stu-id="deb12-112">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
