---
title: 工作 3：建立工具箱與 PropertyGrid 窗格
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 402a25c1cb82c245afa94f58cefc180515622ea9
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275857"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>工作 3：建立工具箱與 PropertyGrid 窗格

在這項工作中，您將建立 [**工具箱**] 和 [ **PropertyGrid** ] 窗格，並將其新增至 [重新裝載 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]]。

如需參考，在完成重新裝載中的三個工作之後，應該在 MainWindow.xaml.cs 檔案中的程式碼，本主題的結尾會提供[工作流程設計工具](rehosting-the-workflow-designer.md)的主題系列。

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>若要建立工具箱，並將它加入至方格

1. 依照 [Task 2 中所述的程式，開啟您所取得的 HostingApplication 專案：裝載工作流程設計工具 @ no__t-0。

2. 在 [**方案總管**] 窗格中，以滑鼠右鍵按一下 [ *mainwindow.xaml* ] 檔案，然後選取 [ **View Code**]。

3. 將 `GetToolboxControl` 方法加入至建立 <xref:System.Activities.Presentation.Toolbox.ToolboxControl> 的 `MainWindow` 類別中，將新的 [**工具箱**] 分類加入 [**工具箱**]，並將 <xref:System.Activities.Statements.Assign> 和 <xref:System.Activities.Statements.Sequence> 活動類型指派給該分類。

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

4. 將私用 `AddToolbox` 方法加入至 `MainWindow` 類別，將 [**工具箱**] 放在方格的左欄中。

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. 在 `MainWindow()` 類別的函式中，新增對 `AddToolBox` 方法的呼叫，如下列程式碼所示：

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. 按<kbd>F5</kbd>以建立並執行您的方案。 包含 <xref:System.Activities.Statements.Assign> 和 @no__t 2 活動的 [**工具箱**] 應該會顯示。

## <a name="to-create-the-propertygrid"></a>若要建立 PropertyGrid

1. 在 [**方案總管**] 窗格中，以滑鼠右鍵按一下 [ *mainwindow.xaml* ] 檔案，然後選取 [ **View Code**]。

2. 將 `AddPropertyInspector` 方法加入至 `MainWindow` 類別，將 [ **PropertyGrid** ] 窗格放在方格的最右邊資料行中：

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. 在 `MainWindow()` 類別的函式中，新增對 `AddPropertyInspector` 方法的呼叫，如下列程式碼所示：

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

4. 按<kbd>F5</kbd>以建立並執行方案。 [**工具箱**]、[工作流程設計畫布] 和 [ **PropertyGrid** ] 窗格都應該顯示出來，而且當您將 [<xref:System.Activities.Statements.Assign>] 活動或 [@no__t 3] 活動拖曳至 [設計] 畫布上時，屬性方格應該會根據反白顯示的活動進行更新。

## <a name="example"></a>範例

*MainWindow.xaml.cs*檔案現在應該包含下列程式碼：

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

## <a name="see-also"></a>另請參閱

- [重新裝載工作流程設計工具](rehosting-the-workflow-designer.md)
- [Task 1：建立新的 Windows Presentation Foundation 應用程式 @ no__t-0
- [Task 2：裝載工作流程設計工具 @ no__t-0
