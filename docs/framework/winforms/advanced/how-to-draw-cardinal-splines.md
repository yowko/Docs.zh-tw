---
title: "如何：繪製基本曲線 | Microsoft Docs"
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
  - "基本曲線, 繪製"
  - "繪製, 基本曲線"
  - "圖形, 基本曲線"
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：繪製基本曲線
基本曲線是指平滑通過一組指定點的曲線。  若要繪製基本曲線，請建立 <xref:System.Drawing.Graphics> 物件，並將點陣列的位址傳遞至 <xref:System.Drawing.Graphics.DrawCurve%2A> 方法。  
  
### 繪製鐘形基本曲線  
  
-   下列範例繪製通過五個指定點的鐘形基本曲線。  下圖顯示的是曲線和五個點。  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### 繪製封閉的基本曲線  
  
-   請使用 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawClosedCurve%2A> 方法來繪製封閉的基本曲線。  在封閉的基本曲線中，曲線會延伸陣列中的最後一個點，和陣列中的第一個點連接。  下列範例繪製通過六個指定點的封閉基本曲線。  下圖顯示的是封閉曲線和六個點。  
  
 ![基本曲線](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### 變更基本曲線的彎曲方式  
  
-   將伸張引數傳遞至 <xref:System.Drawing.Graphics.DrawCurve%2A> 方法，便可變更基本曲線的彎曲方式。  下列範例繪製通過同一組點的三個基本曲線。  下圖顯示的是三個曲線和它們的伸張值。  請注意，當伸張值為 0 時，點與點之間是以直線連接。  
  
 ![基本曲線](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它們需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [建構和繪製曲線](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)