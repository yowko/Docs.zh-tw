---
title: MenuStrip 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: a536d13cb7be3f4e4e4a085e1a4da1b0899b3a0c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734476"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip 控制項概觀 (Windows Form)
功能表會保存以通用主題分組的命令，以向您的使用者公開功能。  
  
 <xref:System.Windows.Forms.MenuStrip> 控制項是在 .NET Framework 的2.0 版中引進。 有了 <xref:System.Windows.Forms.MenuStrip> 控制項，您就可以輕鬆地建立功能表，就像在 Microsoft Office 中找到的一樣。  
  
 <xref:System.Windows.Forms.MenuStrip> 控制項支援多重文件介面（MDI）和功能表合併、工具提示和溢位。 您可以藉由新增存取金鑰、快速鍵、核取記號、影像和分隔線，來增強功能表的可用性和可讀性。  
  
 <xref:System.Windows.Forms.MenuStrip> 控制項會取代 <xref:System.Windows.Forms.MainMenu> 控制項並將其加入功能;不過，如果您選擇，則會保留 <xref:System.Windows.Forms.MainMenu> 控制項，以提供回溯相容性及未來使用。  
  
## <a name="ways-to-use-the-menustrip-control"></a>使用 MenuStrip 控制項的方式  
 使用 <xref:System.Windows.Forms.MenuStrip> 控制項來執行下列動作：  
  
- 建立可輕鬆自訂且常用的功能表，其支援先進的使用者介面和版面配置功能，例如文字和影像順序和對齊、拖放作業、MDI、溢位和存取功能表命令的替代模式。  
  
- 支援作業系統的一般外觀和行為。  
  
- 針對所有容器和包含的專案，以一致的方式處理事件，與處理其他控制項的事件相同。  
  
 下表顯示 <xref:System.Windows.Forms.MenuStrip> 和相關類別的一些特別重要屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|取得或設定用來顯示 MDI 子表單清單的 <xref:System.Windows.Forms.ToolStripMenuItem>。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|取得或設定子功能表在 MDI 應用程式中與父功能表合併的方式。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|取得或設定在 MDI 應用程式的功能表中，合併專案的位置。|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|取得或設定值，指出表單是否為 MDI 子表單的容器。|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|取得或設定值，指出是否會顯示 <xref:System.Windows.Forms.MenuStrip>的工具提示。|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|取得或設定值，表示 <xref:System.Windows.Forms.MenuStrip> 是否支援溢位功能。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|取得或設定與 <xref:System.Windows.Forms.ToolStripMenuItem>相關聯的快速鍵。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|取得或設定值，指出與 <xref:System.Windows.Forms.ToolStripMenuItem> 相關聯的快速鍵是否會顯示在 <xref:System.Windows.Forms.ToolStripMenuItem>旁。|  
  
 下表顯示重要的 <xref:System.Windows.Forms.MenuStrip> 附屬類別。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|表示 <xref:System.Windows.Forms.MenuStrip> 或 <xref:System.Windows.Forms.ContextMenuStrip>上顯示的可選取選項。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|代表捷徑功能表。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|表示可讓使用者從清單中選取單一專案的控制項，當使用者按一下 <xref:System.Windows.Forms.ToolStripDropDownButton> 或更高層級的功能表項目時，就會顯示此清單。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|為衍生自 <xref:System.Windows.Forms.ToolStripItem> 的控制項提供基本功能，而這些控制項會在按一下時顯示下拉式專案。|  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
