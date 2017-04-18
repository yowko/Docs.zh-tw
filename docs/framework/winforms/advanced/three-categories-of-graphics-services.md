---
title: "圖形服務的三個分類 | Microsoft Docs"
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
  - "2D 向量圖形"
  - "圖形, 分類"
  - "影像處理"
  - "印刷樣式"
  - "向量圖形"
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 圖形服務的三個分類
Windows Form 的圖形提供可分為三大分類：  
  
-   二維 \(2\-D\) 向量圖形  
  
-   影像處理  
  
-   印刷樣式  
  
## 2D 向量圖形  
 二維向量圖形是繪圖基本項目 \(例如線條、曲線和圖形\)，這些基本項目是由座標系統上的點集合所指定。  例如，直線是由直線的兩個端點來指定，而矩形是由提供矩形左上方位置的點和一組提供矩形寬度和高度的數值來指定。  簡單的路徑是由直線連接起來的點陣列指定。  貝茲曲線是由四個控制點所指定的複雜曲線。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供用以儲存基本項目相關資訊的類別和結構、用以儲存基本項目繪製方式相關資訊的類別以及實際進行繪製的類別。  例如，<xref:System.Drawing.Rectangle> 結構儲存矩形的位置和大小，而 <xref:System.Drawing.Pen> 類別儲存線條色彩、線條寬度和線條樣式的相關資訊，而 <xref:System.Drawing.Graphics> 類別則擁有繪製線條、矩形、路徑和其他圖形的方法。  另外同時還有好幾種 <xref:System.Drawing.Brush> 類別可儲存如何將封閉的圖形和路徑填滿色彩或圖樣的相關資訊。  
  
 您可以在中繼檔中記錄向量影像，該影像是一連串的圖形命令  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供 <xref:System.Drawing.Imaging.Metafile> 類別，以用於記錄、顯示和儲存中繼檔。  可以使用 <xref:System.Drawing.Imaging.MetafileHeader> 和 <xref:System.Drawing.Imaging.MetaHeader> 類別來檢查中繼檔標題中所儲存的資料。  
  
## 影像處理  
 有些圖片種類很難或無法使用向量圖形的技術來顯示。  例如，工具列按鈕上的圖片和顯示為圖示的圖片，便很難將它們指定為線條和曲線的集合。  如果要使用向量技巧來建立擁擠棒球場上所拍攝的高解析度數位化相片，甚至會更困難。  這種類型的影像會儲存為點陣圖，點陣圖是螢幕上代表每個點之色彩的數字陣列。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供 <xref:System.Drawing.Bitmap> 類別以顯示、管理和儲存點陣圖。  
  
## 印刷樣式  
 印刷樣式是各種字型、大小和樣式的文字顯示。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 為這項複雜的工作提供了擴充的支援。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 的其中一個新功能是子像素反鋸齒，可在 LCD 螢幕上提供文字更平滑的外觀。  
  
 此外，Windows Form 還提供選項，讓您可選擇使用 <xref:System.Windows.Forms.TextRenderer> 類別中的 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 功能來繪製文字。  
  
## 請參閱  
 [圖形概觀](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)   
 [關於 GDI\+ Managed 程式碼](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)   
 [使用 Managed 圖形類別](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)