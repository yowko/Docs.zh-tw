---
title: "如何：建立快顯功能表的動畫 | Microsoft Docs"
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
  - "動畫, Popup 控制項"
  - "Popup 控制項, 動畫"
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：建立快顯功能表的動畫
本範例會顯示兩個方式來建立 <xref:System.Windows.Controls.Primitives.Popup> 控制項的動畫。  
  
## 範例  
 下列範例會將 <xref:System.Windows.Controls.Primitives.PopupAnimation> 屬性設為 <xref:System.Windows.Controls.Primitives.PopupAnimation> 的值，讓 <xref:System.Windows.Controls.Primitives.Popup> 在顯示時「滑入」。  
  
 為了旋轉 <xref:System.Windows.Controls.Primitives.Popup>，本範例會將 <xref:System.Windows.Media.RotateTransform> 指派至 <xref:System.Windows.Controls.Canvas> 上的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性，它是 <xref:System.Windows.Controls.Primitives.Popup> 的子項目。  
  
 為了讓轉換可以正常運作，範例必須將 <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> 屬性設為 `true`。  此外，<xref:System.Windows.Controls.Canvas> 內容上的 <xref:System.Windows.FrameworkElement.Margin%2A> 必須指定足夠的空間讓 <xref:System.Windows.Controls.Primitives.Popup> 旋轉。  
  
 [!code-xml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 下列範例顯示 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件 \(在按一下 <xref:System.Windows.Controls.Button> 時發生\) 如何觸發 <xref:System.Windows.Media.Animation.Storyboard> 啟動動畫。  
  
 [!code-xml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## 請參閱  
 <xref:System.Windows.UIElement.RenderTransform%2A>   
 <xref:System.Windows.Controls.Primitives.BulletDecorator>   
 <xref:System.Windows.Media.RotateTransform>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 <xref:System.Windows.Controls.Primitives.Popup>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)   
 [快顯功能表概觀](../../../../docs/framework/wpf/controls/popup-overview.md)