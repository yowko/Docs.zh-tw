---
title: "如何：填滿開放圖形 | Microsoft Docs"
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
  - "圖形, 填滿"
  - "開放圖形, 填滿"
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：填滿開放圖形
您可以將 <xref:System.Drawing.Drawing2D.GraphicsPath> 物件傳遞至 <xref:System.Drawing.Graphics.FillPath%2A> 方法，藉以填滿路徑。  <xref:System.Drawing.Graphics.FillPath%2A> 方法會根據路徑目前設定的填色模式 \(替代或彎曲\) 來填滿路徑。  如果路徑中有任何開放圖形，會將這些圖形當成封閉圖形來填滿。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 會從結束點到起點繪製一條直線來封閉圖形。  
  
## 範例  
 下列範例會建立包含一個開放圖形 \(弧形\) 和一個封閉圖形 \(橢圓形\) 的路徑。  <xref:System.Drawing.Graphics.FillPath%2A> 方法會根據預設的填色模式 \(<xref:System.Drawing.Drawing2D.FillMode>\) 來填滿路徑。  
  
 下圖顯示的是範例程式碼的輸出。  請注意，已將路徑當成用結束點到起點的直線封閉的開放圖形填滿 \(根據 <xref:System.Drawing.Drawing2D.FillMode>\)。  
  
 ![填入開啟路徑](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath>   
 [GDI\+ 中的圖形路徑](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)