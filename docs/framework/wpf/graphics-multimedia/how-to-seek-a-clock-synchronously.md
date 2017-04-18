---
title: "如何：同步搜尋時鐘 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "時鐘, 同步搜尋"
  - "同步搜尋時鐘"
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：同步搜尋時鐘
使用 <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> 方法同步搜尋時鐘的特定點。  下列範例同時示範 <xref:System.Windows.Media.Animation.ClockController> 的 <xref:System.Windows.Media.Animation.ClockController.Seek%2A> 和 <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> 方法。  
  
 本範例顯示如何搜尋 <xref:System.Windows.Media.Animation.Clock>，如需顯示如何搜尋腳本的範例，請參閱 [同步搜尋腳本](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)。  
  
## 範例  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]