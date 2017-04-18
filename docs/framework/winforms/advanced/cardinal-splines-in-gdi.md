---
title: "GDI+ 中的基本曲線 | Microsoft Docs"
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
  - "基本曲線"
  - "GDI+, 基本曲線"
  - "曲線, 基本"
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# GDI+ 中的基本曲線
基本曲線是聯結起來，形成大型曲線的個別曲線序列 \(Sequence\)。  曲線是由點陣列和緊縮程度參數指定而成。  基本曲線會平滑地通過陣列中的每一個點；拉緊曲線後將不會出現任何銳角或突兀的改變。  下圖將顯示一組點集合和通過該集合中所有點的基本曲線。  
  
 ![基本曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.png "Aboutgdip02\_art09")  
  
## 實體曲線和數學曲線  
 實體曲線是指薄木片或其他具有彈性的材質。  在使用數學上的曲線之前，程式設計人員以前使用實體曲線來繪製曲線。  設計程式人員將曲線放置在紙張上，並且使用指定的點集合將它固定起來。  接下來設計人員使用畫筆或鉛筆沿著曲線繪製出一條曲線出來。  指定的點集合可以產生各種曲線，端視實體曲線的屬性而定。  例如，不具有彎曲屬性的曲線和具有彈性的曲線所產生出來的曲線將大不相同。  
  
 數學曲線公式是根據彈性木棍的屬性而來，因此數學曲線產生的曲線和實體曲線產生的曲線效果相似。  由於不同緊縮程度的實體曲線透過指定點組合所產生的曲線並不相同，因此不同的數學曲線緊縮程度參數值透過指定點組合所產生的曲線也不相同。  下圖將顯示四條通過相同點組合的基本曲線。  每一條曲線都會顯示其張力。  張力 0 會對應為無限的實體張力，它會強迫曲線在點與點之間採取最短的距離 \(直線\)。  張力 1 不會對應到任何實體張力，它允許曲線使用最直的路徑。  如果張力的值大於一，則曲線將和壓縮的彈簧一樣，被迫使用較長的路徑。  
  
 ![基本曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.png "Aboutgdip02\_art10")  
  
 上圖中的四條曲線共用起始點的切線。  切線是指從起始點開始，沿著曲線到下一點所繪製出來的線條。  同樣的，在結束點的共用切線是從結束點開始，沿著曲線到上一點所繪製出來的曲線。  
  
 若要繪製基本曲線，您需要 <xref:System.Drawing.Graphics> 類別執行個體、<xref:System.Drawing.Pen> 和 <xref:System.Drawing.Point> 物件陣列。<xref:System.Drawing.Graphics> 類別執行個體提供 <xref:System.Drawing.Graphics.DrawCurve%2A> 方法來繪製曲線，而 <xref:System.Drawing.Pen> 則是儲存曲線的屬性，例如線條寬度和色彩。  <xref:System.Drawing.Point> 物件陣列儲存曲線所通過的點。  下列程式碼範例會示範如何繪製一條通過 `myPointArray` 中這些點的基本曲線。  第三個參數即為緊縮程度。  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## 請參閱  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [建構和繪製曲線](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)