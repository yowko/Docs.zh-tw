---
title: "自訂複合設計工具 - 工作流程項目展示器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bba89e9da78fd96d0cd7d61e825e4792729bae5b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="da769-102">自訂複合設計工具 - 工作流程項目展示器</span><span class="sxs-lookup"><span data-stu-id="da769-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="da769-103"><xref:System.Activities.Presentation.WorkflowItemPresenter>可允許的 「 卸除區 」 可以放置任意活動建立 WF 設計工具程式設計模型中的關鍵類型。</span><span class="sxs-lookup"><span data-stu-id="da769-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="da769-104">這個範例示範如何建置會呈現這類 「 卸除區。 」 的活動設計工具</span><span class="sxs-lookup"><span data-stu-id="da769-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>  
  
 <span data-ttu-id="da769-105">這個範例會示範下列情況：</span><span class="sxs-lookup"><span data-stu-id="da769-105">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="da769-106">示範</span><span class="sxs-lookup"><span data-stu-id="da769-106">Demonstrates</span></span>  
  
-   <span data-ttu-id="da769-107">建立具有 <xref:System.Activities.Presentation.WorkflowItemPresenter> 的自訂活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="da769-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
-   <span data-ttu-id="da769-108">使用中繼資料存放區登錄自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="da769-108">Registering the custom designer using the metadata store.</span></span>  
  
-   <span data-ttu-id="da769-109">以宣告和強制方式設計重新裝載之工具箱的程式。</span><span class="sxs-lookup"><span data-stu-id="da769-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="da769-110">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="da769-110">Sample Details</span></span>  
 <span data-ttu-id="da769-111">這個範例的程式碼會示範：</span><span class="sxs-lookup"><span data-stu-id="da769-111">The code for this sample shows:</span></span>  
  
-   <span data-ttu-id="da769-112">針對 `SimpleNativeActivity` 類別建置自訂活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="da769-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>  
  
-   <span data-ttu-id="da769-113">建立具有 <xref:System.Activities.Presentation.WorkflowItemPresenter> 的自訂活動設計工具</span><span class="sxs-lookup"><span data-stu-id="da769-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
```xaml  
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"  
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
  
 <span data-ttu-id="da769-114">請注意繫結至 `ModelItem.Body` 的 WPF 資料繫結用法。</span><span class="sxs-lookup"><span data-stu-id="da769-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="da769-115">`ModelItem`位於屬性<xref:System.Activities.Presentation.ActivityDesigner>基礎物件在設計工具使用，在此情況下，它會參考**SimpleNativeActivity**。</span><span class="sxs-lookup"><span data-stu-id="da769-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>  
  
#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="da769-116">若要設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="da769-116">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="da769-117">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="da769-117">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="da769-118">按 F5 編譯和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="da769-118">Press F5 to compile and run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da769-119">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="da769-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="da769-120">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="da769-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="da769-121">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="da769-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="da769-122">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="da769-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="da769-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da769-123">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [<span data-ttu-id="da769-124">使用工作流程設計工具開發應用程式</span><span class="sxs-lookup"><span data-stu-id="da769-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
