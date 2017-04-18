---
title: "如何：設定物件隨滑鼠指標移動 | Microsoft Docs"
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
  - "游標 (滑鼠指標), 讓物件跟隨"
  - "跟隨滑鼠指標 (游標)"
  - "滑鼠指標 (游標), 讓物件跟隨"
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：設定物件隨滑鼠指標移動
本範例示範當滑鼠指標在螢幕上移動時，如何變更物件的維度 \(Dimension\)。  
  
 此範例包括用來建立[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案，以及用來建立事件處理常式的程式碼後置檔案。  
  
## 範例  
 下列 [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] 會建立 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] \(由 <xref:System.Windows.Controls.StackPanel> 內的 <xref:System.Windows.Shapes.Ellipse> 組成\)，並附加 <xref:System.Windows.UIElement.MouseMove> 事件的事件處理常式。  
  
 [!code-xml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 下列程式碼後置會建立 <xref:System.Windows.UIElement.MouseMove> 事件處理常式。  當滑鼠指標移動時，<xref:System.Windows.Shapes.Ellipse> 的高度和寬度也會隨之增加及減少。  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## 請參閱  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)