---
title: 工作 2：裝載工作流程設計工具
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 92c5fa347cc7a2c0088ab8f4fbdfddf25ffb83c1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037862"
---
# <a name="task-2-host-the-workflow-designer"></a>工作 2：裝載工作流程設計工具

本主題描述[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]在 Windows Presentation Foundation (WPF) 應用程式中裝載實例的程式。

此程式會設定包含設計工具的**方格**控制項, 以程式設計方式建立包含<xref:System.Activities.Presentation.WorkflowDesigner>預設<xref:System.Activities.Statements.Sequence>活動的實例, 註冊設計工具中繼資料以提供所有的設計工具支援內建活動, 並裝載 WPF 應用[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]程式中的。

### <a name="to-host-the-workflow-designer"></a>若要裝載工作流程設計工具

1. 開啟您在工作1中[建立的 HostingApplication 專案:建立新的 Windows Presentation Foundation 應用](task-1-create-a-new-wpf-app.md)程式。

2. 將視窗調整至方便使用 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 的大小。 若要這麼做, 請在設計工具中選取 [ **mainwindow.xaml** ], 按 F4 顯示 [**屬性**] 視窗 , 然後在 [配置] 區段中, 將 [**寬度**] 設定為 600, 並將 [**高度**] 設為 [350] 的值。

3. 選取設計工具中的 [**方格**] 面板 (按一下**mainwindow.xaml**內的方塊), 然後將 [**屬性**] 視窗頂端的 [**名稱**] 屬性設定為 "grid1", 以設定格線名稱。

4. 在 [**屬性**] 視窗中, 按一下`ColumnDefinitions`屬性旁邊的省略號 ( **...** ), 以開啟 [**集合編輯器**] 對話方塊。

5. 在 [**集合編輯器**] 對話方塊中, 按一下 [**加入**] 按鈕三次, 將三個數據行插入配置中。 第一個資料行會包含 [**工具箱**], 第二個數據行會[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]裝載, 而第三個數據行則用於屬性偵測器。

6. 將中間資料行的屬性設為"4*"值。`Width`

7. 按一下 [確定] 儲存變更。 以下的 XAML 已加入至您的 MainWindow.xaml 檔案：

    ```xml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. 在**方案總管**中, 以滑鼠右鍵按一下 mainwindow.xaml, 然後選取 [ **View Code**]。 遵循下列步驟修改程式碼：

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

    3. 將下列 `AddDesigner` 方法加入至 `MainWindow` 類別。 此執行會建立的實例<xref:System.Activities.Presentation.WorkflowDesigner>, 並在其中<xref:System.Activities.Statements.Sequence>加入活動, 並將其放在 grid1**方格**的中間資料行中。

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

        如需註冊活動設計工具的詳細資訊[, 請參閱如何:建立自訂活動設計](how-to-create-a-custom-activity-designer.md)工具。

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
        > `RegisterMetadata` 方法會註冊內建活動 (包括 <xref:System.Activities.Statements.Sequence> 活動) 的設計工具中繼資料。 由於 `AddDesigner` 方法會使用 <xref:System.Activities.Statements.Sequence> 活動，因此必須先呼叫 `RegisterMetadata` 方法。

9. 按 F5 以建置及執行方案。

10. 請[參閱工作 3:建立 [工具箱] 和 [](task-3-create-the-toolbox-and-propertygrid-panes.md) PropertyGrid] 窗格, 以瞭解如何在重新裝載工作流程設計工具中加入 [**工具箱**] 和 [ **PropertyGrid** ] 支援。

## <a name="see-also"></a>另請參閱

- [重新裝載工作流程設計工具](rehosting-the-workflow-designer.md)
- [工作 1:建立新的 Windows Presentation Foundation 應用程式](task-1-create-a-new-wpf-app.md)
- [工作 3:建立 [工具箱] 和 [PropertyGrid] 窗格](task-3-create-the-toolbox-and-propertygrid-panes.md)
