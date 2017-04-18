---
title: "Windows Form 座標 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "工作區座標"
  - "座標, Windows Form"
  - "螢幕座標"
  - "Windows Form 座標"
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Windows Form 座標
Windows Form 的座標系統是以裝置座標為基礎，而在 Windows Form 中進行繪製時基本的測量單位則是裝置單位 \(一般是像素\)。  螢幕上的位置是以 X 和 Y 座標軸來描述，X 座標軸是向右遞增，而 Y 座標軸則是從上到下遞增。  相對於螢幕的原點位置會依據您是指定螢幕座標或工作區座標而有所不同。  
  
## 螢幕座標  
 Windows Form 應用程式會以螢幕座標來指定視窗在螢幕上的位置。  如果是螢幕座標，原點位於螢幕的左上角。  視窗的完整區域通常是由 <xref:System.Drawing.Rectangle> 結構來描述，此結構所包含的螢幕座標是兩個分別定義視窗左上角和右下角的點。  
  
## 工作區座標  
 Windows Form 應用程式是使用工作區座標來指定表單或控制項中點的位置。  工作區座標的原點位於控制項或表單的工作區的左上角。  不論表單或控制項是位於螢幕上的哪個位置，工作區座標確保了應用程式在表單或控制項中進行繪製時可以使用一致的座標值。  
  
 工作區的維度也是由包含了工作區座標的 <xref:System.Drawing.Rectangle> 結構來描述。  在所有情況下，矩形左上方的座標都是包含於工作區中，而右下方座標則排除在外。  圖形作業不會包含工作區的右邊緣與下邊緣，  例如，<xref:System.Drawing.Graphics.FillRectangle%2A> 方法會填滿至指定矩形的右邊緣與下邊緣，但不會包含這些邊緣。  
  
## 從一種座標對應至另一種座標  
 有時候，您可能需要從螢幕座標對應至工作區座標。  經由使用 <xref:System.Windows.Forms.Control> 類別中可供使用的 <xref:System.Windows.Forms.Control.PointToClient%2A> 和 <xref:System.Windows.Forms.Control.PointToScreen%2A> 方法，就可以輕鬆地達成這項目的。  例如，<xref:System.Windows.Forms.Control> 的 <xref:System.Windows.Forms.Control.MousePosition%2A> 屬性是以螢幕座標來報告，但您想要將它們轉換成工作區座標。  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.PointToClient%2A>   
 <xref:System.Windows.Forms.Control.PointToScreen%2A>