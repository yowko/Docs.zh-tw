---
title: 工作 1：建立新的 Windows Presentation Foundation 應用程式
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031890"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="3b115-102">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="3b115-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>

<span data-ttu-id="3b115-103">在這項工作中，您將使用 WPF 應用程式 Visual Studio 範本來建立空的 Windows Presentation Foundation （WPF）應用程式，並將參考新增至適當的 @no__t 0 工作流程元件。</span><span class="sxs-lookup"><span data-stu-id="3b115-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
## <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="3b115-104">若要建立 WPF 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="3b115-104">To create the WPF Application project</span></span>

1. <span data-ttu-id="3b115-105">開啟 Visual Studio，並在 **[檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。</span><span class="sxs-lookup"><span data-stu-id="3b115-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="3b115-106">在 [**新增專案**] 對話方塊中，從方塊左側的 [**已安裝的範本**] 窗格中，選取 [**視覺C#效果**] 或 [ **Visual Basic** ]。</span><span class="sxs-lookup"><span data-stu-id="3b115-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="3b115-107">如果未出現您選擇的語言，請查看 [**其他語言**]。</span><span class="sxs-lookup"><span data-stu-id="3b115-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>

3. <span data-ttu-id="3b115-108">在 [**已安裝的範本**] 窗格中選取 [ **Windows** ]。</span><span class="sxs-lookup"><span data-stu-id="3b115-108">Select **Windows** in the **Installed Templates** pane.</span></span>

4. <span data-ttu-id="3b115-109">在上方窗格中，確認已在下拉式清單方塊中選取 [ **.NET Framework 4** ] （預設值），然後選取 [ **WPF 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="3b115-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>

5. <span data-ttu-id="3b115-110">在視窗底部，將專案的名稱設定為**HostingApplication** 。</span><span class="sxs-lookup"><span data-stu-id="3b115-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>

6. <span data-ttu-id="3b115-111">將 [方案名稱] 設定為**設定為 rehostingthedesigner**。</span><span class="sxs-lookup"><span data-stu-id="3b115-111">Set the solution name to **RehostingTheDesigner**.</span></span>

7. <span data-ttu-id="3b115-112">按一下 **[確定]** 以建立應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="3b115-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="3b115-113">Visual Studio 會為您的應用程式建立基本 WPF UI，並且包含適當的 XAML 和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="3b115-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>

8. <span data-ttu-id="3b115-114">新增**WorkflowModel**元件的參考。</span><span class="sxs-lookup"><span data-stu-id="3b115-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="3b115-115">若要這麼做，請在**方案總管**中，以滑鼠右鍵按一下**HostingApplication**專案，然後選取 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="3b115-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>

9. <span data-ttu-id="3b115-116">在 [**加入參考**] 對話方塊中，按一下 [ **.net** ] 索引標籤，按住 CTRL 鍵，選取下列元件，然後按一下 **[確定]** ：</span><span class="sxs-lookup"><span data-stu-id="3b115-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>

    - <span data-ttu-id="3b115-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="3b115-117">System.Activities</span></span>
    - <span data-ttu-id="3b115-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="3b115-118">System.Activities.Presentation</span></span>
    - <span data-ttu-id="3b115-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="3b115-119">System.Activities.Core.Presentation</span></span>

10. <span data-ttu-id="3b115-120">請參閱 [Task 2：裝載工作流程設計工具 @ no__t-0，以瞭解如何裝載工作流程設計工具設計畫布。</span><span class="sxs-lookup"><span data-stu-id="3b115-120">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b115-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b115-121">See also</span></span>

- [<span data-ttu-id="3b115-122">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="3b115-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- <span data-ttu-id="3b115-123">[Task 2：裝載工作流程設計工具 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="3b115-123">[Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md)</span></span>
