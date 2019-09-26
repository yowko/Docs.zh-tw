---
title: HOW TO：建立自訂活動設計工具
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 3c326508744f2aa2b34f5ee574cc9ec1e2863cf6
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306350"
---
# <a name="how-to-create-a-custom-activity-designer"></a>HOW TO：建立自訂活動設計工具

通常實作自訂活動設計工具的方式，是讓其相關聯活動能夠透過其他活動組合，這些活動的設計工具能夠隨著活動放到設計介面上。 這項功能需要自訂活動設計工具提供可放置任意活動的「卸載區」，以及在設計介面上管理專案所產生之集合的方法。 本主題說明如何建立包含這種卸除區的自訂活動設計工具，以及如何建立能夠提供管理設計工具項目集合所需之編輯功能的自訂活動設計工具。

自訂活動設計工具通常繼承自 <xref:System.Activities.Presentation.ActivityDesigner>，它是任何沒有特定設計工具之活動的預設基底活動設計工具型別。 這個型別提供與屬性方格互動及設定管理色彩和圖示等基本層面等的設計階段經驗。

<xref:System.Activities.Presentation.ActivityDesigner> 會使用兩項 Helper 控制項 (<xref:System.Activities.Presentation.WorkflowItemPresenter> 和 <xref:System.Activities.Presentation.WorkflowItemsPresenter>) 來簡化自訂活動設計工具的開發。 這些 Helper 能夠處理拖放子項目、刪除、選取及加入子項目之類的常見功能。 允許內的單一子 UI 專案（提供「卸載區」）， <xref:System.Activities.Presentation.WorkflowItemsPresenter>而可提供支援多個 UI 元素，包括排序、移動、刪除和加入子專案等其他功能。 <xref:System.Activities.Presentation.WorkflowItemPresenter>

在自訂活動設計工具的執行中，需要反白顯示的另一個重要部分，就是使用 WPF 資料系結，將視覺編輯系結至儲存在設計工具中所編輯之記憶體的實例。 這項操作可透過模型項目樹狀完成，該樹狀也負責進行變更通知，以及追蹤如狀態變更這類事件。

本主題將說明兩種程序。

1. 第一種程序描述如何使用提供接收其他活動之卸除區的 <xref:System.Activities.Presentation.WorkflowItemPresenter> 建立自訂活動設計工具。 此程式是以[自訂複合設計工具-工作流程專案展示者](./samples/custom-composite-designers-workflow-item-presenter.md)範例為基礎。

2. 第二種程序描述如何使用提供編輯所包含項目集合時需要之功能的 <xref:System.Activities.Presentation.WorkflowItemsPresenter> 建立自訂活動設計工具。 此程式是以[自訂複合設計工具-工作流程專案展示者](./samples/custom-composite-designers-workflow-items-presenter.md)範例為基礎。

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>若要使用 WorkflowItemPresenter 建立含有卸除區的自訂活動設計工具

1. 啟動 Visual Studio 2010。

2. **在 [檔案**] 功能表上，指向 [**新增**]，然後選取 [**專案**]。

     [ **新增專案** ] 對話方塊隨即開啟。

3. 在 [**已安裝的範本**] 窗格中，從您慣用的語言類別中選取 [ **Windows** ]。

4. 在 [**範本**] 窗格中，選取 [ **WPF 應用程式**]。

5. 在 [**名稱**] 方塊中`UsingWorkflowItemPresenter`，輸入。

6. 在 [**位置**] 方塊中，輸入您要儲存專案的目錄，或按一下 **[流覽]** 以流覽至它。

7. 在 [**方案**] 方塊中，接受預設值。

8. 按一下 [確定]。

9. 以滑鼠右鍵按一下**方案總管**中的*mainwindows.xaml* ，在 [ **Microsoft Visual Studio** ] 對話方塊中選取 [**刪除**]，然後確認 **[確定]** 。

10. 以滑鼠右鍵按一下**方案總管**中的 UsingWorkflowItemPresenter 專案，然後依序選取 [**加入**] 和 [**新增專案**]。 以顯示 [**新增專案**] 對話方塊，然後從左側的 [**已安裝的範本**] 區段中選取 [ **WPF** ] 分類。

11. 選取**視窗（WPF）** 範本，將它`RehostingWFDesigner`命名為，然後按一下 [**新增**]。

12. 開啟*rehostingwfdesigner.xaml* ，並將下列程式碼貼入其中，以定義應用程式的 UI：

    ```xaml
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"
            xmlns:sys="clr-namespace:System;assembly=mscorlib"
            Title="Window1" Height="600" Width="900">
        <Window.Resources>
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>
        </Window.Resources>
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="2*"/>
                <ColumnDefinition Width="7*"/>
                <ColumnDefinition Width="3*"/>
            </Grid.ColumnDefinitions>
            <Border Grid.Column="0">
                <sapt:ToolboxControl Name="Toolbox">
                    <sapt:ToolboxCategory CategoryName="Basic">
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.Sequence
                            </sapt:ToolboxItemWrapper.ToolName>
                           </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.WriteLine
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.If
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.While
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                    </sapt:ToolboxCategory>
                </sapt:ToolboxControl>
            </Border>
            <Border Grid.Column="1" Name="DesignerBorder"/>
            <Border Grid.Column="2" Name="PropertyBorder"/>
        </Grid>
    </Window>
    ```

13. 若要關聯活動設計工具與活動型別，您必須在中繼資料存放區中註冊該活動設計工具。 若要執行這項操作，請將 `RegisterMetadata` 方法加入至 `RehostingWFDesigner` 類別。 在 `RegisterMetadata` 方法的範圍內，建立 <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> 物件，然後呼叫 <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> 方法以便加入屬性。 呼叫 <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> 方法，將 <xref:System.Activities.Presentation.Metadata.AttributeTable> 加入至中繼資料存放區。 下列程式碼包含設計工具的重新裝載邏輯。 它會註冊中繼資料，將 `SimpleNativeActivity` 放入工具箱，然後建立工作流程。 將此程式碼放入*RehostingWFDesigner.xaml.cs*檔案中。

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Presentation.Toolbox;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespace UsingWorkflowItemPresenter
    {
        // Interaction logic for RehostingWFDesigner.xaml
        public partial class RehostingWFDesigner
        {
            public RehostingWFDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. 以滑鼠右鍵按一下方案總管中的 [參考] 目錄，然後選取 [**新增參考 ...** ]。 以顯示 [**加入參考**] 對話方塊。

15. 按一下 [ **.net** ] 索引標籤，找出名為 [System.string **. Presentation**] 的元件，選取它並按一下 **[確定]** 。

16. 使用相同的程序將參考加入至下列組件：

    1. System.Data.DataSetExtensions.dll

    2. System.Activities.Presentation.dll

    3. System.ServiceModel.Activities.dll

17. 開啟*app.xaml*檔案，然後將 StartUpUri 的值變更為 "rehostingwfdesigner.xaml"。

18. 以滑鼠右鍵按一下**方案總管**中的 UsingWorkflowItemPresenter 專案，然後依序選取 [**加入**] 和 [**新增專案**]。 若要顯示 [**新增專案**] 對話方塊，並選取左側的 [**已安裝的範本**] 區段中的 [**工作流程**] 類別。

19. 選取 [**活動設計**工具] 範本， `SimpleNativeDesigner`將它命名為，然後按一下 [**新增**]。

20. 開啟*SimpleNativeDesigner* ，並將下列程式碼貼入其中。 請注意，這個程式碼會使用 <xref:System.Activities.Presentation.ActivityDesigner> 做為根項目，並且示範如何使用繫結將 <xref:System.Activities.Presentation.WorkflowItemPresenter> 整合至設計工具中，以便在複合活動設計工具中顯示子型別。

    > [!NOTE]
    > <xref:System.Activities.Presentation.ActivityDesigner> 的結構描述允許只將一個子項目加入自訂活動設計工具定義中，不過，這個項目可以是 `StackPanel`、`Grid`，也可以是其他複合 UI 項目。

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <StackPanel>
                    <TextBlock>This is the collapsed view</TextBlock>
                </StackPanel>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock>Custom Text</TextBlock>
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                            HintText="Please drop an activity here" />
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
        </Grid>
    </sap:ActivityDesigner>
    ```

21. 以滑鼠右鍵按一下**方案總管**中的 UsingWorkflowItemPresenter 專案，然後依序選取 [**加入**] 和 [**新增專案**]。 若要顯示 [**新增專案**] 對話方塊，並選取左側的 [**已安裝的範本**] 區段中的 [**工作流程**] 類別。

22. 選取 [ **Code] 活動**範本，將`SimpleNativeActivity`它命名為，然後按一下 [**新增**]。

23. 在*SimpleNativeActivity.cs*檔案中輸入下列程式碼，以執行類別：`SimpleNativeActivity`

    ```csharp
    using System.Activities;

    namespace UsingWorkflowItemPresenter
    {
        public sealed class SimpleNativeActivity : NativeActivity
        {
            // this property contains an activity that will be scheduled in the execute method
            // the WorkflowItemPresenter in the designer is bound to this to enable editing
            // of the value
            public Activity Body { get; set; }

            protected override void CacheMetadata(NativeActivityMetadata metadata)
            {
               metadata.AddChild(Body);
               base.CacheMetadata(metadata);

            }

            protected override void Execute(NativeActivityContext context)
            {
                context.ScheduleActivity(Body);
            }
        }
    }
    ```

24. 從 [**建立**] 功能表中選取 [**建立方案**]。

25. 從 [**調試**] 功能表中選取 [**啟動但不進行調試**]，以開啟 [重新裝載自訂設計] 視窗。

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>若要使用 WorkflowItemsPresenter 建立自訂活動設計工具

1. 第二個自訂活動設計工具的程式是第一個只有一些修改，第一個則是為第二個應用程式`UsingWorkflowItemsPresenter`命名。 此外，這個應用程式不會定義新的自訂活動。

2. 主要差異包含在*CustomParallelDesigner*和*RehostingWFDesigner.xaml.cs*檔案中。 以下是*CustomParallelDesigner*檔案中定義 UI 的程式碼：

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <TextBlock>This is the Collapsed View</TextBlock>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"
                                        Items="{Binding Path=ModelItem.Branches}">
                        <sap:WorkflowItemsPresenter.SpacerTemplate>
                            <DataTemplate>
                                <Ellipse Width="10" Height="10" Fill="Black"/>
                            </DataTemplate>
                        </sap:WorkflowItemsPresenter.SpacerTemplate>
                        <sap:WorkflowItemsPresenter.ItemsPanel>
                            <ItemsPanelTemplate>
                                <StackPanel Orientation="Horizontal"/>
                            </ItemsPanelTemplate>
                        </sap:WorkflowItemsPresenter.ItemsPanel>
                    </sap:WorkflowItemsPresenter>
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
        </Grid>
    </sap:ActivityDesigner>
    ```

3. 以下是*RehostingWFDesigner.xaml.cs*檔案中提供重新裝載邏輯的程式碼：

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespaceUsingWorkflowItemsPresenter
    {
        public partial class RehostingWfDesigner : Window
        {
            public RehostingWfDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [自訂工作流程設計體驗](customizing-the-workflow-design-experience.md)
