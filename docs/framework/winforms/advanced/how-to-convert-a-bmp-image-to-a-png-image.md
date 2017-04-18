---
title: "如何：將 BMP 影像轉換為 PNG 影像 | Microsoft Docs"
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
  - "BMP 影像, 轉換為 PNG"
  - "影像格式, 之間轉換"
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：將 BMP 影像轉換為 PNG 影像
有時候，您想要從一個影像檔案格式轉換成另一個。  藉由呼叫 <xref:System.Drawing.Image> 類別的 <xref:System.Drawing.Image.Save%2A> 方法，並指定 <xref:System.Drawing.Imaging.ImageFormat> 為所需的影像檔案格式，您可以輕鬆地執行這項轉換。  
  
## 範例  
 下列範例會從類型載入 BMP 影像，並將影像儲存成 PNG 格式。  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   Windows Form 應用程式。  
  
-   `System.Drawing.Imaging` 命名空間的參考。  
  
## 請參閱  
 [如何：列出已安裝的編碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)   
 [使用 Managed GDI\+ 中的影像編碼器和解碼器](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)   
 [點陣圖類型](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)