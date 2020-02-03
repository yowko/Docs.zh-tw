---
title: ToolStrip 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 931a6a0ea09f9b684b793c05cb1c3db8ee8fb7c7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741072"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.ToolStrip> 控制項和其相關聯的類別提供通用的架構，可將使用者介面專案與工具列、狀態列和功能表結合。 <xref:System.Windows.Forms.ToolStrip> 控制項提供豐富的設計階段經驗，包括就地啟用和編輯、自訂配置和浮動功能，這是工具列共用水準或垂直空間的能力。  
  
 雖然 <xref:System.Windows.Forms.ToolStrip> 會取代並新增舊版中的功能，但如果有需要，<xref:System.Windows.Forms.ToolBar> 會保留供回溯相容性及未來使用。  
  
## <a name="features-of-the-toolstrip-controls"></a>ToolStrip 控制項的功能  
 使用 <xref:System.Windows.Forms.ToolStrip> 控制項來執行下列動作：  
  
- 在容器之間呈現通用的使用者介面。  
  
- 建立可輕鬆自訂且常用的工具列，以支援「高級使用者介面」和「版面配置」功能，例如停駐、浮動、具有文字和影像的按鈕、下拉按鈕和控制項、溢位按鈕，以及 <xref:System.Windows.Forms.ToolStrip> 專案的執行時間重新排列。  
  
- 支援溢位和執行時間專案重新排列。 當沒有足夠的空間可在 <xref:System.Windows.Forms.ToolStrip>中顯示時，溢位功能會將專案移至下拉式功能表。  
  
- 透過常見的轉譯模型，支援作業系統的一般外觀和行為。  
  
- 針對所有容器和包含的專案，以一致的方式處理事件，與處理其他控制項的事件相同。  
  
- 將專案從一個 <xref:System.Windows.Forms.ToolStrip> 拖曳至另一個或在 <xref:System.Windows.Forms.ToolStrip>中。  
  
- 在 <xref:System.Windows.Forms.ToolStripDropDown>中，建立具有「高級」配置的下拉式控制項和使用者介面類別型編輯器。  
  
 使用 <xref:System.Windows.Forms.ToolStripControlHost> 類別，在 <xref:System.Windows.Forms.ToolStrip> 上使用其他控制項，並為其取得 <xref:System.Windows.Forms.ToolStrip> 功能。  
  
 您可以使用 <xref:System.Windows.Forms.ToolStripRenderer>、<xref:System.Windows.Forms.ToolStripProfessionalRenderer>和 <xref:System.Windows.Forms.ToolStripManager> 以及 <xref:System.Windows.Forms.ToolStripRenderMode> 和 <xref:System.Windows.Forms.ToolStripManagerRenderMode> 列舉，來擴充功能及修改外觀和行為。  
  
 <xref:System.Windows.Forms.ToolStrip> 控制項可高度設定和擴充，並提供許多屬性、方法和事件來自訂外觀和行為。 以下是一些值得注意的成員：  
  
### <a name="important-toolstrip-members"></a>重要的 ToolStrip 成員  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|取得或設定停駐 <xref:System.Windows.Forms.ToolStrip> 父容器的邊緣。|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|取得或設定值，表示拖放動作和項目的重新排序是否由 <xref:System.Windows.Forms.ToolStrip> 類別私下處理。|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|取得或設定值，指出 <xref:System.Windows.Forms.ToolStrip> 如何配置其專案。|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|取得或設定 <xref:System.Windows.Forms.ToolStripItem> 是否附加至 <xref:System.Windows.Forms.ToolStrip> 或 <xref:System.Windows.Forms.ToolStripOverflowButton>，或可在兩者之間浮動。|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|取得值，指出當按一下 <xref:System.Windows.Forms.ToolStripItem> 時，<xref:System.Windows.Forms.ToolStripItem> 是否會在下拉式清單中顯示其他專案。|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|取得 <xref:System.Windows.Forms.ToolStripItem>，它會在啟用溢位時做為 <xref:System.Windows.Forms.ToolStrip> 的溢位按鈕。|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|取得或設定用來自訂 <xref:System.Windows.Forms.ToolStrip>之外觀和行為（外觀與風格）的 <xref:System.Windows.Forms.ToolStripRenderer>。|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|取得或設定套用至 <xref:System.Windows.Forms.ToolStrip> 的繪製樣式。|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|在 <xref:System.Windows.Forms.ToolStrip.Renderer%2A> 屬性變更時引發。|  
  
 透過使用一些附屬類別，就能達到 <xref:System.Windows.Forms.ToolStrip> 控制項的彈性。 以下是一些最值得注意的部分：  
  
### <a name="important-toolstrip-companion-classes"></a>重要的 ToolStrip 附屬類別  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|取代並加入 <xref:System.Windows.Forms.MainMenu> 類別的功能。|  
|<xref:System.Windows.Forms.StatusStrip>|取代並加入 <xref:System.Windows.Forms.StatusBar> 類別的功能。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|取代並加入 <xref:System.Windows.Forms.ContextMenu> 類別的功能。|  
|<xref:System.Windows.Forms.ToolStripItem>|針對 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.ToolStripControlHost>或 <xref:System.Windows.Forms.ToolStripDropDown> 可以包含的所有元素，管理事件和配置的抽象基類。|  
|<xref:System.Windows.Forms.ToolStripContainer>|會在表單的每一端提供一個面板，其中控制項可透過各種方式排列。|  
|<xref:System.Windows.Forms.ToolStripRenderer>|處理 <xref:System.Windows.Forms.ToolStrip> 物件的繪製功能。|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|提供 Microsoft Office 樣式的外觀。|  
|<xref:System.Windows.Forms.ToolStripManager>|控制 <xref:System.Windows.Forms.ToolStrip> 的呈現和浮動定位，以及 <xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.ToolStripDropDownMenu> 和 <xref:System.Windows.Forms.ToolStripMenuItem> 物件的合併。|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|指定套用至包含在表單中之多個 <xref:System.Windows.Forms.ToolStrip> 物件的繪製樣式（自訂、Windows XP 或 Microsoft Office Professional）。|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|指定套用至表單所包含之一個 <xref:System.Windows.Forms.ToolStrip> 物件的繪製樣式（自訂、Windows XP 或 Microsoft Office Professional）。|  
|<xref:System.Windows.Forms.ToolStripControlHost>|裝載其他不是特別 <xref:System.Windows.Forms.ToolStrip> 控制項，但您想要 <xref:System.Windows.Forms.ToolStrip> 功能的控制項。|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|指定是否要在主要 <xref:System.Windows.Forms.ToolStrip>、溢位 <xref:System.Windows.Forms.ToolStrip>或兩者皆配置 <xref:System.Windows.Forms.ToolStripItem>。|  
  
 如需詳細資訊，請參閱[Toolstrip 技術摘要](toolstrip-technology-summary.md)和[toolstrip 控制項架構](toolstrip-control-architecture.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
