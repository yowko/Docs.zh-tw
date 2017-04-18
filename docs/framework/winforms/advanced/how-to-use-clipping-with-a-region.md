---
title: "如何：使用區域的裁剪 | Microsoft Docs"
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
  - "區域, 裁剪"
  - "區域, 限制繪圖介面"
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用區域的裁剪
<xref:System.Drawing.Graphics> 類別的其中一個屬性就是裁剪區域 \(Clip Region\)。  由指定 <xref:System.Drawing.Graphics> 物件進行的所有繪製工作都限定只能在該 <xref:System.Drawing.Graphics> 物件的裁剪區域中。  您可以藉由呼叫 <xref:System.Drawing.Graphics.SetClip%2A> 方法來設定裁剪區域。  
  
## 範例  
 下列範例會建構只包含單一多邊形的路徑。  然後程式碼會根據這個路徑來建構區域。  這個區域會傳遞至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.SetClip%2A> 方法，然後繪製兩個字串。  
  
 下圖顯示的是裁剪的字串。  
  
 ![裁剪](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## 編譯程式碼  
 前述範例是專為與 Windows Form 搭配使用而設計的，而且它需要有 <xref:System.Windows.Forms.PaintEventArgs> `e` \(這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 [GDI\+ 中的區域](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)   
 [使用區域](../../../../docs/framework/winforms/advanced/using-regions.md)