---
title: "如何：使用區域的使用點擊測試 | Microsoft Docs"
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
  - "點擊測試, 使用區域"
  - "區域, 點擊測試"
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用區域的使用點擊測試
點擊測試的目的是要決定游標是否已移到指定的物件上方，例如圖示或按鈕。  
  
## 範例  
 下列範例會藉由形成兩個矩形區域的聯集，來建立加號形狀的區域。  假設變數 `point` 保留最近按下的位置。  程式碼會檢查 `point` 是否位於加號形狀的區域。  如果 Point 是在這個區域中 \(命中\)，會將該區域填滿不透明的紅色筆刷；  否則，會將該區域填滿半透明的紅色筆刷。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## 編譯程式碼  
 前述範例是專為與 Windows Form 搭配使用而設計的，而且它需要有 <xref:System.Windows.Forms.PaintEventArgs> `e` \(這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 <xref:System.Drawing.Region>   
 [GDI\+ 中的區域](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)   
 [如何：使用區域的裁剪](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)