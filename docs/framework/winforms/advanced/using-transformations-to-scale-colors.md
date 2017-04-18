---
title: "使用轉換調整色彩 | Microsoft Docs"
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
  - "色彩, 縮放比例"
  - "轉換, 進行色彩調整"
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 使用轉換調整色彩
縮放轉換會將四個色彩元素中的一或多個乘以一個數字。  代表縮放的色彩矩陣項目列在下表中。  
  
|要縮放的元素|矩陣項目|  
|------------|----------|  
|紅色|\[0\]\[0\]|  
|綠色|\[1\]\[1\]|  
|藍色|\[2\]\[2\]|  
|Alpha|\[3\]\[3\]|  
  
## 縮放一個色彩  
 下列範例會從 ColorBars2.bmp 檔案建構 <xref:System.Drawing.Image> 物件。  然後程式碼會以因數 2 縮放影像中每一個像素的藍色元素。  原始影像就繪製在變換影像的旁邊。  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 下圖左邊顯示的是原始的影像，右邊顯示的是縮放的影像。  
  
 ![調整色彩](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")  
  
 下表會列出藍色縮放前後四列的色彩向量。  請注意，四列色彩中的藍色元素是從 0.8 到 0.6。  這是因為 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 只會保留結果的小數部分。  例如，\(2\)\(0.8\) \= 1.6，1.6 的小數部分就是 0.6。  只保留小數部分可確保結果一定會在 \[0, 1\] 之間。  
  
|原始|縮放後|  
|--------|---------|  
|\(0.4, 0.4, 0.4, 1\)|\(0.4, 0.4, 0.8, 1\)|  
|\(0.4, 0.2, 0.2, 1\)|\(0.4, 0.2, 0.4, 1\)|  
|\(0.2, 0.4, 0.2, 1\)|\(0.2, 0.4, 0.4, 1\)|  
|\(0.4, 0.4, 0.8, 1\)|\(0.4, 0.4, 0.6, 1\)|  
  
## 縮放多個色彩  
 下列範例會從 ColorBars2.bmp 檔案建構 <xref:System.Drawing.Image> 物件。  然後程式碼會縮放影像中每一個像素的紅色、綠色和藍色元素。  紅色元素會縮小 25%，綠色元素會縮小 35%，藍色元素會縮小 50%。  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 下圖左邊顯示的是原始的影像，右邊顯示的是縮放的影像。  
  
 ![調整色彩](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")  
  
 下表會列出紅色、綠色和藍色縮放前後四列的色彩向量。  
  
|原始|縮放後|  
|--------|---------|  
|\(0.6, 0.6, 0.6, 1\)|\(0.45, 0.39, 0.3, 1\)|  
|\(0, 1, 1, 1\)|\(0, 0.65, 0.5, 1\)|  
|\(1, 1, 0, 1\)|\(0.75, 0.65, 0, 1\)|  
|\(1, 0, 1, 1\)|\(0.75, 0, 0.5, 1\)|  
  
## 請參閱  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [將影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)