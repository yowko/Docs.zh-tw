---
title: "如何：旋轉、反射和傾斜影像 | Microsoft Docs"
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
  - "影像 [Windows Form], 反映"
  - "影像 [Windows Form], 旋轉"
  - "影像 [Windows Form], 扭曲"
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：旋轉、反射和傾斜影像
您可以指定原始影像左上角、右上角和左下角的目的座標位置，即可旋轉、反射和傾斜影像。  這三個目的座標位置會決定原始的矩形影像對應至平形四邊形的仿射轉換。  
  
## 範例  
 例如，假設原始影像是左上角位於 \(0, 0\)、右上角位於 \(100, 0\) 和左下角位於 \(0, 50\) 的矩形。  現在，假設要依照下列方式，將這三個點對應至目的座標位置。  
  
|原始座標位置|目的座標位置|  
|------------|------------|  
|左上角 \(0, 0\)|\(200, 20\)|  
|右上角 \(100, 0\)|\(110, 100\)|  
|左下角 \(0, 50\)|\(250, 30\)|  
  
 下圖顯示的是原始的影像和對應至平形四邊形的影像。  原始影像已經過傾斜、反射、旋轉和轉換。  原始影像上邊緣的 X 軸會對應至連接 \(200, 20\) 和 \(110, 100\) 的線條。  原始影像左邊緣的 Y 軸則會對應至連接 \(200, 20\) 和 \(250, 30\) 的線條。  
  
 ![Stripes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")  
  
 下圖顯示的是套用於相片影像的類似轉換。  
  
 ![轉換的 Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")  
  
 下圖顯示的是套用於中繼檔的類似轉換。  
  
 ![轉換的中繼檔](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")  
  
 下列範例會產生第一個圖中所顯示的影像。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  請確定以系統中有效的影像路徑來取代 `Stripes.bmp`。  
  
## 請參閱  
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)