---
title: "如何：清除自訂控制項上的筆墨 | Microsoft Docs"
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
  - "自訂控制項, 清除筆墨"
  - "筆墨, 在自訂控制項上清除"
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：清除自訂控制項上的筆墨
<xref:System.Windows.Ink.IncrementalStrokeHitTester> 會判斷目前繪製的筆劃是否和其他筆劃相交集。  這可以用來建立控制項，讓使用者清除部分筆劃，和使用者可以在 <xref:System.Windows.Controls.InkCanvas> 上執行的動作一樣 \(當 <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> 設定為 <xref:System.Windows.Controls.InkCanvasEditingMode> 時\)。  
  
## 範例  
 下列範例會建立一個自訂控制項，可讓使用者清除部分筆劃。  這個範例會建立一個控制項，在初始筆墨後會包含該筆墨。  如果要建立收集筆墨的控制項，請參閱[建立筆墨輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]