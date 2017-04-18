---
title: "座標系統類型 | Microsoft Docs"
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
  - "座標系統"
  - "裝置座標系統"
  - "頁面座標系統"
  - "頁面轉換"
  - "轉換, 頁面"
  - "轉換, 全局"
  - "測量單位"
  - "全局座標系統"
  - "全局轉換"
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 座標系統類型
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 使用三個座標空間：全局、畫面和裝置。  全局座標 \(World Coordinate\) 是用來製作特定繪圖自然模型的座標，也就是在 .NET Framework 中傳遞到方法的座標。  畫面座標 \(Page Coordinate\) 則是指繪圖介面 \(例如表單或控制項\) 使用的座標系統。  裝置座標 \(Device Coordinate\) 是在其上進行繪圖的實體裝置 \(例如螢幕或紙張\) 所使用的座標。  呼叫 `myGraphics.DrawLine(myPen, 0, 0, 160, 80)` 時，傳遞至 <xref:System.Drawing.Graphics.DrawLine%2A> 方法的點 \(`(0, 0)` 和 `(160, 80)`\) 位於全局座標空間。  在 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可以在螢幕上繪製線條之前，座標會先經過轉換序列。  一個名為「全局轉換」的轉換會將全局座標轉換為畫面座標，而另一個名為「畫面轉換」的轉換則是將畫面座標轉換為裝置座標。  
  
## 轉換與座標系統  
 假設您想要使用原點位於工作區 \(Client Area\) 主體中，而非位於左上角的座標系統。  例如，您希望原點位於距離工作區左邊緣 100 像素和距離工作區頂端 50 像素的位置。  下圖將顯示此座標系統。  
  
 ![座標系統](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.png "AboutGdip05\_art01")  
  
 呼叫 `myGraphics.DrawLine(myPen, 0, 0, 160, 80)` 時，您會取得下圖中所顯示的線條。  
  
 ![座標系統](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.png "AboutGdip05\_art02")  
  
 在這三個座標空間中，您線條的結束點座標位置如下：  
  
|||  
|-|-|  
|World|\(0, 0\) 到 \(160, 80\)|  
|頁面|\(100, 50\) 到 \(260, 130\)|  
|裝置|\(100, 50\) 到 \(260, 130\)|  
  
 請注意，畫面座標空間的原點一律位於工作區的左上角。  此外，由於度量單位為像素，因此裝置座標和畫面座標是相同的。  如果您將度量單位設為像素以外的單位 \(例如英吋\)，則裝置座標便與畫面座標不同。  
  
 將全局座標對應至畫面座標的全局轉換，會存放在 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.Transform%2A> 屬性中。  上例中，全局轉換是指在 X 方向轉換 100 個單位和在 Y 方向轉換 50 個單位。  下列範例將設定 <xref:System.Drawing.Graphics> 物件的全局轉換，然後使用該 <xref:System.Drawing.Graphics> 物件來繪製上圖所顯示的線條：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 畫面轉換會將畫面座標對應至裝置座標。  <xref:System.Drawing.Graphics> 類別提供 <xref:System.Drawing.Graphics.PageUnit%2A> 和 <xref:System.Drawing.Graphics.PageScale%2A> 屬性，來管理畫面轉換。  <xref:System.Drawing.Graphics> 類別也提供兩個唯讀屬性，分別是 <xref:System.Drawing.Graphics.DpiX%2A> 和 <xref:System.Drawing.Graphics.DpiY%2A>，來檢視顯示裝置每英吋的水平點和垂直點。  
  
 您可以使用 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.PageUnit%2A> 屬性來指定像素以外的度量單位。  
  
> [!NOTE]
>  您不能將 <xref:System.Drawing.Graphics.PageUnit%2A> 屬性設定為 <xref:System.Drawing.GraphicsUnit>，因為這不是實體單位，而且會造成例外狀況 \(Exception\)。  
  
 下列範例從 \(0, 0\) 到 \(2, 1\) 繪製一條線，其中點 \(2, 1\) 是指距離 \(0, 0\) 點右邊 2 英吋和下方 1 英吋的位置：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  如果建構畫筆時未指定畫筆寬度，則上述範例將繪製出一條寬為一英吋的線條。  您可以在 <xref:System.Drawing.Pen> 建構函式的第二個引數中指定畫筆寬度：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 如果假設顯示裝置的水平方向每英吋有 96 個點，且其垂直方向每英吋有 96 個點，則上述範例的線條結束點會分別在三種座標空間中使用下列座標：  
  
|||  
|-|-|  
|World|\(0, 0\) 到 \(2, 1\)|  
|頁面|\(0, 0\) 到 \(2, 1\)|  
|裝置|\(0, 0\) 到 \(192, 96\)|  
  
 請注意，由於全局座標空間的原點位於工作區的左上角，因此畫面座標和全局座標是相同的。  
  
 您可以結合全局和畫面轉換來達到各種效果。  例如，假設您想要使用英吋做為度量單位，而且想要您的座標系統的原點位於工作區左邊緣的 2 英吋和工作區頂端的 1\/2 英吋處。  下列範例將設定 <xref:System.Drawing.Graphics> 物件的全局轉換和畫面轉換，然後從 \(0, 0\) 到 \(2, 1\) 繪製出一條線：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 下列圖示將顯示該線條和座標系統。  
  
 ![座標系統](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.png "AboutGdip05\_art03")  
  
 如果假設顯示裝置的水平方向每英吋有 96 個點，且其垂直方向每英吋有 96 個點，則上述範例的線條結束點會分別在三種座標空間中使用下列座標：  
  
|||  
|-|-|  
|World|\(0, 0\) 到 \(2, 1\)|  
|頁面|\(2, 0.5\) 到 \(4, 1.5\)|  
|裝置|\(192, 48\) 到 \(384, 144\)|  
  
## 請參閱  
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [以矩陣來表示轉換](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)