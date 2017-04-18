---
title: "如何：工具列上的樣式控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自訂工具列上的控制項"
  - "設定工具列上的控制項樣式"
  - "工具列"
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：工具列上的樣式控制項
<xref:System.Windows.Controls.ToolBar> 會定義 <xref:System.Windows.ResourceKey> 物件，用以指定 <xref:System.Windows.Controls.ToolBar> 內控制項的樣式。  若要設定 <xref:System.Windows.Controls.ToolBar> 中控制項的様式，請將樣式的 `x:key` 屬性設為 <xref:System.Windows.Controls.ToolBar> 中定義的 <xref:System.Windows.ResourceKey>。  
  
 <xref:System.Windows.Controls.ToolBar> 會定義下列 <xref:System.Windows.ResourceKey> 物件：  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## 範例  
 下列範例會定義 <xref:System.Windows.Controls.ToolBar> 內控制項的樣式。  
  
 [!code-xml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## 請參閱  
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)