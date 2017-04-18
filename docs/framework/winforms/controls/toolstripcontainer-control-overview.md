---
title: "ToolStripContainer 控制項概觀 | Microsoft Docs"
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
  - "ToolStripContainer"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "工具列 [Windows Form], 內建浮動定位"
  - "ToolStripContainer 控制項 [Windows Form], 關於 ToolStripContainer 控制項"
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# ToolStripContainer 控制項概觀
<xref:System.Windows.Forms.ToolStripContainer> 在其上、下、左、右方都有面板，可以放置或浮動定位 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.StatusStrip> 控制項。  如果將多重 <xref:System.Windows.Forms.ToolStrip> 控制項放置在左邊或右邊的 <xref:System.Windows.Forms.ToolStripContainer>，這些控制項將會以垂直方式堆疊。  如果將它們放置在上方或下方的 <xref:System.Windows.Forms.ToolStripContainer>，這些控制項將會以水平方式堆疊。  您可以使用 <xref:System.Windows.Forms.ToolStripContainer> 的中央 <xref:System.Windows.Forms.ToolStripContentPanel>，將舊式控制項定位在表單上。  
  
 任何或所有 <xref:System.Windows.Forms.ToolStripContainer> 控制項直接在設計階段就是可選取的，同時也可以刪除。  <xref:System.Windows.Forms.ToolStripContainer> 的每個面板都是可擴充、可摺疊的，而且可使用其所包含的控制項來重新調整大小。  
  
### 重要 ToolStripContainer 成員  
  
|名稱|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|取得 <xref:System.Windows.Forms.ToolStripContainer> 的下方面板。|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|取得或設定值，指出是否可以看見 <xref:System.Windows.Forms.ToolStripContainer> 的下方面板。|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|取得 <xref:System.Windows.Forms.ToolStripContainer> 的左方面板。|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|取得或設定值，指出是否可以看見 <xref:System.Windows.Forms.ToolStripContainer> 的左方面板。|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|取得 <xref:System.Windows.Forms.ToolStripContainer> 的右方面板。|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|取得或設定值，指出是否可以看見 <xref:System.Windows.Forms.ToolStripContainer> 的右方面板。|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|取得 <xref:System.Windows.Forms.ToolStripContainer> 的上方面板。|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|取得或設定值，指出是否可以看見 <xref:System.Windows.Forms.ToolStripContainer> 的上方面板。|  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripContainer>   
 <xref:System.Windows.Forms.ToolStripContentPanel>