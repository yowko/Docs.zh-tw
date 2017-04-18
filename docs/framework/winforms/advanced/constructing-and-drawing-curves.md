---
title: "建構和繪製曲線 | Microsoft Docs"
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
  - "曲線, 繪製"
  - "繪製, 曲線"
  - "範例 [Windows Form], 繪製曲線"
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 建構和繪製曲線
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可支援幾種曲線類型：橢圓形、弧形、基本曲線和貝茲曲線。  橢圓形是根據它的週框 \(Bounding Rectangle\) 來定義；弧形是橢圓形的一部分，根據起點角度和散出角度 \(Sweep Angle\) 來定義。  基本曲線是由點陣列和伸張值參數所定義；曲線在陣列中平滑通過每個點，而且伸張值參數會影響曲線的彎曲方式。  貝茲曲線是由兩個端點和兩個控制點所定義；曲線並不通過控制點，但控制點會在曲線從一個端點到另一個端點時影響方向和彎曲方式。  
  
## 在本節中  
 [如何：繪製基本曲線](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 說明基本曲線以及如何繪製基本曲線。  
  
 [如何：繪製單一貝茲曲線](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 說明貝茲曲線以及如何繪製貝茲曲線。  
  
 [如何：繪製一連串的貝茲曲線](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 解說如何依序繪製數條貝茲曲線。