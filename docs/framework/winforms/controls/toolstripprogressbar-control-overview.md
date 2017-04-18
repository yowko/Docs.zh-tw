---
title: "ToolStripProgressBar 控制項概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ToolStripProgressBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "進度控制項"
  - "工具列 [Windows Form], 進度列"
  - "ToolStripProgressBar 控制項 [Windows Form], 關於 ToolStripProgressBar 控制項"
ms.assetid: ec3ab522-5fe4-4b4d-a551-bc19e84f4774
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# ToolStripProgressBar 控制項概觀
<xref:System.Windows.Forms.ToolStripProgressBar> 結合了所有 <xref:System.Windows.Forms.ToolStrip> 控制項的呈垷和浮動定位功能，並加上其典型的處理序追蹤功能。  <xref:System.Windows.Forms.ToolStripProgressBar> 通常會裝載於 <xref:System.Windows.Forms.StatusStrip> 上，而比較少裝載於 <xref:System.Windows.Forms.ToolStrip>。  
  
 雖然 <xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代舊版的控制項並加入其他功能，不過，也可以選擇保留 <xref:System.Windows.Forms.ToolStripProgressBar>，以提供回溯相容性 \(Backward Compatibility\) 以及未來使用。  
  
### 重要 ToolStripProgressBar 成員  
  
|名稱|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.ToolStripProgressBar.MarqueeAnimationSpeed%2A>|取得或設定值，表示每一次 <xref:System.Windows.Forms.ProgressBarStyle> 顯示更新之間的延遲時間 \(以毫秒為單位\)。|  
|<xref:System.Windows.Forms.ProgressBar.Maximum%2A>|取得或設定為此 <xref:System.Windows.Forms.ToolStripProgressBar> 所定義的範圍上限。|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Minimum%2A>|取得或設定為此 <xref:System.Windows.Forms.ToolStripProgressBar> 所定義的範圍下限。|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Style%2A>|取得或設定 <xref:System.Windows.Forms.ToolStripProgressBar> 顯示作業進度的樣式。|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Value%2A>|取得或設定目前 <xref:System.Windows.Forms.ToolStripProgressBar> 的值。|  
|<xref:System.Windows.Forms.ToolStripProgressBar.PerformStep%2A>|根據 <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> 屬性所設定的量，在進度列上從目前位置前進到下一個位置。|  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripProgressBar>