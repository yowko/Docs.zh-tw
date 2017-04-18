---
title: "如何：使用影像材質填滿圖案 | Microsoft Docs"
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
  - "點陣圖 [Windows Form], 使用紋理"
  - "影像 [Windows Form], 與筆刷一起使用"
  - "圖案, 填滿影像"
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用影像材質填滿圖案
您可以使用 <xref:System.Drawing.Image> 類別和 <xref:System.Drawing.TextureBrush> 類別，即可使用材質填滿一個圖案。  
  
## 範例  
 下列範例會使用影像填滿橢圓形。  程式碼會建構 <xref:System.Drawing.Image> 物件，然後將 <xref:System.Drawing.Image> 物件的位址當成引數傳遞至 <xref:System.Drawing.TextureBrush.%23ctor%2A> 建構函式。  第三個陳述式會縮放影像，而第四個陳述式則會以縮放影像的重複複本填滿橢圓形。  
  
 在下列程式碼中，<xref:System.Drawing.TextureBrush.Transform%2A> 屬性包含在繪製前套用於影像的轉換。  假設原始影像的寬度為 640 個像素，高度為 480 個像素。  轉換會藉由設定水平和垂直縮放值，將影像縮小為 75×75。  
  
> [!NOTE]
>  在下列範例中，影像尺寸為 75×75，而橢圓形的大小為 150×250。  因為影像填滿的部分比橢圓形小，橢圓形會和影像並排顯示。  並排顯示是指以水平和垂直方向重複顯示影像，一直到圖案的邊界為止。  如需有關並排顯示的詳細資訊，請參閱 [如何：使用影像並排顯示圖案](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md)。  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)