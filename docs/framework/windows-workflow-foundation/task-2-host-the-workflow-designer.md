---
title: 工作 2：裝載工作流程設計工具
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 8e4c17ed182cec7748b9a1f11f76ff90aa60c39e
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715782"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="fbf6c-102">工作 2：裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="fbf6c-102">Task 2: Host the Workflow Designer</span></span>

<span data-ttu-id="fbf6c-103">本主題描述在 Windows Presentation Foundation （WPF）應用程式中裝載 Windows 工作流程設計工具實例的程式。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-103">This topic describes the procedure for hosting an instance of the Windows Workflow Designer in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="fbf6c-104">此程式會設定包含設計工具的**方格**控制項，以程式設計方式建立包含預設 <xref:System.Activities.Statements.Sequence> 活動之 <xref:System.Activities.Presentation.WorkflowDesigner> 的實例，註冊設計工具中繼資料以提供所有內建活動的設計工具支援，並將工作流程設計工具裝載于 WPF 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the Workflow Designer in the WPF application.</span></span>

## <a name="to-host-the-workflow-designer"></a><span data-ttu-id="fbf6c-105">若要裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="fbf6c-105">To host the workflow designer</span></span>

1. <span data-ttu-id="fbf6c-106">開啟您在工作[1：建立新的 Windows Presentation Foundation 應用程式](task-1-create-a-new-wpf-app.md)中建立的 HostingApplication 專案。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>

2. <span data-ttu-id="fbf6c-107">調整視窗大小，讓使用工作流程設計工具變得更容易。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-107">Adjust the size of the window to make it easier to use the Workflow Designer.</span></span> <span data-ttu-id="fbf6c-108">若要這麼做，請在設計工具中選取 [ **mainwindow.xaml** ]，按 F4 顯示 [**屬性**] 視窗，然後**在 [配置**] 區段中，將 [**寬度**] 設定為600，並將 [**高度**] 設為 [350] 的值。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>

3. <span data-ttu-id="fbf6c-109">選取設計工具中的 [**方格**] 面板（按一下**mainwindow.xaml**內的方塊），然後將 [**屬性**] 視窗頂端的 [**名稱**] 屬性設定為 "grid1"，以設定格線名稱。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>

4. <span data-ttu-id="fbf6c-110">在 [**屬性**] 視窗中，按一下 [`ColumnDefinitions`] 屬性旁的省略號（ **...** ），以開啟 [**集合編輯器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>

5. <span data-ttu-id="fbf6c-111">在 [**集合編輯器**] 對話方塊中，按一下 [**加入**] 按鈕三次，將三個數據行插入配置中。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="fbf6c-112">第一個資料行會包含 [**工具箱**]，第二個數據行會裝載工作流程設計工具，而第三個數據行則用於屬性偵測器。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-112">The first column will contain the **Toolbox**, the second column will host the Workflow Designer, and the third column will be used for the property inspector.</span></span>

6. <span data-ttu-id="fbf6c-113">將中間資料行的 `Width` 屬性設定為 "4 \*" 值。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-113">Set the `Width` property of the middle column to the value "4\*".</span></span>

7. <span data-ttu-id="fbf6c-114">按一下 [確定] 儲存變更。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="fbf6c-115">下列 XAML 會新增至您的*mainwindow.xaml*檔案：</span><span class="sxs-lookup"><span data-stu-id="fbf6c-115">The following XAML is added to your *MainWindow.xaml* file:</span></span>

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. <span data-ttu-id="fbf6c-116">在**方案總管**中，以滑鼠右鍵按一下*mainwindow.xaml* ，然後選取 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-116">In **Solution Explorer**, right-click *MainWindow.xaml* and select **View Code**.</span></span> <span data-ttu-id="fbf6c-117">遵循下列步驟修改程式碼：</span><span class="sxs-lookup"><span data-stu-id="fbf6c-117">Modify the code by following these steps:</span></span>

    1. <span data-ttu-id="fbf6c-118">加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="fbf6c-118">Add the following namespaces:</span></span>

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. <span data-ttu-id="fbf6c-119">若要宣告私用成員欄位以保存 <xref:System.Activities.Presentation.WorkflowDesigner>的實例，請將下列程式碼新增至 `MainWindow` 類別：</span><span class="sxs-lookup"><span data-stu-id="fbf6c-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class:</span></span>

        ```csharp
        public partial class MainWindow : Window
        {
            private WorkflowDesigner wd;

            public MainWindow()
            {
                InitializeComponent();
            }
        }
        ```

    3. <span data-ttu-id="fbf6c-120">將下列 `AddDesigner` 方法加入至 `MainWindow` 類別。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="fbf6c-121">此執行會建立 <xref:System.Activities.Presentation.WorkflowDesigner>的實例、在其中加入 <xref:System.Activities.Statements.Sequence> 活動，並將它放在 grid1**方格**的中間資料行中。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>

        ```csharp
        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. <span data-ttu-id="fbf6c-122">註冊設計工具中繼資料，為所有內建活動加入設計工具支援。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="fbf6c-123">這可讓您將工具箱中的活動拖放到工作流程設計工具中的原始 <xref:System.Activities.Statements.Sequence> 活動。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the Workflow Designer.</span></span> <span data-ttu-id="fbf6c-124">若要這麼做，請將 `RegisterMetadata` 方法新增至 `MainWindow` 類別：</span><span class="sxs-lookup"><span data-stu-id="fbf6c-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class:</span></span>

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        <span data-ttu-id="fbf6c-125">如需註冊活動設計工具的詳細資訊，請參閱[如何：建立自訂活動設計](how-to-create-a-custom-activity-designer.md)工具。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>

    5. <span data-ttu-id="fbf6c-126">在 `MainWindow` 類別建構函式中，將呼叫加入至先前宣告的方法，為中繼資料註冊設計工具支援，以建立 <xref:System.Activities.Presentation.WorkflowDesigner>。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > <span data-ttu-id="fbf6c-127">`RegisterMetadata` 方法會註冊內建活動 (包括 <xref:System.Activities.Statements.Sequence> 活動) 的設計工具中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="fbf6c-128">由於 `AddDesigner` 方法會使用 <xref:System.Activities.Statements.Sequence> 活動，因此必須先呼叫 `RegisterMetadata` 方法。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>

9. <span data-ttu-id="fbf6c-129">按<kbd>F5</kbd>以建立並執行方案。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-129">Press <kbd>F5</kbd> to build and run the solution.</span></span>

10. <span data-ttu-id="fbf6c-130">請參閱工作[3：建立工具箱和 PropertyGrid 窗格](task-3-create-the-toolbox-and-propertygrid-panes.md)，以瞭解如何在重新裝載工作流程設計工具中加入 [**工具箱**] 和 [ **PropertyGrid** ] 支援。</span><span class="sxs-lookup"><span data-stu-id="fbf6c-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbf6c-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf6c-131">See also</span></span>

- [<span data-ttu-id="fbf6c-132">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="fbf6c-132">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="fbf6c-133">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="fbf6c-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="fbf6c-134">工作 3：建立工具箱與 PropertyGrid 窗格</span><span class="sxs-lookup"><span data-stu-id="fbf6c-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
