---
title: "如何：將資料繫結至 InkCanvas | Microsoft Docs"
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
  - "InkCanvas，資料繫結至"
  - "資料繫結，至 InkCanvas"
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：將資料繫結至 InkCanvas
## <a name="example"></a>範例  
 下列範例示範如何繫結<xref:System.Windows.Controls.InkCanvas.Strokes%2A>屬性<xref:System.Windows.Controls.InkCanvas>到另一個<xref:System.Windows.Controls.InkCanvas>。  
  
 [!code-xml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 下列範例示範如何繫結<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>到資料來源的屬性。  
  
 [!code-xml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 下列範例會宣告兩個<xref:System.Windows.Controls.InkCanvas> XAML 中的物件，並建立它們與其他資料來源之間的資料繫結。  第一個<xref:System.Windows.Controls.InkCanvas>，稱為`ic`，繫結至兩個資料來源。  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>和<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性`ic`繫結至<xref:System.Windows.Controls.ListBox>物件，依序繫結至 XAML 所定義的陣列。  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>， <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>，和<xref:System.Windows.Controls.InkCanvas.Strokes%2A>的第二個屬性<xref:System.Windows.Controls.InkCanvas>繫結至第一個<xref:System.Windows.Controls.InkCanvas>， `ic`。  
  
 [!code-xml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]