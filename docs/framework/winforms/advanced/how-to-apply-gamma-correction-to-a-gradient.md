---
title: "如何：將 Gamma 修正套用至漸層 | Microsoft Docs"
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
  - "漸層筆刷, Gamma 修正"
  - "漸層, Gamma 修正"
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：將 Gamma 修正套用至漸層
您可以將筆刷的 <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> 屬性設定為 `true`，即可啟用線形漸層筆刷的 Gamma 修正。  將 <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> 屬性設定為 `false`，即可停用 Gamma 修正。  依照預設，Gamma 修正為停用狀態。  
  
## 範例  
 下列範例建立線形漸層筆刷，並使用該筆刷填滿兩個矩形。  填滿第一個矩形時不使用 Gamma 修正，填滿第二個矩形時則會使用 Gamma 修正。  
  
 下圖顯示的是兩個已填滿的矩形。  上面的矩形沒有 Gamma 修正，中間顯示為暗色，  下面的矩形有 Gamma 修正，顯示的濃度較為一致。  
  
 ![漸層](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>   
 [使用漸層筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)