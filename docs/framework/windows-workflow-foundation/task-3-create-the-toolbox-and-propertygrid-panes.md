---
title: 工作 3：建立工具箱與 PropertyGrid 窗格
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 29e50b24135cd3d6a02052d846e1781b0d9fa325
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716223"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="045f6-102">工作 3：建立工具箱與 PropertyGrid 窗格</span><span class="sxs-lookup"><span data-stu-id="045f6-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>

<span data-ttu-id="045f6-103">在這項工作中，您將建立 [**工具箱**] 和 [ **PropertyGrid** ] 窗格，並將其新增至重新裝載 Windows 工作流程設計工具。</span><span class="sxs-lookup"><span data-stu-id="045f6-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted Windows Workflow Designer.</span></span>

<span data-ttu-id="045f6-104">如需參考，在完成重新裝載中的三個工作之後，應該在 MainWindow.xaml.cs 檔案中的程式碼，本主題的結尾會提供[工作流程設計工具](rehosting-the-workflow-designer.md)的主題系列。</span><span class="sxs-lookup"><span data-stu-id="045f6-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="045f6-105">若要建立工具箱，並將它加入至方格</span><span class="sxs-lookup"><span data-stu-id="045f6-105">To create the Toolbox and add it to the grid</span></span>

1. <span data-ttu-id="045f6-106">遵循工作[2：裝載工作流程設計工具](task-2-host-the-workflow-designer.md)中所述的程式，開啟您取得的 HostingApplication 專案。</span><span class="sxs-lookup"><span data-stu-id="045f6-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md).</span></span>

2. <span data-ttu-id="045f6-107">在 [**方案總管**] 窗格中，以滑鼠右鍵按一下 [ *mainwindow.xaml* ] 檔案，然後選取 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="045f6-107">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

3. <span data-ttu-id="045f6-108">將 `GetToolboxControl` 方法加入至建立 <xref:System.Activities.Presentation.Toolbox.ToolboxControl>的 `MainWindow` 類別，將新的 [**工具箱**] 分類加入 [**工具箱**]，並將 <xref:System.Activities.Statements.Assign> 和 <xref:System.Activities.Statements.Sequence> 活動類型指派給該分類。</span><span class="sxs-lookup"><span data-stu-id="045f6-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>

    ```csharp
    private ToolboxControl GetToolboxControl()
    {
        // Create the ToolBoxControl.
        var ctrl = new ToolboxControl();

        // Create a category.
        var category = new ToolboxCategory("category1");

        // Create Toolbox items.
        var tool1 =
            new ToolboxItemWrapper("System.Activities.Statements.Assign",
            typeof(Assign).Assembly.FullName, null, "Assign");

        var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
            typeof(Sequence).Assembly.FullName, null, "Sequence");

        // Add the Toolbox items to the category.
        category.Add(tool1);
        category.Add(tool2);

        // Add the category to the ToolBox control.
        ctrl.Categories.Add(category);
        return ctrl;
    }
    ```

4. <span data-ttu-id="045f6-109">將私用 `AddToolbox` 方法加入 `MainWindow` 類別，將 [**工具箱**] 放在方格的左欄中。</span><span class="sxs-lookup"><span data-stu-id="045f6-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. <span data-ttu-id="045f6-110">在 `MainWindow()` 類別的函式中，新增對 `AddToolBox` 方法的呼叫，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="045f6-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. <span data-ttu-id="045f6-111">按<kbd>F5</kbd>以建立並執行您的方案。</span><span class="sxs-lookup"><span data-stu-id="045f6-111">Press <kbd>F5</kbd> to build and run your solution.</span></span> <span data-ttu-id="045f6-112">應該會顯示包含 [<xref:System.Activities.Statements.Assign>] 和 [<xref:System.Activities.Statements.Sequence>] 活動的 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="045f6-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>

## <a name="to-create-the-propertygrid"></a><span data-ttu-id="045f6-113">若要建立 PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="045f6-113">To create the PropertyGrid</span></span>

1. <span data-ttu-id="045f6-114">在 [**方案總管**] 窗格中，以滑鼠右鍵按一下 [ *mainwindow.xaml* ] 檔案，然後選取 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="045f6-114">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

2. <span data-ttu-id="045f6-115">將 `AddPropertyInspector` 方法加入 `MainWindow` 類別，將 [ **PropertyGrid** ] 窗格放在方格的最右邊資料行中：</span><span class="sxs-lookup"><span data-stu-id="045f6-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid:</span></span>

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. <span data-ttu-id="045f6-116">在 `MainWindow()` 類別的函式中，新增對 `AddPropertyInspector` 方法的呼叫，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="045f6-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();
        this.AddToolBox();

        this.AddPropertyInspector();
    }
    ```

4. <span data-ttu-id="045f6-117">按<kbd>F5</kbd>以建立並執行方案。</span><span class="sxs-lookup"><span data-stu-id="045f6-117">Press <kbd>F5</kbd> to build and run the solution.</span></span> <span data-ttu-id="045f6-118">[**工具箱**]、[工作流程設計畫布] 和 [ **PropertyGrid** ] 窗格都應該顯示出來，而且當您將 [<xref:System.Activities.Statements.Assign>] 活動或 [<xref:System.Activities.Statements.Sequence>] 活動拖曳至 [設計] 畫布上時，屬性方格應該會根據反白顯示的活動進行更新。</span><span class="sxs-lookup"><span data-stu-id="045f6-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>

## <a name="example"></a><span data-ttu-id="045f6-119">範例</span><span class="sxs-lookup"><span data-stu-id="045f6-119">Example</span></span>

<span data-ttu-id="045f6-120">*MainWindow.xaml.cs*檔案現在應該包含下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="045f6-120">The *MainWindow.xaml.cs* file should now contain the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
// dlls added.
using System.Activities;
using System.Activities.Core.Presentation;
using System.Activities.Presentation;
using System.Activities.Presentation.Metadata;
using System.Activities.Presentation.Toolbox;
using System.Activities.Statements;
using System.ComponentModel;

namespace HostingApplication
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private WorkflowDesigner wd;

        public MainWindow()
        {
            InitializeComponent();
            RegisterMetadata();
            AddDesigner();
            this.AddToolBox();
            this.AddPropertyInspector();
        }

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

        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }

        private ToolboxControl GetToolboxControl()
        {
            // Create the ToolBoxControl.
            var ctrl = new ToolboxControl();

            // Create a category.
            var category = new ToolboxCategory("category1");

            // Create Toolbox items.
            var tool1 =
                new ToolboxItemWrapper("System.Activities.Statements.Assign",
                typeof(Assign).Assembly.FullName, null, "Assign");

            var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
                typeof(Sequence).Assembly.FullName, null, "Sequence");

            // Add the Toolbox items to the category.
            category.Add(tool1);
            category.Add(tool2);

            // Add the category to the ToolBox control.
            ctrl.Categories.Add(category);
            return ctrl;
        }

        private void AddToolBox()
        {
            ToolboxControl tc = GetToolboxControl();
            Grid.SetColumn(tc, 0);
            grid1.Children.Add(tc);
        }

        private void AddPropertyInspector()
        {
            Grid.SetColumn(wd.PropertyInspectorView, 2);
            grid1.Children.Add(wd.PropertyInspectorView);
        }

    }
}
```

## <a name="see-also"></a><span data-ttu-id="045f6-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="045f6-121">See also</span></span>

- [<span data-ttu-id="045f6-122">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="045f6-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="045f6-123">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="045f6-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="045f6-124">工作 2：裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="045f6-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
