---
title: "如何：列出已安裝的編碼器 | Microsoft Docs"
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
  - "影像轉碼器, 列出"
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：列出已安裝的編碼器
您可能會想要列出電腦上可用的影像編碼器，以判斷應用程式是否能夠儲存特定的影像檔案格式。  <xref:System.Drawing.Imaging.ImageCodecInfo> 類別提供 <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> 靜態方法，讓您能夠判斷可用的影像編碼器。  <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> 會傳回 <xref:System.Drawing.Imaging.ImageCodecInfo> 物件的陣列。  
  
## 範例  
 下列程式碼範例會輸出已安裝之編碼器及其屬性值的清單。  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   Windows Form 應用程式。  
  
-   <xref:System.Windows.Forms.PaintEventArgs>，是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## 請參閱  
 [如何：列出已安裝的解碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)   
 [使用 Managed GDI\+ 中的影像編碼器和解碼器](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)