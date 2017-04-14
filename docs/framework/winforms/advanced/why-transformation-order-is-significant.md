---
title: "為何轉換順序很重要 | Microsoft Docs"
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
  - "轉換, 順序的重要性"
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 為何轉換順序很重要
單一的 <xref:System.Drawing.Drawing2D.Matrix> 物件可儲存單一轉換或一系列轉換。  後者稱為複合轉換。  複合轉換矩陣的取得方式是乘以個別轉換的矩陣。  
  
## 複合轉換範例  
 在複合轉換中，個別轉換的順序非常重要。  例如，如果先旋轉、再縮放，然後平移，則取得的結果會與先平移、再旋轉，然後縮放的結果不同。  在 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 中，複合轉換是從左到右建置。  假設 S、R 和 T 依次代表縮放、旋轉和轉換矩陣，則 SRT \(依此順序\) 的結果是先縮放、再旋轉，然後轉換所產生的複合轉換矩陣。  SRT 產生的矩陣和 TRS 產生的矩陣不同。  
  
 順序很重要的原因之一是，旋轉和縮放這類的轉換是根據座標系統的原點來進行。  縮放中心位於原點的物件所產生的結果，與縮放已從原點移開的物件不同。  同樣地，旋轉中心位於原點的物件所產生的結果，也會與旋轉已從原點移開的物件不同。  
  
 下列範例組合了縮放、旋轉和轉換 \(依此順序\)，形成複合轉換。  傳遞至 <xref:System.Drawing.Graphics.RotateTransform%2A> 方法的 <xref:System.Drawing.Drawing2D.MatrixOrder> 引數指出旋轉將在縮放之後進行。  同樣地，傳遞至 <xref:System.Drawing.Drawing2D.MatrixOrder> 方法的 <xref:System.Drawing.Graphics.TranslateTransform%2A> 引數會指出轉換將在旋轉之後進行。  <xref:System.Drawing.Drawing2D.MatrixOrder> 和 <xref:System.Drawing.Drawing2D.MatrixOrder> 是 <xref:System.Drawing.Drawing2D.MatrixOrder> 列舉的成員。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 下列範例會進行和上述範例中相同的呼叫，只不過順序顛倒。  最後的作業順序為先轉換、再旋轉，然後縮放，產生的結果和先縮放、再旋轉，然後轉換的結果完全不同。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 使複合轉換中個別轉換的順序顛倒的方式之一，就是將一系列方法呼叫的順序顛倒。  控制作業順序的第二種方式是變更矩陣順序引數。  下列的範例與上述範例相同，除了 <xref:System.Drawing.Drawing2D.MatrixOrder> 已變更為 <xref:System.Drawing.Drawing2D.MatrixOrder> 以外。  矩陣乘法是依照 SRT 的順序，此處的 S、R 和 T 分別是指縮放、旋轉和轉換的矩陣。  複合轉換的順序是先縮放、再旋轉，然後轉換。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 最後這個範例的結果與這個主題中的第一個範例相同。  這是因為我們同時將方法呼叫的順序和矩陣乘法的順序都顛倒了。  
  
## 請參閱  
 <xref:System.Drawing.Drawing2D.Matrix>   
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [使用 Managed GDI\+ 中的轉換](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)