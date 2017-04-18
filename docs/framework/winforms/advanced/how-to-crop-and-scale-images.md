---
title: "如何：裁剪和縮放影像 | Microsoft Docs"
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
  - "影像 [Windows Form], 裁剪"
  - "影像 [Windows Form], 縮放比例"
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：裁剪和縮放影像
<xref:System.Drawing.Graphics> 類別提供了幾個 <xref:System.Drawing.Graphics.DrawImage%2A> 方法，有些方法的來源和目的端矩形參數可用來裁切和縮放影像。  
  
## 範例  
 下列範例會從磁碟檔案 Apple.gif 建構 <xref:System.Drawing.Image> 物件。  程式碼會以原始大小來繪製整個蘋果影像。  接著，程式碼會呼叫 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawImage%2A> 方法，在大於原始蘋果影像的目的端矩形中繪製一部分蘋果影像。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> 方法會查看來源矩形，決定要繪製的蘋果部分，來源矩形是由第三、第四、第五和第六個引數來指定。  在這種情況下，會將蘋果的寬度裁切為 75%，高度也會裁切為 75%。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> 方法也會查看目的端矩形，決定繪製裁切蘋果的位置和裁切蘋果的大小，目的端矩形是由第二個引數來指定。  在這種情況下，目的端矩形的寬度會比原始影像寬 30%，長度也會比原始影像長 30%。  
  
 下圖顯示的是原始的蘋果以及縮放和裁切過的蘋果。  
  
 ![裁剪 & 縮放](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  請以系統中有效的影像檔名稱和路徑取代 `Apple.gif`。  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)