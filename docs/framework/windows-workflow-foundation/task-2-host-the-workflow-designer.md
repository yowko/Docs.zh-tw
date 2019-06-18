---
title: 工作 2：裝載工作流程設計工具
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 553a02732e08fa148ffdee250df0305deb8e63b7
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169989"
---
# <a name="task-2-host-the-workflow-designer"></a>工作 2：裝載工作流程設計工具
本主題說明的程序裝載的執行個體[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]Windows Presentation Foundation (WPF) 應用程式中。  
  
 程序會設定**方格**控制項，其中包含設計工具中，以程式設計方式建立的執行個體<xref:System.Activities.Presentation.WorkflowDesigner>，其中包含預設<xref:System.Activities.Statements.Sequence>活動，會註冊提供的設計工具中繼資料設計工具支援所有內建活動和主機[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]在 WPF 應用程式。  
  
### <a name="to-host-the-workflow-designer"></a>若要裝載工作流程設計工具  
  
1. 開啟的 HostingApplication 專案中建立[工作 1:建立新的 Windows Presentation Foundation 應用程式](task-1-create-a-new-wpf-app.md)。  
  
2. 將視窗調整至方便使用 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 的大小。 若要這樣做，請選取**MainWindow**在設計師中，按 F4 顯示**屬性**視窗中，然後在**配置**那里區段中，將**寬度**值為 600，**高度**350 的值。  
  
3. 選取以設定資料格的名稱**格線**設計工具中的面板 (按一下 [] 內的方塊**MainWindow**) 和設定**名稱**頂端的屬性**屬性**為"grid1"視窗。  
  
4. 在 **屬性** 視窗中，按一下省略符號 ( **...** ) 旁`ColumnDefinitions`屬性可開啟**集合編輯器** 對話方塊。  
  
5. 在 [**集合編輯器**] 對話方塊中，按一下**新增**按鈕三次，以插入版面配置中的三個資料行。 第一個資料行會包含**工具箱**，第二個資料行將裝載[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]，以及第三個資料行用於屬性偵測器。  
  
6. 設定`Width`屬性中間的資料行的值"4 *"。  
  
7. 按一下 [確定]  儲存變更。 以下的 XAML 已加入至您的 MainWindow.xaml 檔案：  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8. 在 **方案總管**，以滑鼠右鍵按一下 MainWindow.xaml，然後選取**檢視程式碼**。 遵循下列步驟修改程式碼：  
  
    1. 加入下列命名空間：  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2. 若要宣告私用成員欄位以保留 <xref:System.Activities.Presentation.WorkflowDesigner> 的執行個體，請將下列程式碼加入至 `MainWindow` 類別。  
  
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
  
    3. 將下列 `AddDesigner` 方法加入至 `MainWindow` 類別。 這個實作會建立的執行個體<xref:System.Activities.Presentation.WorkflowDesigner>，將<xref:System.Activities.Statements.Sequence>活動，並將它放在中間的資料行的 grid1**格線**。  
  
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
  
    4. 註冊設計工具中繼資料，為所有內建活動加入設計工具支援。 這樣可讓您從工具箱將活動放置於 <xref:System.Activities.Statements.Sequence> 中的原始 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 活動。 若要執行這項操作，請將 `RegisterMetadata` 方法加入至 `MainWindow` 類別。  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         如需有關如何註冊活動設計工具的詳細資訊，請參閱[How to:建立自訂活動設計工具](how-to-create-a-custom-activity-designer.md)。  
  
    5. 在 `MainWindow` 類別建構函式中，將呼叫加入至先前宣告的方法，為中繼資料註冊設計工具支援，以建立 <xref:System.Activities.Presentation.WorkflowDesigner>。  
  
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
  
10. 請參閱[工作 3:建立工具箱與 PropertyGrid 窗格](task-3-create-the-toolbox-and-propertygrid-panes.md)以了解如何新增**工具箱**並**PropertyGrid**支援新增至您的重新裝載工作流程設計工具。  
  
## <a name="see-also"></a>另請參閱

- [重新裝載工作流程設計工具](rehosting-the-workflow-designer.md)
- [工作 1:建立新的 Windows Presentation Foundation 應用程式](task-1-create-a-new-wpf-app.md)
- [工作 3:建立工具箱與 PropertyGrid 窗格](task-3-create-the-toolbox-and-propertygrid-panes.md)
