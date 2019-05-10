---
title: 工作 1：建立新的 Windows Presentation Foundation 應用程式
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 44152f0af73b134218cd975d93e186166b1e57ae
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665313"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="80ad9-102">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="80ad9-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="80ad9-103">在這個工作中，您會使用 WPF 應用程式的 Visual Studio 範本建立空白的 Windows Presentation Foundation (WPF) 應用程式，並將參考加入至適當[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]工作流程組件。</span><span class="sxs-lookup"><span data-stu-id="80ad9-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="80ad9-104">若要建立 WPF 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="80ad9-104">To create the WPF Application project</span></span>  
  
1. <span data-ttu-id="80ad9-105">開啟 Visual Studio 並在**檔案**功能表上，指向**新增**，然後按一下**專案**。</span><span class="sxs-lookup"><span data-stu-id="80ad9-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="80ad9-106">在 **新的專案**對話方塊方塊中，選取**Visual C#** 或**Visual Basic**從**已安裝的範本**在左側窗格文字方塊的邊。</span><span class="sxs-lookup"><span data-stu-id="80ad9-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="80ad9-107">如果您選擇的語言沒有出現，請查看底下**其他語言**。</span><span class="sxs-lookup"><span data-stu-id="80ad9-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3. <span data-ttu-id="80ad9-108">選取  **Windows**中**已安裝的範本**窗格。</span><span class="sxs-lookup"><span data-stu-id="80ad9-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4. <span data-ttu-id="80ad9-109">在上方窗格中，確認已選取 （預設值） **.NET Framework 4**已在下拉式清單方塊中，選取，然後選取**WPF 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="80ad9-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5. <span data-ttu-id="80ad9-110">設定專案的名稱**HostingApplication**視窗的底部。</span><span class="sxs-lookup"><span data-stu-id="80ad9-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6. <span data-ttu-id="80ad9-111">將方案名稱設定為**RehostingTheDesigner**。</span><span class="sxs-lookup"><span data-stu-id="80ad9-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7. <span data-ttu-id="80ad9-112">按一下 **確定**建立應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="80ad9-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="80ad9-113">Visual Studio 會建立基本的 WPF UI，您的應用程式，並包含適當的 XAML 和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="80ad9-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8. <span data-ttu-id="80ad9-114">將參考加入至**WorkflowModel**組件。</span><span class="sxs-lookup"><span data-stu-id="80ad9-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="80ad9-115">若要這樣做，請在**方案總管**，以滑鼠右鍵按一下**HostingApplication**專案，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="80ad9-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="80ad9-116">在 [**加入參考**] 對話方塊中，按一下 **.NET**索引標籤上，按住 CTRL 鍵，選取下列組件，，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="80ad9-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    - <span data-ttu-id="80ad9-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="80ad9-117">System.Activities</span></span>  
  
    - <span data-ttu-id="80ad9-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="80ad9-118">System.Activities.Presentation</span></span>  
  
    - <span data-ttu-id="80ad9-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="80ad9-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="80ad9-120">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="80ad9-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="80ad9-121">請參閱[工作 2:裝載工作流程設計工具](task-2-host-the-workflow-designer.md)以了解如何裝載工作流程設計工具設計畫布。</span><span class="sxs-lookup"><span data-stu-id="80ad9-121">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ad9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80ad9-122">See also</span></span>

- [<span data-ttu-id="80ad9-123">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="80ad9-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="80ad9-124">工作 2:裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="80ad9-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
