---
title: 自訂複合設計工具 - 工作流程項目展示器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: f0a3616e6723d43ee4f2772c37e930c5facef31a
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48263959"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>自訂複合設計工具 - 工作流程項目展示器
<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> 是 WF 設計工具程式撰寫模型中的關鍵類型，允許編輯包含的項目集合。 這個範例示範如何建置會呈現這類可編輯集合的活動設計工具。

 這個範例會示範下列情況：

-   建立具有 <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> 的自訂活動設計工具。

-   使用 「 摺疊 」 和 「 展開 」 檢視中建立活動設計工具。

-   覆寫重新裝載應用程式中的預設設計工具。

### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1.  開啟**UsingWorkflowItemsPresenter.sln**適用於 C# 或 Visual Studio 2010 中的 VB 範例方案。

2.  建置並執行方案。 重新裝載的工作流程設計工具應用程式應該會開啟，您可以將活動拖曳至畫布上。

## <a name="sample-highlights"></a>範例重點
 這個範例的程式碼示範下列操作：

-   設計工具建置的目標活動：`Parallel`

-   建立具有 <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> 的自訂活動設計工具 請注意下列幾點事項：

    -   請注意繫結至 `ModelItem.Branches` 的 WPF 資料繫結用法。 `ModelItem` 是 `WorkflowElementDesigner` 上的屬性，它會參考設計工具的目標基礎物件，在這個範例中為 `Parallel`。

    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> 可用來放置視覺效果，在集合中的個別項目之間顯示。

    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> 是範本，可供判斷集合中的項目配置。 在這個範例中，會使用水平堆疊面板。

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

    -   接著覆寫 `RegisterCustomMetadata` 方法中的 parallel。

 下列 C# 和 Visual Basic 程式碼會示範這點。

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
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 [使用工作流程設計工具開發應用程式](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
