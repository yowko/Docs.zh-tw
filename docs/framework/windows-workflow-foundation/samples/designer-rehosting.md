---
title: "設計工具重新裝載"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed270aeba08dfaf67e376b9116d5f8572b3c11b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="designer-rehosting"></a>設計工具重新裝載
設計工具重新裝載是在自訂應用程式中裝載工作流程設計畫布的一般案例。 大多數人熟悉的裝載應用程式是 Visual Studio，但在一些情況下，在應用程式中顯示工作流程設計工具可能很有用：  
  
-   監視應用程式 (讓使用者視覺化處理序，以及有關處理序的執行階段資料，例如目前作用中狀態、彙總執行時間資料，或有關工作流程執行個體的其他資訊)。  
  
-   讓使用者以有限活動集來自訂處理序的應用程式。  
  
 為了支援這些類型的應用程式，.NET Framework 隨附工作流程設計工具，該設計工具可裝載於 WPF 應用程式或具有適當 WPF 裝載程式碼的 WinForms 應用程式。 這個範例會示範下列情況：  
  
-   重新裝載 WF 設計工具。  
  
-   使用重新裝載的工具箱以及屬性方格。  
  
## <a name="rehosting-the-designer"></a>重新裝載設計工具  
 這個範例示範如何建立 WPF 配置以包含設計工具，如下列方格配置所示 (基於空間考量而省略工具箱程式碼)。 請注意包含設計工具和屬性方格之框線的命名。  
  
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
  
 範例接著建立設計工具，並且將其主要 <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> 和 <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> 與使用者介面中的適當容器產生關聯。 在下列範例中有些其他程式碼行需要說明。 若要針對 <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> 隨附的活動，與預設活動設計工具建立關聯，必須使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 呼叫。 會呼叫 <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> 以傳入所要編輯的 WF 項目。 最後，<xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (主要畫布) 和 <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (屬性方格) 會放在使用者介面上。  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>使用重新裝載的工具列  
 這個範例在 XAML 中以宣告方式使用重新裝載的工具箱控制項。 請注意，在程式碼中可將類型傳遞給 <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> 建構函式。  
  
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
  
#### <a name="using-the-sample"></a>使用範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 DesignerRehosting.sln 方案。  
  
2.  按 F5 編譯和執行應用程式。  
  
3.  WPF 應用程式隨即以重新裝載的設計工具啟動。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`