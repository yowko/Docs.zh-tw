---
title: "工作 2：裝載工作流程設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# 工作 2：裝載工作流程設計工具
本主題說明在 [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] 應用程式中裝載 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 執行個體的程序。  
  
 此程序會設定包含設計工具的 **Grid** 控制項、以程式設計方式建立包含預設 <xref:System.Activities.Statements.Sequence> 活動之 <xref:System.Activities.Presentation.WorkflowDesigner> 的執行個體、註冊設計工具中繼資料以便為所有內建活動提供設計工具支援，以及在 [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] 應用程式中裝載 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]。  
  
### 若要裝載工作流程設計工具  
  
1.  開啟您在[工作 1：建立新的 Windows Presentation Foundation 應用程式](../../../docs/framework/windows-workflow-foundation//task-1-create-a-new-wpf-app.md) 中建立的 HostingApplication 專案。  
  
2.  將視窗調整至方便使用 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 的大小。若要執行這項操作，請在設計工具中選取 \[**MainWindow**\]，按 F4 顯示 \[**屬性**\] 視窗，然後在 \[**配置**\] 區段中將 \[**寬度**\] 設定成數值 600 並且將 \[**高度** 設定成數值 350。  
  
3.  選取設計工具中的 \[**方格**\] 面板 \(按一下 \[**MainWindow**\] 內的方塊\)，並且將 \[**屬性**\] 視窗頂端的 \[**Name**\] 屬性設定為 "grid1"，藉此設定方格名稱。  
  
4.  在 \[**屬性**\] 視窗中，按一下 `ColumnDefinitions` 屬性旁的省略符號 \(**...**\)，開啟 \[**集合編輯器**\] 對話方塊。  
  
5.  在 \[**集合編輯器**\] 對話方塊中，按三次 \[**加入**\] 按鈕將三個資料行插入配置中。第一個資料行包含 \[**工具箱**\]、第二個資料行將裝載 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]，而第三個資料行則用於屬性偵測器。  
  
6.  將中間資料行的 `Width` 屬性的值設定為 “4\*”。  
  
7.  按一下 \[**確定**\] 儲存變更。以下的 XAML 已加入至您的 MainWindow.xaml 檔案：  
  
    ```  
  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
  
    ```  
  
8.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 MainWindow.xaml，然後選取 \[**檢視程式碼**\]。遵循下列步驟修改程式碼：  
  
    1.  加入下列命名空間：  
  
        ```csharp  
  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
  
        ```  
  
    2.  若要宣告私用成員欄位以保留 <xref:System.Activities.Presentation.WorkflowDesigner> 的執行個體，請將下列程式碼加入至 `MainWindow` 類別。  
  
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
  
    3.  將下列 `AddDesigner` 方法加入至 `MainWindow` 類別。這個實作會建立 <xref:System.Activities.Presentation.WorkflowDesigner> 的執行個體、在其中加入 <xref:System.Activities.Statements.Sequence> 活動，然後將其置於 grid1 \[**方格**\] 的中間資料行中。  
  
        ```csharp  
  
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
  
        ```  
  
    4.  註冊設計工具中繼資料，為所有內建活動加入設計工具支援。這樣可讓您從工具箱將活動放置於 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 中的原始 <xref:System.Activities.Statements.Sequence> 活動。若要執行這項操作，請將 `RegisterMetadata` 方法加入至 `MainWindow` 類別。  
  
        ```csharp  
  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        ```  
  
         [!INCLUDE[crabout](../../../includes/crabout-md.md)]註冊活動設計工具的詳細資訊，請參閱[HOW TO：建立自訂活動設計工具](../../../docs/framework/windows-workflow-foundation//how-to-create-a-custom-activity-designer.md)。  
  
    5.  在 `MainWindow` 類別建構函式中，將呼叫加入至先前宣告的方法，為中繼資料註冊設計工具支援，以建立 <xref:System.Activities.Presentation.WorkflowDesigner>。  
  
        ```csharp  
        public MainWindow()  
        {  
            InitializeComponent();  
  
            // Register the metadata  
            RegisterMetadata();  
  
            // Add the WFF Designer  
            AddDesigner();  
        }  
  
        ```  
  
        > [!NOTE]
        >  `RegisterMetadata` 方法會註冊內建活動 \(包括 <xref:System.Activities.Statements.Sequence> 活動\) 的設計工具中繼資料。由於 `AddDesigner` 方法會使用 <xref:System.Activities.Statements.Sequence> 活動，因此必須先呼叫 `RegisterMetadata` 方法。  
  
9. 按 F5 以建置及執行方案。  
  
10. 請參閱[工作 3：建立工具箱與 PropertyGrid 窗格](../../../docs/framework/windows-workflow-foundation//task-3-create-the-toolbox-and-propertygrid-panes.md)，了解如何在重新裝載的工作流程設計工具中加入 \[**工具箱**\] 和 \[**PropertyGrid**\] 支援。  
  
## 請參閱  
 [重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [工作 1：建立新的 Windows Presentation Foundation 應用程式](../../../docs/framework/windows-workflow-foundation//task-1-create-a-new-wpf-app.md)   
 [工作 3：建立工具箱與 PropertyGrid 窗格](../../../docs/framework/windows-workflow-foundation//task-3-create-the-toolbox-and-propertygrid-panes.md)