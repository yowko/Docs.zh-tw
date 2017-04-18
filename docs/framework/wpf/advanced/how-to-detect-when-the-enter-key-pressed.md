---
title: "如何：偵測何時按下 Enter 鍵 | Microsoft Docs"
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
  - "ENTER 鍵, 偵測"
  - "索引鍵, Enter"
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：偵測何時按下 Enter 鍵
本範例示範如何偵測何時在鍵盤上按下 <xref:System.Windows.Input.Key> 鍵。  
  
 本範例包含一個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案和一個程式碼後置的檔案。  
  
## 範例  
 當使用者按下 <xref:System.Windows.Controls.TextBox> 中的 <xref:System.Windows.Input.Key> 鍵時，文字方塊中的輸入會出現在[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的另一個區域。  
  
 下列 [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] 會建立由 <xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.TextBox> 組成的使用者介面。  
  
 [!code-xml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 下列程式碼後置會建立 <xref:System.Windows.UIElement.KeyDown> 事件處理常式。  如果按下的按鍵是 <xref:System.Windows.Input.Key> 鍵，<xref:System.Windows.Controls.TextBlock> 中會顯示一則訊息。  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## 請參閱  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)