---
title: "工作 1：建立新的 Windows Presentation Foundation 應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a207b09ff7124bb161678627f365a6fa4021a38d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="b079c-102">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="b079c-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="b079c-103">在這個工作中，您將會使用 WPF 應用程式 Visual Studio 範本建立一個空的 [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] 應用程式，再將參考加入至適當的 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 工作流程組件。</span><span class="sxs-lookup"><span data-stu-id="b079c-103">In this task, you will create an empty [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="b079c-104">若要建立 WPF 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="b079c-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="b079c-105">開啟[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]以及**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="b079c-105">Open [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="b079c-106">在**新專案**對話方塊方塊中，選取  **Visual C#**或**Visual Basic**從**已安裝的範本**的左側窗格方塊。</span><span class="sxs-lookup"><span data-stu-id="b079c-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="b079c-107">如果您選擇的語言沒有出現，查看 **其他語言**。</span><span class="sxs-lookup"><span data-stu-id="b079c-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="b079c-108">選取**Windows**中**已安裝的範本**窗格。</span><span class="sxs-lookup"><span data-stu-id="b079c-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="b079c-109">在上方窗格中，確認 （預設值） **.NET Framework 4**已選取下拉式清單方塊中，然後選取**WPF 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="b079c-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="b079c-110">設定專案的名稱**HostingApplication**視窗的底部。</span><span class="sxs-lookup"><span data-stu-id="b079c-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="b079c-111">方案名稱設定為**RehostingTheDesigner**。</span><span class="sxs-lookup"><span data-stu-id="b079c-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="b079c-112">按一下**確定**建立應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="b079c-112">Click **OK** to create the application project.</span></span> [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]<span data-ttu-id="b079c-113"> 會為應用程式建立基本 WPF UI，並且包含適當的 XAML 和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="b079c-113"> creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="b079c-114">將參考加入至**WorkflowModel**組件。</span><span class="sxs-lookup"><span data-stu-id="b079c-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="b079c-115">若要這樣做，請在**方案總管 中**，以滑鼠右鍵按一下**HostingApplication**專案，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="b079c-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="b079c-116">在**加入參考**對話方塊中，按一下  **.NET**索引標籤上，按住 CTRL 鍵，選取下列組件，，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="b079c-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="b079c-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="b079c-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="b079c-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="b079c-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="b079c-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="b079c-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="b079c-120">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="b079c-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="b079c-121">請參閱[工作 2： 裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)以了解如何裝載工作流程設計工具設計畫布。</span><span class="sxs-lookup"><span data-stu-id="b079c-121">See [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b079c-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="b079c-122">See Also</span></span>  
 [<span data-ttu-id="b079c-123">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="b079c-123">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="b079c-124">工作 2：裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="b079c-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
