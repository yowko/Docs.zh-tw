---
title: "如何：轉譯影像色彩 | Microsoft Docs"
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
  - "點陣圖 [Windows Form], 變更色彩"
  - "影像色彩 [Windows Form]"
  - "影像 [Windows Form], 變更色彩"
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：轉譯影像色彩
轉換會將四個色彩元素中的一或多個加上一個數值。  代表轉換的色彩矩陣項目列在下表中。  
  
|要轉換的元素|矩陣項目|  
|------------|----------|  
|紅色|\[4\]\[0\]|  
|綠色|\[4\]\[1\]|  
|藍色|\[4\]\[2\]|  
|Alpha|\[4\]\[3\]|  
  
## 範例  
 下列範例會從 ColorBars.bmp 檔案建構 <xref:System.Drawing.Image> 物件。  然後程式碼會將影像中每一個像素的紅色元素加上 0.75。  原始影像就繪製在變換影像的旁邊。  
  
 下圖左邊顯示的是原始的影像，右邊顯示的是轉換的影像。  
  
 ![轉譯色彩](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 下表會列出紅色轉換前後四列的色彩向量。  請注意，由於色彩元素的最大值是 1，因此第二列中的紅色元素並不會變更   \(同理，色彩元素的最小值 0\)。  
  
|原始|轉換的|  
|--------|---------|  
|黑色 \(0, 0, 0, 1\)|\(0.75, 0, 0, 1\)|  
|紅色 \(1, 0, 0, 1\)|\(1, 0, 0, 1\)|  
|綠色 \(0, 1, 0, 1\)|\(0.75, 1, 0, 1\)|  
|藍色 \(0, 0, 1, 1\)|\(0.75, 0, 1, 1\)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  請以系統中有效的影像檔名稱和路徑取代 `ColorBars.bmp` 。  
  
## 請參閱  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [將影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)