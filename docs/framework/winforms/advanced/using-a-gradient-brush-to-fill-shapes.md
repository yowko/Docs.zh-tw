---
title: "使用漸層筆刷填滿形狀 | Microsoft Docs"
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
  - "筆刷, 漸層筆刷"
  - "範例 [Windows Form], 漸層筆刷"
  - "漸層筆刷"
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 使用漸層筆刷填滿形狀
您可以使用漸層筆刷，以逐漸變更的色彩來填滿形狀。  例如，您可以使用水平漸層，以隨著您從形狀左邊緣移動到右邊緣時逐漸變更的色彩來填滿形狀。  假設有一個矩形，左邊緣是黑色的 \(以 0、0、0 來表示紅色、綠色和藍色元素\)，右邊緣是紅色的 \(以 255、0、0 來表示\)。  如果矩形的寬度為 256 個像素，某個像素的紅色元素將會比它左邊像素的紅色元素大。  一列中最左邊像素的紅色元素為 \(0, 0, 0\)，第二個像素為 \(1, 0, 0\)，第三個像素為 \(2, 0, 0\)，依此類推，最右邊像素的紅色元素為 \(255, 0, 0\)。  這些內插的色彩值即組成色彩漸層。  
  
 線形漸層會隨著您水平、垂直或與指定斜線成平行方向移動而變更色彩。  路徑漸層則會隨著您在路徑內部和界限上移動時而變更色彩。  您可以自訂路徑漸層來達到不同的效果。  
  
 下圖顯示的是使用線形漸層筆刷填滿的矩形和使用路徑漸層筆刷填滿的橢圓形。  
  
 ![漸層](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## 在本節中  
 [如何：建立線形漸層](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 示範如何使用 <xref:System.Drawing.Drawing2D.LinearGradientBrush> 類別建立線形漸層。  
  
 [如何：建立路徑漸層](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 說明如何使用 <xref:System.Drawing.Drawing2D.PathGradientBrush> 類別建立路徑漸層。  
  
 [如何：將 Gamma 修正套用至漸層](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 解說如何搭配漸層筆刷使用 Gamma 修正。  
  
## 參考  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=fullName>  
 不僅描述這個類別，並且提供連至它所有成員的連結。  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=fullName>  
 不僅描述這個類別，並且提供連至它所有成員的連結。