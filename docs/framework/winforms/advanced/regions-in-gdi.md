---
title: "GDI+ 中的區域 | Microsoft Docs"
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
  - "繪製, 區域"
  - "GDI+, 區域"
  - "區域"
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# GDI+ 中的區域
區域是指輸出裝置的顯示區域的某個部分。  區域可以是簡單區域 \(單一矩形\) 或複雜區域 \(多邊形和封閉型區線的組合\)。  下圖顯示兩個區域：一個是從矩形建構的，另一個是從路徑建構的。  
  
 ![區域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.png "AboutGdip02\_Art27")  
  
## 使用區域  
 通常區域用來裁剪 \(Clipping\) 和進行點擊測試 \(Hit Testing\)。  裁剪包括限制對顯示區域的某個特定區域進行繪製，通常該區域為必須進行更新的部分。  點擊測試包括檢查並判斷當按下滑鼠按鈕時，游標是否位於螢幕的某個特定區域中。  
  
 您可以從矩形或路徑建立區域。  您也可以透過結合現有的區域來建立複雜的區域。  <xref:System.Drawing.Region> 類別提供下列用來結合區域的方法：<xref:System.Drawing.Region.Intersect%2A>、<xref:System.Drawing.Region.Union%2A>、<xref:System.Drawing.Region.Xor%2A>、<xref:System.Drawing.Region.Exclude%2A> 和 <xref:System.Drawing.Region.Complement%2A>。  
  
 兩個區域的交集是指隸屬於這兩個區域的所有點的組合。  聯集是指屬於其中一個或兩個區域的所有點的組合。  區域的補數 \(Complement\) 是指所有區域以外的點。  下圖將顯示前圖所說明的兩個區域的交集和聯集。  
  
 ![區域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02\_Art28")  
  
 套用到區域組的 <xref:System.Drawing.Region.Xor%2A> 方法會產生一個區域，其中含有隸屬於其中一個區域 \(而非兩個\) 的所有點。  套用到區域組合的 <xref:System.Drawing.Region.Exclude%2A> 方法會產生一個區域，其中含有第一個區域中但位於第二個區域以外的所有點。  下圖將顯示因套用 <xref:System.Drawing.Region.Xor%2A> 和 <xref:System.Drawing.Region.Exclude%2A> 方法到本主題一開始所說明的兩個區域時，所產生的區域。  
  
 ![區域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.png "AboutGdip02\_Art29")  
  
 若要繪製區域，您需要 <xref:System.Drawing.Graphics> 物件、<xref:System.Drawing.Brush> 物件和 <xref:System.Drawing.Region> 物件。  <xref:System.Drawing.Graphics> 物件提供 <xref:System.Drawing.Graphics.FillRegion%2A> 方法，而 <xref:System.Drawing.Brush> 物件則是儲存填入的特性，例如色彩或圖樣。  下列範例將純色填入區域中：  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## 請參閱  
 <xref:System.Drawing.Region?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [使用區域](../../../../docs/framework/winforms/advanced/using-regions.md)