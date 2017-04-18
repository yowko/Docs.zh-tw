---
title: "如何：列出已安裝的解碼器 | Microsoft Docs"
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
  - "影像轉碼器, 列出"
  - "影像解碼器, 列出"
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：列出已安裝的解碼器
您可能會想要列出電腦上可用的影像解碼器，以判斷應用程式是否能夠讀取特定的影像檔案格式。  <xref:System.Drawing.Imaging.ImageCodecInfo> 類別提供 <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> 靜態方法，讓您能夠判斷可用的影像解碼器。  <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> 會傳回 <xref:System.Drawing.Imaging.ImageCodecInfo> 物件的陣列。  
  
## 範例  
 下列程式碼範例會輸出已安裝之解碼器及其屬性值的清單。  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   Windows Form 應用程式。  
  
-   <xref:System.Windows.Forms.PaintEventArgs>，是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## 請參閱  
 [如何：列出已安裝的編碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)   
 [使用 Managed GDI\+ 中的影像編碼器和解碼器](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)