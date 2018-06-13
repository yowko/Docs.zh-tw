---
title: 工作 3：建立工具箱與 PropertyGrid 窗格
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 9bfce22e9de1d6115cb88daddcd2dca355b6bae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519746"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>工作 3：建立工具箱與 PropertyGrid 窗格
在這個工作中，您將建立**工具箱**和**PropertyGrid**窗格並將其新增至重新裝載[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]。  
  
 如需參考，應該在 MainWindow.xaml.cs 檔案完成三個之後的程式碼中的工作[重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)一系列的主題會提供於本主題的結尾。  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>若要建立工具箱，並將它加入至方格  
  
1.  開啟 HostingApplication 專案中所述的程序取得[工作 2： 裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)。  
  
2.  在**方案總管 中** 窗格中，以滑鼠右鍵按一下 MainWindow.xaml 檔案，然後選取**檢視程式碼**。  
  
3.  新增`GetToolboxControl`方法`MainWindow`類別會建立<xref:System.Activities.Presentation.Toolbox.ToolboxControl>，加入新**工具箱**類別**工具箱**，並指派<xref:System.Activities.Statements.Assign>和<xref:System.Activities.Statements.Sequence>活動類型，該類別目錄。  
  
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
  
4.  加入私用`AddToolbox`方法`MainWindow`類別，將**工具箱**方格左側的資料行中。  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  在 `AddToolBox` 類別建構函式中加入 `MainWindow()` 方法的呼叫，如下列程式碼所示。  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  按 F5 以建置及執行您的方案。 **工具箱**包含<xref:System.Activities.Statements.Assign>和<xref:System.Activities.Statements.Sequence>活動應該會顯示。  
  
### <a name="to-create-the-propertygrid"></a>若要建立 PropertyGrid  
  
1.  在**方案總管 中** 窗格中，以滑鼠右鍵按一下 MainWindow.xaml 檔案，然後選取**檢視程式碼**。  
  
2.  新增`AddPropertyInspector`方法`MainWindow`類別來放置**PropertyGrid**在方格上最右側資料行中的窗格。  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  在 `AddPropertyInspector` 類別建構函式中加入 `MainWindow()` 方法的呼叫，如下列程式碼所示。  
  
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
  
4.  按 F5 以建置及執行方案。 **工具箱**，工作流程設計畫布，和**PropertyGrid**窗格應會全部顯示，以及當您拖曳<xref:System.Activities.Statements.Assign>活動或<xref:System.Activities.Statements.Sequence>拖曳到設計畫布上的活動屬性方格應該更新根據反白顯示的活動。  
  
## <a name="example"></a>範例  
 MainWindow.xaml.cs 檔案現在應該會包含下列程式碼。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [工作 1：建立新的 Windows Presentation Foundation 應用程式](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [工作 2：裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
