---
title: "如何：判斷編碼器所支援的參數 | Microsoft Docs"
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
  - "編碼器參數, 判斷支援"
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：判斷編碼器所支援的參數
您可以調整如品質與壓縮等級的影像參數，但是必須了解指定之影像編碼器所支援的參數。  <xref:System.Drawing.Image> 類別提供 <xref:System.Drawing.Image.GetEncoderParameterList%2A> 方法，讓您能夠判斷特定編碼器所支援的影像參數。  您可以以 GUID 指定編碼器。  <xref:System.Drawing.Image.GetEncoderParameterList%2A> 方法會傳回 <xref:System.Drawing.Imaging.EncoderParameter> 物件的陣列。  
  
## 範例  
 下列範例程式碼會輸出 JPEG 編碼器所支援的參數。  請使用 <xref:System.Drawing.Imaging.Encoder> 類別概觀中的參數分類清單與關聯的 GUID，判斷每個參數的分類。  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   Windows Form 應用程式。  
  
-   <xref:System.Windows.Forms.PaintEventArgs>，是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## 請參閱  
 [如何：列出已安裝的編碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)   
 [點陣圖類型](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)   
 [使用 Managed GDI\+ 中的影像編碼器和解碼器](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)