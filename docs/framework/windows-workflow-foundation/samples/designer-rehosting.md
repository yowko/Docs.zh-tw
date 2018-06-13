---
title: 設計工具重新裝載
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 3caff782dcb7ce2434960e24c4586877788da653
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516145"
---
# <a name="designer-rehosting"></a><span data-ttu-id="50a2d-102">設計工具重新裝載</span><span class="sxs-lookup"><span data-stu-id="50a2d-102">Designer ReHosting</span></span>
<span data-ttu-id="50a2d-103">設計工具重新裝載是在自訂應用程式中裝載工作流程設計畫布的一般案例。</span><span class="sxs-lookup"><span data-stu-id="50a2d-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="50a2d-104">大多數人熟悉的裝載應用程式是 Visual Studio，但在一些情況下，在應用程式中顯示工作流程設計工具可能很有用：</span><span class="sxs-lookup"><span data-stu-id="50a2d-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
-   <span data-ttu-id="50a2d-105">監視應用程式 (讓使用者視覺化處理序，以及有關處理序的執行階段資料，例如目前作用中狀態、彙總執行時間資料，或有關工作流程執行個體的其他資訊)。</span><span class="sxs-lookup"><span data-stu-id="50a2d-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
-   <span data-ttu-id="50a2d-106">讓使用者以有限活動集來自訂處理序的應用程式。</span><span class="sxs-lookup"><span data-stu-id="50a2d-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="50a2d-107">為了支援這些類型的應用程式，.NET Framework 隨附工作流程設計工具，該設計工具可裝載於 WPF 應用程式或具有適當 WPF 裝載程式碼的 WinForms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="50a2d-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="50a2d-108">這個範例會示範下列情況：</span><span class="sxs-lookup"><span data-stu-id="50a2d-108">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="50a2d-109">重新裝載 WF 設計工具。</span><span class="sxs-lookup"><span data-stu-id="50a2d-109">Rehosting the WF designer.</span></span>  
  
-   <span data-ttu-id="50a2d-110">使用重新裝載的工具箱以及屬性方格。</span><span class="sxs-lookup"><span data-stu-id="50a2d-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="50a2d-111">重新裝載設計工具</span><span class="sxs-lookup"><span data-stu-id="50a2d-111">Rehosting the designer</span></span>  
 <span data-ttu-id="50a2d-112">這個範例示範如何建立 WPF 配置以包含設計工具，如下列方格配置所示 (基於空間考量而省略工具箱程式碼)。</span><span class="sxs-lookup"><span data-stu-id="50a2d-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="50a2d-113">請注意包含設計工具和屬性方格之框線的命名。</span><span class="sxs-lookup"><span data-stu-id="50a2d-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 <span data-ttu-id="50a2d-114">範例接著建立設計工具，並且將其主要 <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> 和 <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> 與使用者介面中的適當容器產生關聯。</span><span class="sxs-lookup"><span data-stu-id="50a2d-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="50a2d-115">在下列範例中有些其他程式碼行需要說明。</span><span class="sxs-lookup"><span data-stu-id="50a2d-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="50a2d-116">若要針對 <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> 隨附的活動，與預設活動設計工具建立關聯，必須使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 呼叫。</span><span class="sxs-lookup"><span data-stu-id="50a2d-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="50a2d-117">會呼叫 <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> 以傳入所要編輯的 WF 項目。</span><span class="sxs-lookup"><span data-stu-id="50a2d-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="50a2d-118">最後，<xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (主要畫布) 和 <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (屬性方格) 會放在使用者介面上。</span><span class="sxs-lookup"><span data-stu-id="50a2d-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="50a2d-119">使用重新裝載的工具列</span><span class="sxs-lookup"><span data-stu-id="50a2d-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="50a2d-120">這個範例在 XAML 中以宣告方式使用重新裝載的工具箱控制項。</span><span class="sxs-lookup"><span data-stu-id="50a2d-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="50a2d-121">請注意，在程式碼中可將類型傳遞給 <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> 建構函式。</span><span class="sxs-lookup"><span data-stu-id="50a2d-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
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
            <sapt:ToolboxControl>  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="50a2d-122">使用範例</span><span class="sxs-lookup"><span data-stu-id="50a2d-122">Using the sample</span></span>  
  
1.  <span data-ttu-id="50a2d-123">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 DesignerRehosting.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="50a2d-123">Open the DesignerRehosting.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="50a2d-124">按 F5 編譯和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="50a2d-124">Press F5 to compile and run the application.</span></span>  
  
3.  <span data-ttu-id="50a2d-125">WPF 應用程式隨即以重新裝載的設計工具啟動。</span><span class="sxs-lookup"><span data-stu-id="50a2d-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="50a2d-126">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="50a2d-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="50a2d-127">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="50a2d-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="50a2d-128">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="50a2d-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="50a2d-129">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="50a2d-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`