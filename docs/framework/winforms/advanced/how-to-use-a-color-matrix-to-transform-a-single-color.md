---
title: "如何：使用色彩矩陣轉換單一色彩 | Microsoft Docs"
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
  - "色彩矩陣, 使用"
  - "影像色彩, 轉換"
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：使用色彩矩陣轉換單一色彩
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供 <xref:System.Drawing.Image> 和 <xref:System.Drawing.Bitmap> 類別，以供儲存與操作影像。  <xref:System.Drawing.Image> 和 <xref:System.Drawing.Bitmap> 物件會將每個像素的色彩儲存為 32 位元的數字：紅、藍、綠三色和 Alpha 值各用 8 位元來表示。  每一個元素的數字都是從 0 到 255，0 表示不含濃度，255 表示最高濃度。  Alpha 元素指定色彩的透明度：0 表示完全透明，255 表示完全不透明。  
  
 色彩向量由 4 個元素值組成，格式為 \(紅色, 綠色, 藍色, Alpha\)。  例如，色彩向量 \(0, 255, 0, 255\) 表示不含紅色或藍色的不透明色彩，但是綠色的濃度達最高。  
  
 另外一種表示色彩的慣例是使用數字 1 來表示最高濃度。  如果使用這個慣例，那麼上一段落中所描述的色彩則應用向量 \(0, 1, 0, 1\) 表示。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 執行色彩轉換時所用的慣例是用 1 表示最高濃度。  
  
 您可以將色彩向量乘以 4×4 的矩陣，即可將線形轉換 \(旋轉、縮放等\) 套用至色彩向量。  但是，不能使用 4×4 的矩陣來執行轉移 \(非線形\)。  如果將空的第五個座標 \(例如，數字 1\) 加入至每一個色彩向量中，就可以使用 5×5 的矩陣來套用線形轉換和轉移的任何組合。  包含線形轉換的轉換後面再接著轉換，即稱為仿射轉換。  
  
 例如，假設您要從色彩 \(0.2, 0.0, 0.4, 1.0\) 開始，並套用下列轉換：  
  
1.  將紅色元素加倍  
  
2.  將紅色、綠色和藍色元素加上 0.2  
  
 下列矩陣乘法將會依照列出來的順序執行成對的轉換。  
  
 ![重新著色](../../../../docs/framework/winforms/advanced/media/recoloring01.png "recoloring01")  
  
 色彩矩陣的元素是根據先列後行的順序來編列索引 \(以零起始\)。  例如，在矩陣 M 中第五列、第三行的項目便是以 M\[4\]\[2\] 來表示。  
  
 5×5 單位矩陣 \(顯示在下圖中\) 的對角線上都是 1，其他位置上都是 0。  如果您將色彩向量乘以單位矩陣，色彩向量不會變更。  若要組成色彩轉換矩陣，從單位矩陣開始是很方便的方式，然後做小幅度變更來產生想要的轉換。  
  
 ![重新著色](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")  
  
 如需矩陣和轉換的詳細資訊，請參閱[座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)。  
  
## 範例  
 下列範例會使用全部為 \(0.2, 0.0, 0.4, 1.0\) 一個色彩的影像，並套用上一段所描述的轉換。  
  
 下圖左邊顯示的是原始的影像，右邊顯示的是轉換的影像。  
  
 ![色彩](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")  
  
 下列範例中的程式碼是使用以下步驟來執行重新著色：  
  
1.  初始化 <xref:System.Drawing.Imaging.ColorMatrix> 物件。  
  
2.  建立 <xref:System.Drawing.Imaging.ImageAttributes> 物件並將 <xref:System.Drawing.Imaging.ColorMatrix> 物件傳遞至 <xref:System.Drawing.Imaging.ImageAttributes> 物件的 <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> 方法。  
  
3.  將 <xref:System.Drawing.Imaging.ImageAttributes> 物件傳遞至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawImage%2A> 方法。  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [將影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)   
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)