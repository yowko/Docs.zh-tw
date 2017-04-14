---
title: "自訂複合設計工具 - 工作流程項目展示器 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 自訂複合設計工具 - 工作流程項目展示器
<xref:System.Activities.Design.WorkflowItemsPresenter> 是 WF 設計工具程式撰寫模型中的關鍵類型，允許編輯包含的項目集合。這個範例示範如何建置會呈現這類可編輯集合的活動設計工具。  
  
 這個範例會示範下列情況：  
  
-   建立具有 <xref:System.Activities.Design.WorkflowItemsPresenter> 的自訂活動設計工具。  
  
-   建立具有「折疊」和「展開」檢視的活動設計工具。  
  
-   覆寫重新裝載應用程式中的預設設計工具。  
  
### 若要安裝、建立及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟適用於 C\# 或 VB 的 **UsingWorkflowItemsPresenter.sln** 範例方案。  
  
2.  建立和執行方案。重新裝載的工作流程設計工具應用程式應該會開啟，您可以將活動拖曳至畫布上。  
  
## 範例重點  
 這個範例的程式碼示範下列操作：  
  
-   設計工具建置的目標活動：`Parallel`  
  
-   建立具有 <xref:System.Activities.Design.WorkflowItemsPresenter> 的自訂活動設計工具請注意下列幾點事項：  
  
    -   請注意繫結至 `ModelItem.Branches` 的 WPF 資料繫結用法。`ModelItem` 是 <xref:System.Activities.Design.WorkflowElementDesigner> 上的屬性，它會參考設計工具的目標基礎物件，在這個範例中為 `Parallel`。  
  
    -   <xref:System.Activities.Design.WorkflowItemsPresenter.SpacerTemplate%2A> 可用來放置視覺效果，在集合中的個別項目之間顯示。  
  
    -   <xref:System.Activities.Design.WorkflowItemsPresenter.ItemsPanel%2A> 是範本，可供判斷集合中的項目配置。在這個範例中，會使用水平堆疊面板。  
  
 下列範例程式碼會示範這點。  
  
```xaml  
<sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                              Items="{Binding Path=ModelItem.Branches}">  
    <sad:WorkflowItemsPresenter.SpacerTemplate>  
      <DataTemplate>  
        <Ellipse Width="10" Height="10" Fill="Black"/>  
      </DataTemplate>  
    </sad:WorkflowItemsPresenter.SpacerTemplate>  
    <sad:WorkflowItemsPresenter.ItemsPanel>  
      <ItemsPanelTemplate>  
        <StackPanel Orientation="Horizontal"/>  
      </ItemsPanelTemplate>  
    </sad:WorkflowItemsPresenter.ItemsPanel>  
  </sad:WorkflowItemsPresenter>  
  
```  
  
-   執行 `DesignerAttribute` 與 `Parallel` 類型的關聯，然後輸出回報的屬性。  
  
    -   首先，註冊所有預設設計工具。  
  
 以下是程式碼範例。  
  
```csharp  
// register metadata  
(new DesignerMetadata()).Register();  
RegisterCustomMetadata();  
  
```  
  
```vb  
' register metadata  
Dim metadata = New DesignerMetadata()  
metadata.Register()  
' register custom metadata  
RegisterCustomMetadata()  
  
```  
  
-   -   接著覆寫 `RegisterCustomMetadata` 方法中的 parallel。  
  
 下列 C\# 和 Visual Basic 程式碼會示範這點。  
  
 C\#  
  
```csharp  
void RegisterCustomMetadata()  
{  
      AttributeTableBuilder builder = new AttributeTableBuilder();  
      builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
      MetadataStore.AddAttributeTable(builder.CreateTable());  
}  
  
```  
  
```vb  
Sub RegisterCustomMetadata()  
   Dim builder As New AttributeTableBuilder()  
   builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))  
   MetadataStore.AddAttributeTable(builder.CreateTable())  
End Sub  
  
```  
  
-   最後，請注意不同資料範本和觸發程序根據 `IsRootDesigner` 屬性來選取適當範本的用法。  
  
 以下是程式碼範例。  
  
```xaml  
<sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"  
    xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">  
  <sad:ActivityDesigner.Resources>  
    <DataTemplate x:Key="Expanded">  
      <StackPanel>  
        <TextBlock>This is the Expanded View</TextBlock>  
        <sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                    Items="{Binding Path=ModelItem.Branches}">  
          <sad:WorkflowItemsPresenter.SpacerTemplate>  
            <DataTemplate>  
              <Ellipse Width="10" Height="10" Fill="Black"/>  
            </DataTemplate>  
          </sad:WorkflowItemsPresenter.SpacerTemplate>  
          <sad:WorkflowItemsPresenter.ItemsPanel>  
            <ItemsPanelTemplate>  
              <StackPanel Orientation="Horizontal"/>  
            </ItemsPanelTemplate>  
          </sad:WorkflowItemsPresenter.ItemsPanel>  
        </sad:WorkflowItemsPresenter>  
      </StackPanel>  
    </DataTemplate>  
    <DataTemplate x:Key="Collapsed">  
      <TextBlock>This is the Collapsed View</TextBlock>  
    </DataTemplate>  
    <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
      <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
      <Style.Triggers>  
        <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">  
          <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
        </DataTrigger>  
      </Style.Triggers>  
    </Style>  
  </sad: ActivityDesigner.Resources>  
  <Grid>  
    <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
  </Grid>  
</sad: ActivityDesigner>  
  
```  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## 請參閱  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>   
 [使用工作流程設計工具開發應用程式](../Topic/Developing%20Applications%20with%20the%20Workflow%20Designer.md)