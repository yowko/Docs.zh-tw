---
title: "ToolStrip 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "Toolstrip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "工具列 [Windows Form]"
  - "工具列 [Windows Form], Windows Form 的新功能"
  - "ToolStrip 控制項 [Windows Forms], 關於 ToolStrip 控制項"
  - "新功能 [Windows Form], 工具列"
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# ToolStrip 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.ToolStrip> 控制項及其相關類別提供通用架構，可用來組合使用者介面項目至工具列、狀態列和功能表中。  <xref:System.Windows.Forms.ToolStrip> 控制項可以提供豐富的設計階段體驗，包括就地啟動、就地編輯、自訂配置和浮動定位 \(此為工具列共用水平空間或垂直空間的功能\)。  
  
 雖然 <xref:System.Windows.Forms.ToolStrip> 控制項會取代舊版的控制項並加入其他功能，不過，也可以選擇保留 <xref:System.Windows.Forms.ToolBar>，以提供回溯相容性 \(Backward Compatibility\) 以及未來使用。  
  
## ToolStrip 控制項的功能  
 <xref:System.Windows.Forms.ToolStrip> 控制項的用途包括：  
  
-   呈現跨容器的通用使用者介面。  
  
-   建立可輕鬆自訂且經常使用的工具列，此工具列可支援進階使用者介面和配置功能，例如停駐、浮動定位、具有文字和影像的按鈕、下拉式按鈕、下拉式控制項、溢位按鈕以及 <xref:System.Windows.Forms.ToolStrip> 項目的執行階段重新排序。  
  
-   支援溢位和執行階段項目重新排序。  當 <xref:System.Windows.Forms.ToolStrip> 空間不足，無法顯示功能表項目時，溢位功能會將項目移至下拉式功能表。  
  
-   透過通用的呈現模型，支援作業系統的一般外觀和行為。  
  
-   以處理其他控制項事件的方式，來處理所有容器和被收納項目共同的事件。  
  
-   將項目從一個 <xref:System.Windows.Forms.ToolStrip> 拖曳到另一個，或者在同一個 <xref:System.Windows.Forms.ToolStrip> 內拖曳項目。  
  
-   使用 <xref:System.Windows.Forms.ToolStripDropDown> 中的進階配置來建立下拉式控制項和使用者介面型別編輯器。  
  
 使用 <xref:System.Windows.Forms.ToolStripControlHost> 類別來使用 <xref:System.Windows.Forms.ToolStrip> 上的其他控制項，並且取得這些控制項的 <xref:System.Windows.Forms.ToolStrip> 功能。  
  
 藉由使用 <xref:System.Windows.Forms.ToolStripRenderer>、<xref:System.Windows.Forms.ToolStripProfessionalRenderer> 和 <xref:System.Windows.Forms.ToolStripManager> 搭配 <xref:System.Windows.Forms.ToolStripRenderMode> 列舉型別和 <xref:System.Windows.Forms.ToolStripManagerRenderMode> 列舉型別，可以擴充功能並且修改外觀和行為。  
  
 <xref:System.Windows.Forms.ToolStrip> 控制項可隨意設定和延伸，它提供了許多屬性、方法和事件來自訂外觀和行為。  以下是部分值得注意的成員：  
  
### 重要 ToolStrip 成員  
  
|名稱|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|取得或設定 <xref:System.Windows.Forms.ToolStrip> 所停駐的父容器邊綠為何。|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|取得或設定值，指出拖放動作和項目重新排序是否由 <xref:System.Windows.Forms.ToolStrip> 類別處理。|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|取得或設定值，指出 <xref:System.Windows.Forms.ToolStrip> 如何配置其項目。|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|取得或設定 <xref:System.Windows.Forms.ToolStripItem> 是附加至 <xref:System.Windows.Forms.ToolStrip> 或 <xref:System.Windows.Forms.ToolStripOverflowButton> 上，或者它可在兩者之間浮動。|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|取得值，指出按一下 <xref:System.Windows.Forms.ToolStripItem> 時 <xref:System.Windows.Forms.ToolStripItem> 是否顯示下拉式清單中的其他項目。|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|取得 <xref:System.Windows.Forms.ToolStripItem>，它會在啟用溢位時做為 <xref:System.Windows.Forms.ToolStrip> 的溢位按鈕。|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|取得或設定 <xref:System.Windows.Forms.ToolStripRenderer>，它用於自訂 <xref:System.Windows.Forms.ToolStrip> 的外觀和行為 \(外觀和操作\)。|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|取得或設定套用至 <xref:System.Windows.Forms.ToolStrip> 的繪製樣式。|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|當 <xref:System.Windows.Forms.ToolStrip.Renderer%2A> 屬性發生變更時引發。|  
  
 透過使用數個附屬類別，可讓 <xref:System.Windows.Forms.ToolStrip> 控制項具有彈性。  以下是一些最值得注意的類別：  
  
### 重要 ToolStrip 附屬類別  
  
|名稱|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.MenuStrip>|取代並加入功能至 <xref:System.Windows.Forms.MainMenu> 類別。|  
|<xref:System.Windows.Forms.StatusStrip>|取代並加入功能至 <xref:System.Windows.Forms.StatusBar> 類別。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|取代並加入功能至 <xref:System.Windows.Forms.ContextMenu> 類別。|  
|<xref:System.Windows.Forms.ToolStripItem>|抽象基底類別，用於管理 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.ToolStripControlHost> 或 <xref:System.Windows.Forms.ToolStripDropDown> 中可包含的所有項目的事件和配置。|  
|<xref:System.Windows.Forms.ToolStripContainer>|在表單的各邊為容器提供面板，控制項就可在其中以各種方式排列。|  
|<xref:System.Windows.Forms.ToolStripRenderer>|處理 <xref:System.Windows.Forms.ToolStrip> 物件的繪製功能。|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|提供 Microsoft Office 樣式的外觀。|  
|<xref:System.Windows.Forms.ToolStripManager>|控制 <xref:System.Windows.Forms.ToolStrip> 的呈現和浮動定位，以及 <xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.ToolStripDropDownMenu> 和 <xref:System.Windows.Forms.ToolStripMenuItem> 物件的合併。|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|指定要套用至表單上多重 <xref:System.Windows.Forms.ToolStrip> 物件的繪製樣式 \(自訂、Windows XP 或 Microsoft Office Professional\)。|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|指定要套用至表單上某一個 <xref:System.Windows.Forms.ToolStrip> 物件的繪製樣式 \(自訂、Windows XP 或 Microsoft Office Professional\)。|  
|<xref:System.Windows.Forms.ToolStripControlHost>|裝載其他控制項，尤其是 <xref:System.Windows.Forms.ToolStrip> 控制項以及想取得 <xref:System.Windows.Forms.ToolStrip> 功能的控制項。|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|指定要在主要 <xref:System.Windows.Forms.ToolStrip> 上或在溢位 <xref:System.Windows.Forms.ToolStrip> 上配置 <xref:System.Windows.Forms.ToolStripItem>，或者兩者都不配置。|  
  
 如需詳細資訊，請參閱 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)和 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripDropDown>