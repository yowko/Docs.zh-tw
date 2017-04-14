---
title: "使用全局轉換 | Microsoft Docs"
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
  - "圖形, 全局轉換"
  - "全局轉換, 範例"
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 使用全局轉換
全局轉換是 <xref:System.Drawing.Graphics> 類別的屬性。  指定全局轉換的數字是儲存在 <xref:System.Drawing.Drawing2D.Matrix> 物件中，這個物件代表 3×3 的矩陣。  <xref:System.Drawing.Drawing2D.Matrix> 和 <xref:System.Drawing.Graphics> 類別提供了幾個方法，可用來設定全局轉換矩陣中的數字。  
  
## 不同類型的轉換  
 在下列範例中，程式碼會先建立 50×50 的矩形，並將它放在原點 \(0, 0\)。  原點是指工作區 \(Client Area\) 左下角的位置。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 下列程式碼會套用縮放轉換，將矩形的 x 方向以 1.75 因數放大，將矩形的 y 方向以 0.5 因數縮小：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 產生矩形的 x 方向比原始矩形長，y 方向則比原始矩形短。  
  
 若要旋轉矩形，而非縮放矩形，請使用下列程式碼：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 若要轉換矩形，請使用下列程式碼：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## 請參閱  
 <xref:System.Drawing.Drawing2D.Matrix>   
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [使用 Managed GDI\+ 中的轉換](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)