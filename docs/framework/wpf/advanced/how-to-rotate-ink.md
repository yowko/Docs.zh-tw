---
title: "如何：旋轉筆墨 | Microsoft Docs"
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
  - "筆墨, 旋轉"
  - "旋轉筆墨"
ms.assetid: fac36cc9-dd01-41ca-9bde-9d33e3790bbe
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：旋轉筆墨
## 範例  
 下列範例會將筆墨從 <xref:System.Windows.Controls.InkCanvas> 複製到包含 <xref:System.Windows.Controls.InkPresenter> 的 <xref:System.Windows.Controls.Canvas>。  當應用程式複製筆墨時，也會將筆墨順時針旋轉 90 度。  
  
 [!code-xml[HowToRotateInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[HowToRotateInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml.cs#2)]  
  
## 範例  
 下列範例是一個自訂的 <xref:System.Windows.Documents.Adorner>，它會旋轉 <xref:System.Windows.Controls.InkPresenter> 上的筆劃。  
  
 [!code-csharp[AdornerForStrokes#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/RotatingAdornerForStrokes.cs#1)]
 [!code-vb[AdornerForStrokes#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/RotatingAdornerForStrokes.vb#1)]  
  
 下列範例是一個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案，它會定義 <xref:System.Windows.Controls.InkPresenter> 並在其中填入筆墨。  `Window_Loaded` 事件處理常式會將自訂裝飾項加入至 <xref:System.Windows.Controls.InkPresenter>。  
  
 [!code-xml[AdornerForStrokes#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[AdornerForStrokes#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml.cs#3)]
 [!code-vb[AdornerForStrokes#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/Window1.xaml.vb#3)]