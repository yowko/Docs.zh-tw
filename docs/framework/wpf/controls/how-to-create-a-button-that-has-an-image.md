---
title: "如何：建立具有影像的按鈕 | Microsoft Docs"
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
  - "Button 控制項 [WPF], 建立"
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：建立具有影像的按鈕
本範例說明如何將影像加入到 <xref:System.Windows.Controls.Button>。  
  
## 範例  
 下列範例會建立兩個 <xref:System.Windows.Controls.Button> 控制項。  一個 <xref:System.Windows.Controls.Button> 包含文字，另一個包含影像。  這個影像是位於範例專案資料夾底下名為 data 的子資料夾中。  使用者按一下有影像的 <xref:System.Windows.Controls.Button> 時，另一個 <xref:System.Windows.Controls.Button> 的背景和文字會改變。  
  
 這個範例會使用標記建立 <xref:System.Windows.Controls.Button> 控制項，但用程式碼撰寫 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式。  
  
 [!code-xml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## 請參閱  
 [控制項](../../../../docs/framework/wpf/controls/index.md)   
 [控制項程式庫](../../../../docs/framework/wpf/controls/control-library.md)