---
title: "工作 2：裝載工作流程設計工具"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f3b35bf4150dc05c6bedaaebc65a0a188c5c782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="task-2-host-the-workflow-designer"></a>工作 2：裝載工作流程設計工具
本主題說明在 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 應用程式中裝載 [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] 執行個體的程序。  
  
 程序會設定**方格**控制項，其中包含設計工具中，以程式設計方式建立的執行個體<xref:System.Activities.Presentation.WorkflowDesigner>，其中包含預設值<xref:System.Activities.Statements.Sequence>活動，註冊以提供設計工具中繼資料所有內建活動和裝載的設計工具支援[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]中[!INCLUDE[avalon2](../../../includes/avalon2-md.md)]應用程式。  
  
### <a name="to-host-the-workflow-designer"></a>若要裝載工作流程設計工具  
  
1.  開啟 HostingApplication 專案中建立您[工作 1： 建立新的 Windows Presentation Foundation 應用程式](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)。  
  
2.  將視窗調整至方便使用 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 的大小。 若要這樣做，請選取**MainWindow**在設計師中，按 F4 顯示**屬性**視窗中，然後在**配置**那里區段中，將**寬度** 600 的值和**高度**350 的值。  
  
3.  選取以設定方格名稱**方格**設計工具中的面板 (按一下 [] 內的方塊**MainWindow**) 和設定**名稱**頂端的屬性**屬性**"grid1"的視窗。  
  
4.  在**屬性**視窗中，按一下省略符號 (**...**) 旁邊`ColumnDefinitions`屬性可開啟**集合編輯器** 對話方塊。  
  
5.  在**集合編輯器**對話方塊中，按一下 **新增**按鈕將三個資料行插入配置三次。 第一個資料行會包含**工具箱**，第二個資料行將裝載[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]，和第三個資料行用於屬性偵測器。  
  
6.  設定`Width`屬性中間的資料行的值"4 *"。  
  
7.  按一下 [確定]  儲存變更。 以下的 XAML 已加入至您的 MainWindow.xaml 檔案：  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  在**方案總管 中**，以滑鼠右鍵按一下 MainWindow.xaml，然後選取**檢視程式碼**。 遵循下列步驟修改程式碼：  
  
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
  
    3.  將下列 `AddDesigner` 方法加入至 `MainWindow` 類別。 這個實作會建立的執行個體<xref:System.Activities.Presentation.WorkflowDesigner>，新增<xref:System.Activities.Statements.Sequence>活動，並將其置於 grid1 中間資料行中**方格**。  
  
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
  
    4.  註冊設計工具中繼資料，為所有內建活動加入設計工具支援。 這樣可讓您從工具箱將活動放置於 <xref:System.Activities.Statements.Sequence> 中的原始 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 活動。 若要執行這項操作，請將 `RegisterMetadata` 方法加入至 `MainWindow` 類別。  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         [!INCLUDE[crabout](../../../includes/crabout-md.md)]註冊活動設計工具，請參閱[How to： 建立自訂活動設計工具](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md)。  
  
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
        >  `RegisterMetadata` 方法會註冊內建活動 (包括 <xref:System.Activities.Statements.Sequence> 活動) 的設計工具中繼資料。 由於 `AddDesigner` 方法會使用 <xref:System.Activities.Statements.Sequence> 活動，因此必須先呼叫 `RegisterMetadata` 方法。  
  
9. 按 F5 以建置及執行方案。  
  
10. 請參閱[工作 3： 建立工具箱與 PropertyGrid 窗格](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)以了解如何加入**工具箱**和**PropertyGrid**到重新裝載工作流程設計工具支援。  
  
## <a name="see-also"></a>另請參閱  
 [重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [工作 1：建立新的 Windows Presentation Foundation 應用程式](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [工作 3：建立工具箱與 PropertyGrid 窗格](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
