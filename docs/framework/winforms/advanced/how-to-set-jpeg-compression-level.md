---
title: "如何：設定 JPEG 壓縮層級 | Microsoft Docs"
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
  - "影像 [Windows Form], 變更編碼器參數"
  - "JPEG 影像, 設定品質等級"
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：設定 JPEG 壓縮層級
當您將影像儲存至磁碟時，您可能會想要修改影像的參數，將檔案的大小最小化或改善其品質。  您可以修改壓縮品質，調整 JPEG 影像的品質。  若要在儲存 JPEG 影像時指定壓縮品質，就必須建立 <xref:System.Drawing.Imaging.EncoderParameters> 物件，然後將其傳遞至 <xref:System.Drawing.Image> 類別的 <xref:System.Drawing.Image.Save%2A> 方法。  初始化 <xref:System.Drawing.Imaging.EncoderParameters> 物件，使其擁有由 <xref:System.Drawing.Imaging.EncoderParameter> 所組成的陣列。  當您建立 <xref:System.Drawing.Imaging.EncoderParameter> 時，請指定 <xref:System.Drawing.Imaging.Encoder.Quality> 編碼器以及所需的壓縮品質。  
  
## 範例  
 下列範例程式碼會建立 <xref:System.Drawing.Imaging.EncoderParameter> 物件，並儲存三個 JPEG 影像。  每個 JPEG 影像會藉由修改傳遞至 <xref:System.Drawing.Imaging.EncoderParameter> 建構函式的 `long` 值，以不同的品質等級儲存。  品質等級 0 會對應至最大的壓縮率，而品質等級 100 則對應至最小的壓縮率。  
  
 [!code-csharp[UsingImageEncodersDecoders#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#8)]
 [!code-vb[UsingImageEncodersDecoders#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#8)]  
[!code-csharp[UsingImageEncodersDecoders#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#6)]
[!code-vb[UsingImageEncodersDecoders#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#6)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   Windows Form 應用程式。  
  
-   <xref:System.Windows.Forms.PaintEventArgs>，是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
-   名為 `TestPhoto.jpg` 的影像檔，並且位於 **c:\\**。  
  
## 請參閱  
 [如何：判斷編碼器所支援的參數](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)   
 [點陣圖類型](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)   
 [使用 Managed GDI\+ 中的影像編碼器和解碼器](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)