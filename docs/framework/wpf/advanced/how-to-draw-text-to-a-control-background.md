---
title: "如何：繪製文字至控制項的背景 | Microsoft Docs"
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
  - "背景, 將文字繪製至"
  - "控制項, 將文字繪製至背景"
  - "繪製, 將文字至控制項背景"
  - "文字, 繪製至控制項背景"
  - "印刷樣式, 將文字繪製至控制項背景"
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：繪製文字至控制項的背景
將文字字串轉換為 <xref:System.Windows.Media.FormattedText> 物件，然後將物件繪製至控制項的 <xref:System.Windows.Media.DrawingContext>，就可以直接將文字繪製至控制項的背景。  您也可以使用這個技術來繪製至衍生自 <xref:System.Windows.Controls.Panel> 之物件 \(如 <xref:System.Windows.Controls.Canvas> 和 <xref:System.Windows.Controls.StackPanel>\) 的背景。  
  
 ![將文字當做背景顯示的控制項](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
具有自訂文字背景的控制項範例  
  
## 範例  
 若要繪製至控制項的背景，請建立新的 <xref:System.Windows.Media.DrawingBrush> 物件，並將轉換後的文字繪製至物件的 <xref:System.Windows.Media.DrawingContext>。  然後，將新的 <xref:System.Windows.Media.DrawingBrush> 指派給控制項的背景屬性。  
  
 下列程式碼範例顯示如何建立 <xref:System.Windows.Media.FormattedText> 物件，以及繪製至 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.Button> 物件的背景。  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## 請參閱  
 <xref:System.Windows.Media.FormattedText>   
 [繪製格式化的文字](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)