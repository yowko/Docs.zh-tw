---
title: "自訂複合設計工具 - 工作流程項目展示器 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# 自訂複合設計工具 - 工作流程項目展示器
<xref:System.Activities.Presentation.WorkflowItemPresenter> 是 WF 設計工具程式設計模型中的關鍵型別，可允許建立可以放置任意活動的「卸除區」。這個範例示範如何建置會呈現這類「卸除區」的活動設計工具。  
  
 這個範例會示範下列情況：  
  
## 示範  
  
-   建立具有 <xref:System.Activities.Presentation.WorkflowItemPresenter> 的自訂活動設計工具。  
  
-   使用中繼資料存放區登錄自訂設計工具。  
  
-   以宣告和強制方式設計重新裝載之工具箱的程式。  
  
## 範例詳細資料  
 這個範例的程式碼會示範：  
  
-   針對 `SimpleNativeActivity` 類別建置自訂活動設計工具。  
  
-   建立具有 <xref:System.Activities.Presentation.WorkflowItemPresenter> 的自訂活動設計工具  
  
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
  
 請注意繫結至 `ModelItem.Body` 的 WPF 資料繫結用法。`ModelItem` 是 <xref:System.Activities.Presentation.WorkflowElementDesigner> 上的屬性，它會參考設計工具的目標基礎物件，在這個範例中為 **SimpleNativeActivity**。  
  
#### 若要設定、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。  
  
2.  按 F5 編譯和執行應用程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## 請參閱  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>   
 [使用工作流程設計工具開發應用程式](../Topic/Developing%20Applications%20with%20the%20Workflow%20Designer.md)