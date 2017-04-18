---
title: "如何：在執行階段時建立點陣圖 | Microsoft Docs"
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
  - "點陣圖, 建立"
  - "點陣圖, 範例 [Visual Basic]"
ms.assetid: 737bae30-e599-4e1d-bf30-bab8280b32be
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：在執行階段時建立點陣圖
這個範例會建立 <xref:System.Drawing.Bitmap> 物件並在其中描繪，然後在現有的 Windows Form <xref:System.Windows.Forms.PictureBox> 控制項中顯示該物件。  
  
## 範例  
 [!code-csharp[System.Drawing.CreateBitmapAtRuntime#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CreateBitmapAtRuntime/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.CreateBitmapAtRuntime#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CreateBitmapAtRuntime/VB/Form1.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   匯入 System、System.Drawing 和 System.Windows.Forms 組件的 Windows Form。  
  
## 請參閱  
 <xref:System.Drawing.Bitmap>   
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)