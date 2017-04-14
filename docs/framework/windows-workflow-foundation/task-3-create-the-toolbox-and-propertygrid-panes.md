---
title: "工作 3：建立工具箱與 PropertyGrid 窗格 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 工作 3：建立工具箱與 PropertyGrid 窗格
在這個工作中，您將會建立 \[**工具箱**\] 和 \[**PropertyGrid**\] 窗格，並將它們加入至重新裝載的 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 中。  
  
 如需參考，請參閱本主題結尾的程式碼，此程式碼是在完成[重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)主題系列後的 MainWindow.xaml.cs 檔案中。  
  
### 若要建立工具箱，並將它加入至方格  
  
1.  開啟您依照[工作 2：裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md) 中描述的程序所取得的 HostingApplication 專案。  
  
2.  以滑鼠右鍵按一下 \[**方案總管**\] 窗格中的 MainWindow.xaml 檔案，然後選取 \[**檢視程式碼**\]。  
  
3.  將 `GetToolboxControl` 方法加入至 `MainWindow` 類別 \(此方法會建立 <xref:System.Activities.Presentation.Toolbox.ToolboxControl>\)、將新 \[**工具箱**\] 分類加入至 \[**工具箱**\]，然後指派 <xref:System.Activities.Statements.Assign> 和 <xref:System.Activities.Statements.Sequence> 活動型別至該分類。  
  
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
  
4.  將 `AddToolbox` 私用方法加入至 `MainWindow` 類別，將 \[**工具箱**\] 放置在資料格線的最左欄。  
  
    ```csharp  
  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
  
    ```  
  
5.  在 `MainWindow()` 類別建構函式中加入 `AddToolBox` 方法的呼叫，如下列程式碼所示。  
  
    ```csharp  
  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
  
    ```  
  
6.  按 F5 以建置及執行您的方案。接著，應該會顯示 \[**工具箱**\]，其中包含 <xref:System.Activities.Statements.Assign> 和 <xref:System.Activities.Statements.Sequence> 活動。  
  
### 若要建立 PropertyGrid  
  
1.  以滑鼠右鍵按一下 \[**方案總管**\] 窗格中的 MainWindow.xaml 檔案，然後選取 \[**檢視程式碼**\]。  
  
2.  在 `MainWindow` 類別中加入 `AddPropertyInspector` 方法，將 **PropertyGrid** 窗格放置在資料格線的最右欄。  
  
    ```csharp  
  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
  
    ```  
  
3.  在 `MainWindow()` 類別建構函式中加入 `AddPropertyInspector` 方法的呼叫，如下列程式碼所示。  
  
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
  
4.  按 F5 以建置及執行方案。\[**工具箱**\]、工作流程設計畫布與 \[**PropertyGrid**\] 窗格應會全部顯示，當您將 <xref:System.Activities.Statements.Assign> 活動或 <xref:System.Activities.Statements.Sequence> 活動拖曳到設計畫布上時，屬性方格應會根據反白標示的活動更新。  
  
## 範例  
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
  
## 請參閱  
 [重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [工作 1：建立新的 Windows Presentation Foundation 應用程式](../../../docs/framework/windows-workflow-foundation//task-1-create-a-new-wpf-app.md)   
 [工作 2：裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md)