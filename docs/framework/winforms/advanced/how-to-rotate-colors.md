---
title: "如何：旋轉色彩 | Microsoft Docs"
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
  - "色彩, 旋轉"
  - "範例 [Windows Form], 旋轉色彩"
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：旋轉色彩
將四度空間中的旋轉視覺化很困難。  但是，如果能將其中一個色彩元素固定，視覺化起來就會比較容易。  假設已同意將 Alpha 元素固定為 1 \(完全不透明\)，  然後就可以用紅色、綠色和藍色三個軸，將三度色彩空間視覺化，如下圖所示。  
  
 ![重新著色](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")  
  
 您可以將色彩想像成是三度空間中的一個點。  例如，在三度空間中的 \(1, 0, 0\) 這個點代表紅色，\(0, 1, 0\) 這個點則代表綠色。  
  
 下圖顯示的就是何謂在紅綠平面中將色彩 \(1, 0, 0\) 旋轉 60 度角。  在與紅綠平面平行的平面中旋轉可以想像成是以藍色軸為中心的旋轉。  
  
 ![重新著色](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")  
  
 下圖顯示的是如何初始化色彩矩陣，分別執行以這三個座標軸 \(紅色、綠色、藍色\) 為中心的旋轉。  
  
 ![重新著色](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")  
  
## 範例  
 下列範例會使用全部為 \(1, 0, 0.6\) 一個色彩的影像，並套用以藍色軸為中心的 60 度旋轉。  旋轉的角度是在與紅綠平面平行的平面中散出。  
  
 下圖左邊顯示的是原始的影像，右邊顯示的是旋轉色彩的影像。  
  
 ![旋轉色彩](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")  
  
 下圖顯示以下程式碼執行色彩旋轉的視覺化效果。  
  
 ![重新著色](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  請以系統中有效的影像檔案名稱和路徑來取代 `RotationInput.bmp`。  
  
## 請參閱  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [將影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)