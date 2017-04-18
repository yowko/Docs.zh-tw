---
title: "使用巢狀圖形容器 | Microsoft Docs"
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
  - "圖形 [Windows Form], 裁剪"
  - "圖形, 巢狀容器"
  - "圖形, 在巢狀物件中轉換"
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 使用巢狀圖形容器
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供的容器可用來暫時取代或擴大 <xref:System.Drawing.Graphics> 物件中的部分狀態。  建立容器的方式是呼叫 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.BeginContainer%2A> 方法。  您可以重複呼叫 <xref:System.Drawing.Graphics.BeginContainer%2A>，便可形成巢狀容器。  每一次呼叫 <xref:System.Drawing.Graphics.BeginContainer%2A> 都必須搭配呼叫 <xref:System.Drawing.Graphics.EndContainer%2A>。  
  
## 巢狀容器中的轉換  
 下列範例建立 <xref:System.Drawing.Graphics> 物件和該 <xref:System.Drawing.Graphics> 物件中的容器。  <xref:System.Drawing.Graphics> 物件的全局轉換是 x 方向轉換 100 個單位和 y 方向轉換 80 個單位。  容器的全局轉換是 30 度旋轉。  程式碼會呼叫兩次 `DrawRectangle(pen, -60, -30, 120, 60)` 。  第一次呼叫 <xref:System.Drawing.Graphics.DrawRectangle%2A> 是在容器內；也就是說，這個呼叫是在 <xref:System.Drawing.Graphics.BeginContainer%2A> 和 <xref:System.Drawing.Graphics.EndContainer%2A> 兩個呼叫之間。  第二次呼叫 <xref:System.Drawing.Graphics.DrawRectangle%2A> 則是在呼叫 <xref:System.Drawing.Graphics.EndContainer%2A> 之後。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 在上述程式碼中，從容器內部繪製的矩形會先根據容器的全局轉換 \(旋轉\)，再根據 <xref:System.Drawing.Graphics> 物件的全局轉換 \(轉換\) 來轉換。  從容器外部繪製的矩形則只會根據 <xref:System.Drawing.Graphics> 物件的全局轉換 \(轉換\) 來轉換。  下圖顯示的是兩個矩形。  
  
 ![巢狀容器](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## 在巢狀容器中裁剪  
 下列範例將說明巢狀容器如何處理裁剪區域。  程式碼會建立 <xref:System.Drawing.Graphics> 物件和該 <xref:System.Drawing.Graphics> 物件中的容器。  <xref:System.Drawing.Graphics> 物件的裁剪區域是矩形，而容器的裁剪區域則是橢圓形。  程式碼會呼叫兩次 <xref:System.Drawing.Graphics.DrawLine%2A> 方法。  第一次呼叫 <xref:System.Drawing.Graphics.DrawLine%2A> 是在容器內，而第二次呼叫 <xref:System.Drawing.Graphics.DrawLine%2A> 則是在容器外 \(在呼叫 <xref:System.Drawing.Graphics.EndContainer%2A> 之後\)。  第一行會根據兩個裁剪區域的交集來裁剪，  第二行則只會根據 <xref:System.Drawing.Graphics> 物件的矩形裁剪區域來裁剪。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 下圖顯示的是兩條裁剪的線條。  
  
 ![巢狀容器](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 如上述兩個範例所示，在巢狀容器中的轉換和裁剪區域都是累積的。  如果設定容器和 <xref:System.Drawing.Graphics> 物件的全局轉換，這兩種轉換都將套用至從容器內部繪製的項目。  容器的轉換會先套用，然後再套用 <xref:System.Drawing.Graphics> 物件的轉換。  如果設定容器和 <xref:System.Drawing.Graphics> 物件的裁剪區域，則會根據兩個裁剪區域的交集來裁剪從容器內部繪製的項目。  
  
## 巢狀容器中的品質設定  
 巢狀容器中的品質設定 \(<xref:System.Drawing.Graphics.SmoothingMode%2A>、<xref:System.Drawing.Graphics.TextRenderingHint%2A> 等等\) 不會累積；相反地，容器的品質設定會暫時取代 <xref:System.Drawing.Graphics> 物件的品質設定。  當您建立新的容器時，該容器的品質設定會設定為預設值。  例如，假設您有一個平滑化模式為 <xref:System.Drawing.Drawing2D.SmoothingMode> 的 <xref:System.Drawing.Graphics> 物件。  當您建立容器時，容器內部的平滑化模式就是預設的平滑化模式。  您可以任意設定容器的平滑化模式，從容器內部繪製的任何項目都將根據您所設定的模式來進行繪製。  在呼叫 <xref:System.Drawing.Graphics.EndContainer%2A> 之後所繪製的項目將會根據呼叫 <xref:System.Drawing.Graphics.BeginContainer%2A> 之前的平滑化模式 \(<xref:System.Drawing.Drawing2D.SmoothingMode>\) 來進行繪製。  
  
## 巢狀容器中的幾個圖層  
 您並不受限於 <xref:System.Drawing.Graphics> 物件中只能有一個容器。  您可以建立一連串容器，每一個容器都是套疊於前一個容器內，而且可以為每一個巢狀容器指定全局轉換、裁剪區域和品質設定。  如果您從最內層的容器呼叫繪圖方法，轉換將會從最內層的容器依序套用到最外層的容器。  從最內層的容器繪製的項目將根據所有製剪區域的交集來進行裁剪。  
  
 下列範例建立 <xref:System.Drawing.Graphics> 物件，並將它的文字呈現提示設定為 <xref:System.Drawing.Drawing2D.SmoothingMode>。  程式碼會建立兩個容器，一個套疊於另一個。  外部容器的文字呈現提示是設定為 <xref:System.Drawing.Text.TextRenderingHint>，而內部容器的文字呈現提示則是設定為 <xref:System.Drawing.Drawing2D.SmoothingMode>。  這個程式碼繪製三個字串：一個從內部容器、一個從外部容器，另一個從 <xref:System.Drawing.Graphics> 物件本身。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 下圖顯示的是三個字串。  從內部容器和從 <xref:System.Drawing.Graphics> 物件繪製的字串會由反鋸齒功能平滑化。  從外部容器繪製的字串則不會以反鋸齒功能平滑化，原因是 <xref:System.Drawing.Graphics.TextRenderingHint%2A> 屬性已設定為 <xref:System.Drawing.Text.TextRenderingHint>。  
  
 ![巢狀容器](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## 請參閱  
 <xref:System.Drawing.Graphics>   
 [管理圖形物件的狀態](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)