---
title: "如何：使用色彩重新對應表 | Microsoft Docs"
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
  - "色彩重新對應表, 使用"
  - "色彩表, 重新對應色彩的方式"
  - "自訂色彩, 使用色彩重新對應表建立"
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用色彩重新對應表
重新對應是指根據色彩重新對應表轉換影像中色彩的程序。  色彩重新對應表是 <xref:System.Drawing.Imaging.ColorMap> 物件的陣列。  陣列中的每個 <xref:System.Drawing.Imaging.ColorMap> 物件都具有 <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> 屬性和 <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> 屬性。  
  
 當 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 繪製影像時，會將影像中的每一個像素與舊色彩陣列加以比較。  如果像素的色彩與舊的色彩相符，就會將色彩變成對應的新色彩。  色彩只有在呈現時才會變更，也就是說影像本身的色彩值 \(儲存在 <xref:System.Drawing.Image> 或 <xref:System.Drawing.Bitmap> 物件中\) 不會變更。  
  
 若要繪製重新對應的影像，請初始化 <xref:System.Drawing.Imaging.ColorMap> 物件的陣列。  將該陣列傳遞至 <xref:System.Drawing.Imaging.ImageAttributes> 物件的 <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> 方法，然後再將 <xref:System.Drawing.Imaging.ImageAttributes> 物件傳遞至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawImage%2A> 方法。  
  
## 範例  
 下列範例會從 RemapInput.bmp 檔案建立 <xref:System.Drawing.Image> 物件。  程式碼將建立只包含單一 <xref:System.Drawing.Imaging.ColorMap> 物件的色彩重新對應表。  `ColorRemap`  物件的 <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> 屬性是紅色，<xref:System.Drawing.Imaging.ColorMap.NewColor%2A> 屬性則為藍色。  繪製影像時，一次不含重新對應，一次包含重新對應。  重新對應程序會將所有紅色像素變成藍色。  
  
 下圖左邊顯示的是原始的影像，右邊顯示的是重新對應的影像。  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [將影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)   
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)