---
title: "如何：建立線形漸層 | Microsoft Docs"
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
  - "色彩, 建立線形漸層"
  - "漸層"
  - "漸層, 建立線形"
  - "線形漸層, 建立"
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：建立線形漸層
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了水平、垂直和對角線形漸層。  依照預設，線形漸層中的色彩會一致變更，  但是，您也可以自訂線形漸層，使色彩以不一致的方式變更。  
  
 下列範例會使用水平線形漸層筆刷來填滿直線、橢圓形和矩形。  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> 建構函式會接收四個引數：兩個點和兩個色彩。  第一個點 \(0, 10\) 和第一個色彩 \(紅色\) 關聯，第二個點 \(200, 10\) 和第二個色彩 \(藍色\) 關聯。  如同預期，從 \(0, 10\) 到 \(200, 10\) 繪製的直線會從紅色逐漸變成藍色。  
  
 在 \(50, 10\) 和 \(200, 10\) 這兩點中的 10 並不重要。  重點在於兩個點都有相同的第二座標，連接它們的直線是水平的。  當水平座標從 0 移到 200 時，橢圓形和矩形也會從紅色逐漸變成藍色。  
  
 下圖顯示的是直線、橢圓形和矩形。  請注意，當水平座標增加到 200 以上時，色彩漸層又會重複。  
  
 ![線性漸層](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")  
  
### 若要使用水平線形漸層  
  
-   請傳入不透明紅色和不透明藍色，分別做為第三和第四個引數。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 在上述範例中，當您從水平座標 0 移動到水平座標 200 時，色彩元素會呈線形變更。  例如，第一個座標介於 0 和 200 之間的點，它的藍色元素將會介於 0 和 255 之間。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可讓您調整色彩從漸層一端到另一端的改變方式。  假設您要根據下表，建立從黑色變成紅色的漸層筆刷。  
  
|水平座標|RGB 元件|  
|----------|------------|  
|0|\(0, 0, 0\)|  
|40|\(128, 0, 0\)|  
|200|\(255, 0, 0\)|  
  
 請注意，當水平座標為 0 到 200 之間的 20% 時，紅色元素的濃度只有一半。  
  
 下列範例會設定 <xref:System.Drawing.Drawing2D.LinearGradientBrush> 物件的 <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> 屬性，建立三個相關濃度與三個相關位置之間的關聯。  如同上述表格，相對濃度 0.5 和相關位置 0.2 關聯。  程式碼會使用漸層筆刷來填滿橢圓形和矩形。  
  
 下圖顯示的是產生的橢圓形和矩形。  
  
 ![線性漸層](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")  
  
### 若要自訂線形漸層  
  
-   請傳入不透明黑色和不透明紅色，分別做為第三和第四個引數。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 上述範例中的漸層都是水平漸層；也就是說，當您延著任何水平直線移動時，色彩便會逐漸變更。  您也可以定義垂直漸層和對角漸層。  
  
 下列範例會將 \(0, 0\) 和 \(200, 100\) 兩點傳遞至 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> 建構函式。  藍色和 \(0, 0\) 關聯，綠色和 \(200, 100\) 關聯。  直線 \(畫筆寬度為 10\) 和矩形會使用線形漸層筆刷填滿。  
  
 下圖顯示的是直線和橢圓形。  請注意，當您延著與通過 \(0, 0\) 和 \(200, 100\) 兩點的直線成平形方向的任何直線移動時，橢圓形中的色彩便會逐漸變更。  
  
 ![線性漸層](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")  
  
### 若要建立對角線形漸層  
  
-   請傳入不透明藍色和不透明綠色，分別做為第三和第四個引數。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## 請參閱  
 [使用漸層筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)