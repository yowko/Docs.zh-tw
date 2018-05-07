---
title: ToolStrip 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 3927f180e738541f2f2f8af6d03d281f6a601167
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.ToolStrip>控制項以及與其相關聯的類別提供一般架構合併工具列、 狀態列和功能表的使用者介面項目。 <xref:System.Windows.Forms.ToolStrip> 控制項提供豐富的設計階段經驗，包括在就地啟用和編輯、 自訂配置] 和 [浮動定位，這是工具列共用水平或垂直空間的能力。  
  
 雖然<xref:System.Windows.Forms.ToolStrip>取代，並將功能加入至較舊的版本中的控制項<xref:System.Windows.Forms.ToolBar>如果想要保留以提供回溯相容性及未來使用。  
  
## <a name="features-of-the-toolstrip-controls"></a>ToolStrip 控制項的功能  
 使用<xref:System.Windows.Forms.ToolStrip>控制權傳輸至：  
  
-   在容器存在通用使用者介面。  
  
-   建立易於自訂，常採用支援的工具列進階使用者介面和版面配置功能，例如文字和影像、 下拉式按鈕和控制項的停駐、 浮動定位，按鈕，溢位按鈕和執行階段時重新排列<xref:System.Windows.Forms.ToolStrip>項目。  
  
-   支援溢位和執行階段項目重新排列。 溢位功能會移至下拉功能表項目時的空間不足以它們顯示在<xref:System.Windows.Forms.ToolStrip>。  
  
-   支援的典型的外觀和行為的作業系統，透過常見的轉譯模型。  
  
-   處理事件的所有容器和包含的項目，以一致的方式，您可以在相同的方式處理其他控制項的事件。  
  
-   拖曳項目從某個<xref:System.Windows.Forms.ToolStrip>之間或<xref:System.Windows.Forms.ToolStrip>。  
  
-   建立下拉式清單控制項和使用者介面的型別編輯器進階的配置的<xref:System.Windows.Forms.ToolStripDropDown>。  
  
 使用<xref:System.Windows.Forms.ToolStripControlHost>類別上使用其他控制項<xref:System.Windows.Forms.ToolStrip>並取得<xref:System.Windows.Forms.ToolStrip>它們的功能。  
  
 您可以擴充功能，並使用修改的外觀和行為<xref:System.Windows.Forms.ToolStripRenderer>， <xref:System.Windows.Forms.ToolStripProfessionalRenderer>，和<xref:System.Windows.Forms.ToolStripManager>連同<xref:System.Windows.Forms.ToolStripRenderMode>和<xref:System.Windows.Forms.ToolStripManagerRenderMode>列舉型別。  
  
 <xref:System.Windows.Forms.ToolStrip>控制項高度可設定且可延伸的而且它會提供許多屬性、 方法和事件，以自訂外觀和行為。 以下是一些值得注意的成員：  
  
### <a name="important-toolstrip-members"></a>重要的 ToolStrip 成員  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|取得或設定父容器的邊緣<xref:System.Windows.Forms.ToolStrip>停駐於。|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|取得或設定值，表示拖放動作和項目的重新排序是否由 <xref:System.Windows.Forms.ToolStrip> 類別私下處理。|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|取得或設定值，指出如何<xref:System.Windows.Forms.ToolStrip>配置其項目。|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|取得或設定是否<xref:System.Windows.Forms.ToolStripItem>附加至<xref:System.Windows.Forms.ToolStrip>或<xref:System.Windows.Forms.ToolStripOverflowButton>或兩者之間可以浮動。|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|取得值，指出是否<xref:System.Windows.Forms.ToolStripItem>會顯示在下拉式清單中的其他項目清單時<xref:System.Windows.Forms.ToolStripItem>按下。|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|取得 <xref:System.Windows.Forms.ToolStripItem>，它會在啟用溢位時做為 <xref:System.Windows.Forms.ToolStrip> 的溢位按鈕。|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|取得或設定<xref:System.Windows.Forms.ToolStripRenderer>用來自訂外觀和行為 （外觀及操作） <xref:System.Windows.Forms.ToolStrip>。|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|取得或設定要套用至的繪製樣式<xref:System.Windows.Forms.ToolStrip>。|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|引發的時機<xref:System.Windows.Forms.ToolStrip.Renderer%2A>屬性變更。|  
  
 <xref:System.Windows.Forms.ToolStrip>控制項的彈性達成附屬類別數目。 以下是一些最值得注意：  
  
### <a name="important-toolstrip-companion-classes"></a>重要的 ToolStrip 附屬類別  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|取代，並將功能加入<xref:System.Windows.Forms.MainMenu>類別。|  
|<xref:System.Windows.Forms.StatusStrip>|取代，並將功能加入<xref:System.Windows.Forms.StatusBar>類別。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|取代，並將功能加入<xref:System.Windows.Forms.ContextMenu>類別。|  
|<xref:System.Windows.Forms.ToolStripItem>|抽象基底類別，可管理事件和配置的所有項目， <xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.ToolStripControlHost>，或<xref:System.Windows.Forms.ToolStripDropDown>可以包含。|  
|<xref:System.Windows.Forms.ToolStripContainer>|提供的表單可以以各種方式排列控制項中的每一端上的面板的容器。|  
|<xref:System.Windows.Forms.ToolStripRenderer>|處理的繪製功能<xref:System.Windows.Forms.ToolStrip>物件。|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|提供 Microsoft Office 樣式外觀。|  
|<xref:System.Windows.Forms.ToolStripManager>|控制項<xref:System.Windows.Forms.ToolStrip>轉譯和浮動定位，及合併<xref:System.Windows.Forms.MenuStrip>， <xref:System.Windows.Forms.ToolStripDropDownMenu>，和<xref:System.Windows.Forms.ToolStripMenuItem>物件。|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|指定套用至多個的繪製樣式 （自訂，Windows XP 或 Microsoft Office Professional）<xref:System.Windows.Forms.ToolStrip>表單中所包含的物件。|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|指定套用至其中的繪製樣式 （自訂，Windows XP 或 Microsoft Office Professional）<xref:System.Windows.Forms.ToolStrip>表單中所包含的物件。|  
|<xref:System.Windows.Forms.ToolStripControlHost>|裝載其他控制項，不會特別<xref:System.Windows.Forms.ToolStrip>控制項但要為其<xref:System.Windows.Forms.ToolStrip>功能。|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|指定是否<xref:System.Windows.Forms.ToolStripItem>是配置在主要<xref:System.Windows.Forms.ToolStrip>，溢位<xref:System.Windows.Forms.ToolStrip>，或兩者都關閉。|  
  
 如需詳細資訊，請參閱[ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)和[ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
