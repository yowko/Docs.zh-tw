---
title: "如何：將曲線路徑簡維為線條 | Microsoft Docs"
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
  - "曲線, 簡維"
  - "繪製, 扁平化曲線"
  - "Flatten 方法"
  - "圖形, 扁平化曲線至直線"
  - "GraphicsPath 物件"
  - "路徑, 簡維"
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：將曲線路徑簡維為線條
<xref:System.Drawing.Drawing2D.GraphicsPath> 物件儲存線條和貝茲曲線的序列。  您可以將數種不同曲線類型 \(橢圓形、弧形、基本曲線\) 加至路徑中，但是在每一種曲線儲存於路徑之前都會轉換為貝茲曲線。  將路徑簡維化是指將路徑中的每個貝茲曲線都轉換成一直線序列。  下圖將顯示簡維化之前及之後的路徑。  
  
 ![直線和曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.png "AboutGdip02\_Art32A")  
  
### 若要簡維路徑  
  
-   呼叫 <xref:System.Drawing.Drawing2D.GraphicsPath> 物件的 <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> 方法。  <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> 方法會接收一個扁平度引數，此引數指定簡維路徑和原始路徑之間最大距離。  
  
## 請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)