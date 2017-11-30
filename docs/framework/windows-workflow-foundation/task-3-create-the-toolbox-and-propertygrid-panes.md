---
title: "工作 3：建立工具箱與 PropertyGrid 窗格"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6896e97a4f9b7625efcef40164c3497ef4f7c90a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="1a1bd-102">工作 3：建立工具箱與 PropertyGrid 窗格</span><span class="sxs-lookup"><span data-stu-id="1a1bd-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>
<span data-ttu-id="1a1bd-103">在這個工作中，您將建立**工具箱**和**PropertyGrid**窗格並將其新增至重新裝載[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span>  
  
 <span data-ttu-id="1a1bd-104">如需參考，應該在 MainWindow.xaml.cs 檔案完成三個之後的程式碼中的工作[重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)一系列的主題會提供於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="1a1bd-105">若要建立工具箱，並將它加入至方格</span><span class="sxs-lookup"><span data-stu-id="1a1bd-105">To create the Toolbox and add it to the grid</span></span>  
  
1.  <span data-ttu-id="1a1bd-106">開啟 HostingApplication 專案中所述的程序取得[工作 2： 裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).</span></span>  
  
2.  <span data-ttu-id="1a1bd-107">在**方案總管 中** 窗格中，以滑鼠右鍵按一下 MainWindow.xaml 檔案，然後選取**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-107">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
3.  <span data-ttu-id="1a1bd-108">新增`GetToolboxControl`方法`MainWindow`類別會建立<xref:System.Activities.Presentation.Toolbox.ToolboxControl>，加入新**工具箱**類別**工具箱**，並指派<xref:System.Activities.Statements.Assign>和<xref:System.Activities.Statements.Sequence>活動類型，該類別目錄。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4.  <span data-ttu-id="1a1bd-109">加入私用`AddToolbox`方法`MainWindow`類別，將**工具箱**方格左側的資料行中。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  <span data-ttu-id="1a1bd-110">在 `AddToolBox` 類別建構函式中加入 `MainWindow()` 方法的呼叫，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  <span data-ttu-id="1a1bd-111">按 F5 以建置及執行您的方案。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-111">Press F5 to build and run your solution.</span></span> <span data-ttu-id="1a1bd-112">**工具箱**包含<xref:System.Activities.Statements.Assign>和<xref:System.Activities.Statements.Sequence>活動應該會顯示。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>  
  
### <a name="to-create-the-propertygrid"></a><span data-ttu-id="1a1bd-113">若要建立 PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="1a1bd-113">To create the PropertyGrid</span></span>  
  
1.  <span data-ttu-id="1a1bd-114">在**方案總管 中** 窗格中，以滑鼠右鍵按一下 MainWindow.xaml 檔案，然後選取**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-114">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="1a1bd-115">新增`AddPropertyInspector`方法`MainWindow`類別來放置**PropertyGrid**在方格上最右側資料行中的窗格。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid.</span></span>  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  <span data-ttu-id="1a1bd-116">在 `AddPropertyInspector` 類別建構函式中加入 `MainWindow()` 方法的呼叫，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
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
  
4.  <span data-ttu-id="1a1bd-117">按 F5 以建置及執行方案。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-117">Press F5 to build and run the solution.</span></span> <span data-ttu-id="1a1bd-118">**工具箱**，工作流程設計畫布，和**PropertyGrid**窗格應會全部顯示，以及當您拖曳<xref:System.Activities.Statements.Assign>活動或<xref:System.Activities.Statements.Sequence>拖曳到設計畫布上的活動屬性方格應該更新根據反白顯示的活動。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a1bd-119">範例</span><span class="sxs-lookup"><span data-stu-id="1a1bd-119">Example</span></span>  
 <span data-ttu-id="1a1bd-120">MainWindow.xaml.cs 檔案現在應該會包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a1bd-120">The MainWindow.xaml.cs file should now contain the following code.</span></span>  
  
```  
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
//dlls added  
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
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
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
  
## <a name="see-also"></a><span data-ttu-id="1a1bd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a1bd-121">See Also</span></span>  
 [<span data-ttu-id="1a1bd-122">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="1a1bd-122">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="1a1bd-123">工作 1：建立新的 Windows Presentation Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="1a1bd-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [<span data-ttu-id="1a1bd-124">工作 2：裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="1a1bd-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
