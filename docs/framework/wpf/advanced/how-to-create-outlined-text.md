---
title: "如何：建立外框文字 | Microsoft Docs"
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
  - "漸層筆刷"
  - "線形漸層筆刷"
  - "外框文字"
  - "印刷樣式, 線形漸層筆刷"
  - "印刷樣式, 外框效果"
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：建立外框文字
在大部分情況中，當您對 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中的文字字串加入裝飾時，其實會使用由一組不同字元或圖像 \(Glyph\) 組成的字串。  例如，您可建立線形漸層筆刷，然後將它套用至 <xref:System.Windows.Controls.TextBox> 物件的 <xref:System.Windows.Controls.Control.Foreground%2A> 屬性。  當您顯示或編輯文字方塊時，線形漸層筆刷會自動套用至目前文字字串中的字元集。  
  
 ![以線性漸層筆刷顯示的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext01.png "OutlinedText01")  
套用線形漸層筆刷至文字方塊的範例  
  
 但是，您也可以將文字轉換為 <xref:System.Windows.Media.Geometry> 物件，以便建立具有豐富外觀的其他文字類型。  例如，您可以根據文字字串的外框來建立 <xref:System.Windows.Media.Geometry> 物件。  
  
 ![以線性漸層筆刷繪製外框的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext02.png "OutlinedText02")  
套用線形漸層筆刷至文字外框幾何圖形的範例  
  
 將文字轉換為 <xref:System.Windows.Media.Geometry> 物件後，文字就不再是字元的集合，因此您無法修改文字字串中的字元。  不過，您可以透過修改轉換後文字的描邊和填滿屬性，影響文字的外觀。  描邊是指轉換後文字的外框，填滿則是指轉換後文字之外框內的區域。  
  
 下列範例說明透過修改轉換後文字的描邊和填滿，建立視覺效果的數個方法。  
  
 ![使用不同填色和筆觸色彩的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext03.png "OutlinedText03")  
將筆劃和填滿設定為不同色彩的範例  
  
 ![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext04.png "OutlinedText04")  
在筆劃上套用影像筆刷的範例  
  
 也可以修改轉換後文字的週框方塊矩形，或反白。  下列範例說明透過修改所轉換文字的描邊和反白顯示，建立視覺效果的方法。  
  
 ![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext05.png "OutlinedText05")  
在筆劃和反白顯示上套用影像筆刷的範例  
  
## 範例  
 將文字轉換為 <xref:System.Windows.Media.Geometry> 物件的關鍵在於使用 <xref:System.Windows.Media.FormattedText> 物件。  建立這個物件之後，就可以使用 <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> 和 <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> 方法將文字轉換為 <xref:System.Windows.Media.Geometry> 物件。  第一個方法會傳回格式化文字的幾何圖形，第二個方法則會傳回格式化文字之週框方塊的幾何圖形。  下列程式碼範例顯示如何建立 <xref:System.Windows.Media.FormattedText> 物件，並擷取格式化文字和其週框方塊的幾何圖形。  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 為了要顯示擷取後的 <xref:System.Windows.Media.Geometry> 物件，您必須存取用來顯示轉換後文字的物件的 <xref:System.Windows.Media.DrawingContext>。  在這些程式碼範例中，這是透過建立自訂控制項物件來達成，這個控制項物件是從支援使用者定義呈現的類別衍生而來。  
  
 若要在自訂控制項中顯示 <xref:System.Windows.Media.Geometry> 物件，請覆寫 <xref:System.Windows.UIElement.OnRender%2A> 方法。  您覆寫後的方法應該要使用 <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> 方法來繪製 <xref:System.Windows.Media.Geometry> 物件。  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## 請參閱  
 [繪製格式化的文字](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)