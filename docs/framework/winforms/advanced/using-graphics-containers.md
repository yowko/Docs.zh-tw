---
title: "使用圖形容器 | Microsoft Docs"
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
  - "範例 [Windows Form], 圖形容器"
  - "圖形容器"
  - "圖形, 使用容器"
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 使用圖形容器
<xref:System.Drawing.Graphics> 物件會提供用來顯示向量影像、點陣影像和文字的方法，例如 <xref:System.Drawing.Graphics.DrawLine%2A>、<xref:System.Drawing.Graphics.DrawImage%2A> 和 <xref:System.Drawing.Graphics.DrawString%2A>。  <xref:System.Drawing.Graphics> 物件也具有幾個會影響繪製項目品質和方向的屬性。  例如，平滑化模式屬性會決定是否將反鋸齒功能套用於線條和曲線，而全局轉換屬性則會影響繪製項目的位置和旋轉。  
  
 <xref:System.Drawing.Graphics> 物件會和特定顯示裝置關聯。  當您使用 <xref:System.Drawing.Graphics> 物件在視窗中繪製時，<xref:System.Drawing.Graphics> 物件也會和該特定視窗關聯。  
  
 <xref:System.Drawing.Graphics> 物件可視為容器 \(Container\)，因為它保留了一組會影響繪圖的屬性，而且會連結到和裝置相關的資訊。  您可以藉由呼叫 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.BeginContainer%2A> 方法，在現有的 <xref:System.Drawing.Graphics> 物件中建立輔助容器。  
  
## 在本節中  
 [管理圖形物件的狀態](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 說明如何管理 <xref:System.Drawing.Graphics> 物件的品質設定、裁剪區域 \(Clipping Area\) 和轉換。  
  
 [使用巢狀圖形容器](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 示範如何使用容器以控制 <xref:System.Drawing.Graphics> 物件的狀態。