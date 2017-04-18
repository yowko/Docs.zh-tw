---
title: "如何：建立縮圖影像 | Microsoft Docs"
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
  - "影像 [Windows Form], 建立縮圖"
  - "縮圖影像, 建立"
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 如何：建立縮圖影像
縮圖影像是影像的縮小版本。  您可以藉由呼叫 <xref:System.Drawing.Image> 物件的 <xref:System.Drawing.Image.GetThumbnailImage%2A> 方法來建立縮圖影像。  
  
## 範例  
 下列範例會從 JPG 檔案建構 <xref:System.Drawing.Image> 物件。  原始影像的寬度為 640 個像素，高度為 479 個像素。  程式碼會建立寬度為 100 個像素，高度為 100 個像素的縮圖影像。  
  
 下圖顯示的是縮圖影像。  
  
 ![縮圖影像](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  本範例會宣告一個回呼方法，但不會用到這個方法。  這支援所有 GDI\+ 版本。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  若要執行範例，請遵循下列步驟：  
  
1.  建立新的 Windows Form 應用程式。  
  
2.  將範例程式碼加入至表單。  
  
3.  為表單的 <xref:System.Windows.Forms.Control.Paint> 事件建立處理常式。  
  
4.  在 <xref:System.Windows.Forms.Control.Paint> 處理常式中，呼叫 `GetThumbnail` 方法並傳遞 `e` 給 <xref:System.Windows.Forms.PaintEventArgs>。  
  
5.  找出要用於製作縮圖的影像檔。  
  
6.  在 `GetThumbnail` 方法中，指定影像的路徑和檔案名稱。  
  
7.  按 F5 執行範例。  
  
     表單上隨即出現 100 x 100 的縮圖影像。  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)