---
title: "雙重緩衝的使用 | Microsoft Docs"
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
  - "緩衝, 雙重緩衝"
  - "雙重緩衝"
  - "重繪閃動, 在 Windows Form 中減少"
  - "圖形, 雙重緩衝"
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 雙重緩衝的使用
您可以使用雙重緩衝以減少包含複雜繪製作業之應用程式中的重繪閃動。  .NET Framework 包含內建的雙重緩衝支援，您也可以手動管理和呈現圖形。  
  
## 在本節中  
 [雙重緩衝的圖形](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 介紹雙重緩衝概念並概述 .NET Framework 支援。  
  
 [如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 示範如何使用 .NET Framework 中的預設雙重緩衝支援。  
  
 [如何：手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 示範如何管理應用程式中的雙重緩衝。  
  
 [如何：手動呈現已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 示範如何呈現雙重緩衝的圖形。  
  
## 參考  
 <xref:System.Windows.Forms.Control.SetStyle%2A> ,  
 控制啟用雙重緩衝 \(Double Buffering\) 的方法。  
  
 <xref:System.Drawing.BufferedGraphicsContext> ,  
 提供建立圖形緩衝的方法。  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 提供存取應用程式定義域的緩衝圖形內容。