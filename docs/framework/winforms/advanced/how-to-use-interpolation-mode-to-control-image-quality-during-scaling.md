---
title: "如何：縮放期間使用插補法模式控制影像品質 | Microsoft Docs"
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
  - "影像 [Windows Form], 控制品質"
  - "影像 [Windows Form], 縮放比例"
  - "插補模式, 控制影像品質"
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：縮放期間使用插補法模式控制影像品質
<xref:System.Drawing.Graphics> 物件的插補法模式會影響 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 縮放 \(延展和縮小\) 影像的方式。  <xref:System.Drawing.Drawing2D.InterpolationMode> 列舉型別定義了幾種插補法模式，下列清單顯示了其中幾種模式：  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
 若要延展影像，必須將原始影像中的每一個像素對應至較大影像中的像素群組。  若要縮小影像，則必須將原始影像中的像素群組對應至較小影像中的單一像素。  執行這些對應的演算法有效性會決定縮放影像的品質。  可產生較高品質縮放影像的演算法通常需要較長的處理時間。  在上述清單中，<xref:System.Drawing.Drawing2D.InterpolationMode> 是品質最低的模式，<xref:System.Drawing.Drawing2D.InterpolationMode> 則是品質最高的模式。  
  
 若要設定插補法模式，請指派 <xref:System.Drawing.Drawing2D.InterpolationMode> 列舉型別的成員之一至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.InterpolationMode%2A> 屬性。  
  
## 範例  
 下列範例會繪製影像，然後用三種不同的插補法模式來縮小影像：  
  
 下圖顯示的是原始影像和三個較小的影像。  
  
 ![具有各種插補設定的影像](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)