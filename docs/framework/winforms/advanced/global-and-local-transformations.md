---
title: "全域和區域轉換 | Microsoft Docs"
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
  - "矩陣, 使用轉換"
  - "轉換, 全域"
  - "轉換, 本機"
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 全域和區域轉換
全域轉換會套用至特定 <xref:System.Drawing.Graphics> 物件繪製的所有項目。  相對地，區域轉換只套用至要繪製的特定項目。  
  
## 全域轉換  
 如果要建立全域轉換，請建構 <xref:System.Drawing.Graphics> 物件，然後管理其 <xref:System.Drawing.Graphics.Transform%2A> 屬性。  <xref:System.Drawing.Graphics.Transform%2A> 屬性是一個 <xref:System.Drawing.Drawing2D.Matrix> 物件，因此它可以存放仿射轉換的任何序列。  儲存在 <xref:System.Drawing.Graphics.Transform%2A> 屬性的轉換又稱為全局轉換。  <xref:System.Drawing.Graphics> 類別提供幾個方法，用來建置複合的全局轉換：<xref:System.Drawing.Graphics.MultiplyTransform%2A>、<xref:System.Drawing.Graphics.RotateTransform%2A>、<xref:System.Drawing.Graphics.ScaleTransform%2A> 和 <xref:System.Drawing.Graphics.TranslateTransform%2A>。  下列範例會繪製兩次橢圓形：一次是在建立全局轉換之前，一次是在建立之後。  轉換會先在 Y 方向縮放 0.5 個係數，然後在 X 方向轉換 50 個單位，然後再旋轉 30 度。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 下圖將顯示轉換所使用的矩陣。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05\_art14")  
  
> [!NOTE]
>  在上述範例中，橢圓形會繞著座標系統的原點旋轉，該原點位於工作區 \(Client Area\) 的左上角。  這項作業產生的結果和在橢圓形中心點旋轉並不相同。  
  
## 區域轉換  
 區域轉換會套用至要繪製的特定項目。  例如，<xref:System.Drawing.Drawing2D.GraphicsPath> 物件的 <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> 方法可用來轉換該路徑的資料點 \(Data Point\)。  下列範例繪製未轉換的矩形和經過旋轉和轉換的路徑   \(假設沒有全局轉換\)。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 您可以結合全局轉換和區域轉換來達到各種效果。  例如，您可以使用全局轉換來修訂座標系統，並可使用區域轉換來旋轉和縮放新座標系統所繪製的物件。  
  
 假設您想要使用一個座標系統，其原點距離工作區左邊緣 200 像素和工作區頂端 150 像素處。  此外，假設您想使用像素做為度量單位，其 x 軸指向右方，且其 y 軸指向上方。  預設座標系統的 y 軸指向下方，因此您必須在水平軸執行反射。  下圖將顯示此類反射的矩陣。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.png "AboutGdip05\_art15")  
  
 接下來，假設您必須執行右方 200 單位和下方 150 單位的轉換。  
  
 下列範例會建立上述說明的座標系統，使用的方法是設定 <xref:System.Drawing.Graphics> 物件的全局轉換。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 下列程式碼 \(位於上述範例的結束處\) 建立單一矩形組成的路徑，其中該矩形的左上角位於新座標系統的原點。  該矩形將填入色彩兩次，其中一次並未使用區域轉換，另外一次則使用區域轉換。  區域轉換包括水平縮放 2 個係數，隨後進行 30 度的旋轉。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 下圖將顯示新的座標系統和兩個矩形。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.png "AboutGdip05\_art16")  
  
## 請參閱  
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [使用 Managed GDI\+ 中的轉換](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)