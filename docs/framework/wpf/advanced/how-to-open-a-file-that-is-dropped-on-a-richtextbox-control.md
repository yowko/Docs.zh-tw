---
title: "如何：開啟置放在 RichTextBox 控制項上的檔案 | Microsoft Docs"
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
  - "拖放功能 [WPF], 開啟置放的檔案"
  - "拖放功能 [WPF], RichTextBox"
  - "RichTextBox [WPF], 拖放"
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：開啟置放在 RichTextBox 控制項上的檔案
在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，<xref:System.Windows.Controls.TextBox>、<xref:System.Windows.Controls.RichTextBox> 和 <xref:System.Windows.Documents.FlowDocument> 控制項全都內建拖放功能。  此內建功能提供在控制項內和控制項間拖放文字的能力。  但是，並不提供透過將檔案放置到控制項上來開啟檔案的能力。  這些控制項也會將拖放事件標記為已處理。  因此，根據預設您無法加入自己的事件處理常式來提供開啟所放置檔案的功能。  
  
 若要在這些控制項中加入對拖放事件的其他處理方式，請使用 <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> 方法加入您的拖放事件處理常式。  將 `handledEventsToo` 參數設定為 `true`，可針對已經由事件路由上的另一個項目標記為已處理的路由事件，叫用指定的處理常式。  
  
> [!TIP]
>  您可以取代 <xref:System.Windows.Controls.TextBox>、<xref:System.Windows.Controls.RichTextBox> 和 <xref:System.Windows.Documents.FlowDocument> 的內建拖放功能，方法是處理拖放事件的預覽版本並將預覽版本標記為已處理。  不過，這樣會停用內建拖放功能，並不建議這麼做。  
  
## 範例  
 下列範例示範如何在 <xref:System.Windows.Controls.RichTextBox> 上加入 <xref:System.Windows.DragDrop.DragOver> 和 <xref:System.Windows.DragDrop.Drop> 事件的處理常式。  這個範例會使用 <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> 方法，並將 `handledEventsToo` 參數設定為 `true`，使得即使 <xref:System.Windows.Controls.RichTextBox> 已將這些事件標記為已處理，仍會叫用事件處理常式。  事件處理常式中的程式碼會加入功能，以開啟放置到 <xref:System.Windows.Controls.RichTextBox> 上的文字檔。  
  
 若要測試這個範例，請從 Windows 檔案總管拖曳文字檔或 RTF 檔案至 <xref:System.Windows.Controls.RichTextBox>。  該檔案將會在 <xref:System.Windows.Controls.RichTextBox> 中開啟。  如果您在放置檔案前按 SHIFT 鍵，該檔案將會開啟為純文字檔。  
  
 [!code-xml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]