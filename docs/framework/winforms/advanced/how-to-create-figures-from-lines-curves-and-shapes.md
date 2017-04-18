---
title: "如何：從直線、曲線和形狀建立圖形 | Microsoft Docs"
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
  - "圖形, 從線條建立"
  - "圖形, 從圖案建立"
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：從直線、曲線和形狀建立圖形
若要建立圖形，請建構 <xref:System.Drawing.Drawing2D.GraphicsPath>，然後呼叫方法 \(例如 <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> 和 <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>\)，將基本圖形加入至路徑。  
  
## 範例  
 下列程式碼範例會建立含有圖形的路徑：  
  
-   第一個範例會建立包含單一圖形的路徑。  圖形只包含單一弧形。  這個弧形的散出角度為 \-180 度，也就是預設座標系統的逆時針方向。  
  
-   第二個範例會建立包含兩個圖形的路徑。  第一個圖形是弧形，後面跟著一條直線。  第二個圖形是一條直線，後面跟著一條曲線再加上一條直線。  第一個圖形的左邊是開放的，第二個圖形是封閉的。  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它們需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath>   
 [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)   
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)