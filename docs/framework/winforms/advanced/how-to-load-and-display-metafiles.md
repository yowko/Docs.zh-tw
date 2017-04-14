---
title: "如何：載入和顯示中繼檔 | Microsoft Docs"
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
  - "範例 [Windows Form], 中繼檔"
  - "中繼檔, 顯示"
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：載入和顯示中繼檔
從 <xref:System.Drawing.Image> 類別繼承而來的 <xref:System.Drawing.Imaging.Metafile> 類別提供了記錄、顯示和檢查向量影像的方法。  
  
## 範例  
 若要將向量影像 \(中繼檔\) 顯示在螢幕上，需要有 <xref:System.Drawing.Imaging.Metafile> 物件和 <xref:System.Drawing.Graphics> 物件。  將檔案 \(或資料流\) 名稱傳遞至 <xref:System.Drawing.Imaging.Metafile> 建構函式。  在您建立 <xref:System.Drawing.Imaging.Metafile> 物件後，將 <xref:System.Drawing.Imaging.Metafile> 物件傳遞至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawImage%2A> 方法。  
  
 下列範例會從 EMF \(加強型中繼檔\) 檔案建立 <xref:System.Drawing.Imaging.Metafile> 物件，然後繪製左上角位於 \(60, 10\) 的影像：  
  
 下圖顯示的是在指定位置繪製的中繼檔 \(Metafile\)。  
  
 ![影像位置](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)