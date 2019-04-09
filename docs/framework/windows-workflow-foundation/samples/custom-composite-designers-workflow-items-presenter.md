---
title: 自訂複合設計工具 - 工作流程項目展示器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: f4db3325081a820a37a8791849d2ad9697d15151
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118101"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="a7705-102">自訂複合設計工具 - 工作流程項目展示器</span><span class="sxs-lookup"><span data-stu-id="a7705-102">Custom Composite Designers - Workflow Items Presenter</span></span>
<span data-ttu-id="a7705-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> 是 WF 設計工具程式撰寫模型中的關鍵類型，允許編輯包含的項目集合。</span><span class="sxs-lookup"><span data-stu-id="a7705-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="a7705-104">這個範例示範如何建置會呈現這類可編輯集合的活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="a7705-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

 <span data-ttu-id="a7705-105">這個範例會示範下列情況：</span><span class="sxs-lookup"><span data-stu-id="a7705-105">This sample demonstrates:</span></span>

-   <span data-ttu-id="a7705-106">建立具有 <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> 的自訂活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="a7705-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

-   <span data-ttu-id="a7705-107">使用 「 摺疊 」 和 「 展開 」 檢視中建立活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="a7705-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

-   <span data-ttu-id="a7705-108">覆寫重新裝載應用程式中的預設設計工具。</span><span class="sxs-lookup"><span data-stu-id="a7705-108">Overriding a default designer in a rehosted application.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a7705-109">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="a7705-109">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="a7705-110">開啟**UsingWorkflowItemsPresenter.sln**適用於 C# 或 Visual Studio 2010 中的 VB 範例方案。</span><span class="sxs-lookup"><span data-stu-id="a7705-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in Visual Studio 2010.</span></span>

2.  <span data-ttu-id="a7705-111">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="a7705-111">Build and run the solution.</span></span> <span data-ttu-id="a7705-112">重新裝載的工作流程設計工具應用程式應該會開啟，您可以將活動拖曳至畫布上。</span><span class="sxs-lookup"><span data-stu-id="a7705-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="a7705-113">範例重點</span><span class="sxs-lookup"><span data-stu-id="a7705-113">Sample Highlights</span></span>
 <span data-ttu-id="a7705-114">這個範例的程式碼示範下列操作：</span><span class="sxs-lookup"><span data-stu-id="a7705-114">The code for this sample shows the following:</span></span>

-   <span data-ttu-id="a7705-115">活動設計工具建置的：</span><span class="sxs-lookup"><span data-stu-id="a7705-115">The activity a designer is built for:</span></span>  `Parallel`

-   <span data-ttu-id="a7705-116">建立具有 <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> 的自訂活動設計工具</span><span class="sxs-lookup"><span data-stu-id="a7705-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a7705-117">請注意下列幾點事項：</span><span class="sxs-lookup"><span data-stu-id="a7705-117">A few things to point out:</span></span>

    -   <span data-ttu-id="a7705-118">請注意繫結至 `ModelItem.Branches` 的 WPF 資料繫結用法。</span><span class="sxs-lookup"><span data-stu-id="a7705-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> `ModelItem` <span data-ttu-id="a7705-119">屬性位於`WorkflowElementDesigner`設計工具使用，在此情況下，基礎物件，參考我們`Parallel`。</span><span class="sxs-lookup"><span data-stu-id="a7705-119">is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

    -   <span data-ttu-id="a7705-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> 可用來放置視覺效果，在集合中的個別項目之間顯示。</span><span class="sxs-lookup"><span data-stu-id="a7705-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> <span data-ttu-id="a7705-121">是可供判斷集合中的項目配置的範本。</span><span class="sxs-lookup"><span data-stu-id="a7705-121">is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="a7705-122">在這個範例中，會使用水平堆疊面板。</span><span class="sxs-lookup"><span data-stu-id="a7705-122">In this case, a horizontal stack panel is used.</span></span>

 <span data-ttu-id="a7705-123">下列範例程式碼會示範這點。</span><span class="sxs-lookup"><span data-stu-id="a7705-123">This following example code shows this.</span></span>

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

-   <span data-ttu-id="a7705-124">執行 `DesignerAttribute` 與 `Parallel` 類型的關聯，然後輸出回報的屬性。</span><span class="sxs-lookup"><span data-stu-id="a7705-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

    -   <span data-ttu-id="a7705-125">首先，註冊所有預設設計工具。</span><span class="sxs-lookup"><span data-stu-id="a7705-125">First, register all of the default designers.</span></span>

 <span data-ttu-id="a7705-126">以下是程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="a7705-126">The following is the code example.</span></span>

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

    -   <span data-ttu-id="a7705-127">接著覆寫 `RegisterCustomMetadata` 方法中的 parallel。</span><span class="sxs-lookup"><span data-stu-id="a7705-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

 <span data-ttu-id="a7705-128">下列 C# 和 Visual Basic 程式碼會示範這點。</span><span class="sxs-lookup"><span data-stu-id="a7705-128">The following code shows this in C# and Visual Basic.</span></span>

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

-   <span data-ttu-id="a7705-129">最後，請注意不同資料範本和觸發程序根據 `IsRootDesigner` 屬性來選取適當範本的用法。</span><span class="sxs-lookup"><span data-stu-id="a7705-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

 <span data-ttu-id="a7705-130">以下是程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="a7705-130">The following is the code example.</span></span>

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
>  <span data-ttu-id="a7705-131">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a7705-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a7705-132">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a7705-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a7705-133">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="a7705-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7705-134">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a7705-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="a7705-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7705-135">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="a7705-136">使用工作流程設計工具開發應用程式</span><span class="sxs-lookup"><span data-stu-id="a7705-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
