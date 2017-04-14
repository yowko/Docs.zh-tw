---
title: "HOW TO：建立自訂活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# HOW TO：建立自訂活動設計工具
通常實作自訂活動設計工具的方式，是讓其相關聯活動能夠透過其他活動組合，這些活動的設計工具能夠隨著活動放到設計介面上。這項功能需要自訂活動設計工具提供可放置任意活動的「卸除區」，以及管理設計介面上所產生項目集合的方法。本主題說明如何建立包含這種卸除區的自訂活動設計工具，以及如何建立能夠提供管理設計工具項目集合所需之編輯功能的自訂活動設計工具。  
  
 自訂活動設計工具通常繼承自 <xref:System.Activities.Presentation.ActivityDesigner>，它是任何沒有特定設計工具之活動的預設基底活動設計工具型別。這個型別提供與屬性方格互動及設定管理色彩和圖示等基本層面等的設計階段經驗。  
  
 <xref:System.Activities.Presentation.ActivityDesigner> 會使用兩項 Helper 控制項 \(<xref:System.Activities.Presentation.WorkflowItemPresenter> 和 <xref:System.Activities.Presentation.WorkflowItemsPresenter>\) 來簡化自訂活動設計工具的開發。這些 Helper 能夠處理拖放子項目、刪除、選取及加入子項目之類的常見功能。<xref:System.Activities.Presentation.WorkflowItemPresenter> 允許內含單一子 UI 項目 \(假設為「卸除區」\)，而 <xref:System.Activities.Presentation.WorkflowItemsPresenter> 可提供支援多個 UI 項目，包括排列順序、移動、刪除和加入子項目這類額外的功能。  
  
 其他需要在實作自訂活動設計工具中強調的重要部分，是有關如何使用 [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] 資料繫結將視覺化編輯繫結至設計工具中所編輯內容的記憶體內儲存的執行個體。這項操作可透過模型項目樹狀結構完成，該樹狀結構也負責進行變更通知，以及追蹤如狀態變更這類事件。  
  
 本主題將說明兩種程序。  
  
1.  第一種程序描述如何使用提供接收其他活動之卸除區的 <xref:System.Activities.Presentation.WorkflowItemPresenter> 建立自訂活動設計工具。這個程序是以 [自訂複合設計工具 \- 工作流程項目展示器](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) 範例為基礎。  
  
2.  第二種程序描述如何使用提供編輯所包含項目集合時需要之功能的 <xref:System.Activities.Presentation.WorkflowItemsPresenter> 建立自訂活動設計工具。這個程序是以 [自訂複合設計工具 \- 工作流程項目展示器](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) 範例為基礎。  
  
### 若要使用 WorkflowItemPresenter 建立含有卸除區的自訂活動設計工具  
  
1.  啟動 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。  
  
2.  在 \[**檔案**\] 功能表中，指向 \[**開新檔案**\]，再選取 \[**專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
3.  在 \[**已安裝的範本**\] 窗格中，從偏好的語言分類選取 \[**Windows**\]。  
  
4.  在 \[**範本**\] 窗格中，選取 \[**WPF 應用程式**\]。  
  
5.  在 \[**名稱**\] 方塊中輸入 `UsingWorkflowItemPresenter`。  
  
6.  在 \[**位置**\] 方塊中，輸入要儲存專案的目錄，或按一下 \[**瀏覽**\] 巡覽至該目錄。  
  
7.  在 \[**方案**\] 方塊中，接受預設值。  
  
8.  按一下 \[**確定**\]。  
  
9. 以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[MainWindows.xaml\] 檔案，然後選取 \[**刪除**\]，並確認 \[**Microsoft Visual Studio**\] 對話方塊中的 \[**確定**\]。  
  
10. 在 \[**方案總管**\] 中以滑鼠右鍵按一下 UsingWorkflowItemPresenter 專案，依序選取 \[**加入**\] 和 \[**新增項目**\] 以顯示 \[**加入新項目**\] 對話方塊，然後從左側的 \[**已安裝的範本**\] 區段選取 \[**WPF**\] 分類。  
  
11. 選取 \[**視窗 \(WPF\)**\] 範本，將它命名為 `RehostingWFDesigner`，然後按一下 \[**加入**\]。  
  
12. 開啟 RehostingWFDesigner 檔案，將下面的程式碼貼入其中，以定義應用程式的 UI。  
  
    ```  
  
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
  
13. 若要關聯活動設計工具與活動型別，您必須在中繼資料存放區中註冊該活動設計工具。若要執行這項操作，請將 `RegisterMetadata` 方法加入至 `RehostingWFDesigner` 類別。在 `RegisterMetadata` 方法的範圍內，建立 <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> 物件，然後呼叫 <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> 方法以便加入屬性。呼叫 <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> 方法，將 <xref:System.Activities.Presentation.Metadata.AttributeTable> 加入至中繼資料存放區。下列程式碼包含設計工具的重新裝載邏輯。它會註冊中繼資料，將 `SimpleNativeActivity` 放入工具箱，然後建立工作流程。將這個程式碼放入 RehostingWFDesigner.xaml.cs 檔案中。  
  
    ```  
  
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
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
                // add custom activity to toolbox  
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));  
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
  
    ```  
  
14. 以滑鼠右鍵按一下 \[方案總管\] 中的 \[References\] 目錄，並選取 \[**加入參考**\] 以顯示 \[**加入參考**\] 對話方塊。  
  
15. 按一下 **.NET** 索引標籤，找出名為 **System.Activities.Core.Presentation** 的組件，然後選取該組件並按一下 \[**確定**\]。  
  
16. 使用相同的程序將參考加入至下列組件：  
  
    1.  System.Data.DataSetExtensions.dll  
  
    2.  System.Activities.Presentation.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
17. 開啟 \[App.xaml\] 檔案，並且將 StartUpUri 的值變更為 "RehostingWFDesigner.xaml"。  
  
18. 在 \[**方案總管**\] 中以滑鼠右鍵按一下 UsingWorkflowItemPresenter 專案，依序選取 \[**加入**\] 和 \[**新增項目**\] 以顯示 \[**加入新項目**\] 對話方塊，然後從左側的 \[**已安裝的範本**\] 區段選取 \[**工作流程**\] 分類。  
  
19. 選取 \[**活動設計工具**\] 範本，將它命名為 `SimpleNativeDesigner`，然後按一下 \[**加入**\]。  
  
20. 開啟 \[SimpleNativeDesigner.xaml\] 檔案，並將下列程式碼貼入其中。請注意，這個程式碼會使用 <xref:System.Activities.Presentation.ActivityDesigner> 做為根項目，並且示範如何使用繫結將 <xref:System.Activities.Presentation.WorkflowItemPresenter> 整合至設計工具中，以便在複合活動設計工具中顯示子型別。  
  
    > [!NOTE]
    >  <xref:System.Activities.Presentation.ActivityDesigner> 的結構描述允許只將一個子項目加入自訂活動設計工具定義中，不過，這個項目可以是 `StackPanel`、`Grid`，也可以是其他複合 UI 項目。  
  
    ```  
  
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
  
21. 在 \[**方案總管**\] 中以滑鼠右鍵按一下 UsingWorkflowItemPresenter 專案，依序選取 \[**加入**\] 和 \[**新增項目**\] 以顯示 \[**加入新項目**\] 對話方塊，然後從左側的 \[**已安裝的範本**\] 區段選取 \[**工作流程**\] 分類。  
  
22. 選取 \[**程式碼活動**\] 範本，將它命名為 `SimpleNativeActivity`，然後按一下 \[**加入**\]。  
  
23. 將下列程式碼輸入 SimpleNativeActivity.cs 檔案中，以實作 `SimpleNativeActivity` 類別。  
  
    ```  
  
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
  
24. 從 \[**建置**\] 功能表選取 \[**建置方案**\]。  
  
25. 從 \[**偵錯**\] 功能表選取 \[**啟動但不偵錯**\]，開啟重新裝載的自訂設計視窗。  
  
### 若要使用 WorkflowItemsPresenter 建立自訂活動設計工具  
  
1.  第二種自訂活動設計工具的程序與第一種幾乎相同，但有幾處修改：首先是將第二個應用程式命名為 `UsingWorkflowItemsPresenter`。此外，這個應用程式不會定義新的自訂活動。  
  
2.  主要的差異包含在 CustomParallelDesigner.xaml 和 RehostingWFDesigner.xaml.cs 檔案中。以下為 CustomParallelDesigne.xaml 檔案中定義 UI 的程式碼。  
  
    ```  
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
  
3.  以下為 RehostingWFDesigner.xaml.cs 檔案中提供重新裝載邏輯的程式碼。  
  
    ```  
  
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
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
## 請參閱  
 <xref:System.Activities.Presentation.ActivityDesigner>   
 <xref:System.Activities.Presentation.WorkflowItemPresenter>   
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>   
 <xref:System.Activities.Presentation.WorkflowViewElement>   
 <xref:System.Activities.Presentation.Model.ModelItem>   
 [自訂工作流程設計經驗](../../../docs/framework/windows-workflow-foundation//customizing-the-workflow-design-experience.md)