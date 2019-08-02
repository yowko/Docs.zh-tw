---
title: MenuStrip 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733451"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip 控制項概觀 (Windows Form)
功能表會保存以通用主題分組的命令, 以向您的使用者公開功能。  
  
 此<xref:System.Windows.Forms.MenuStrip>控制項是在 .NET Framework 2.0 版中引進。 有了<xref:System.Windows.Forms.MenuStrip>這個控制項, 您就可以輕鬆地建立功能表, 就像在 Microsoft Office 中找到的一樣。  
  
 <xref:System.Windows.Forms.MenuStrip>控制項支援多重文件介面 (MDI) 和功能表合併、工具提示和溢位。 您可以藉由新增存取金鑰、快速鍵、核取記號、影像和分隔線, 來增強功能表的可用性和可讀性。  
  
 控制項會取代並將功能<xref:System.Windows.Forms.MainMenu>加入<xref:System.Windows.Forms.MainMenu>控制項, 不過, 如果您選擇, 則會保留控制項以提供回溯相容性及未來使用。 <xref:System.Windows.Forms.MenuStrip>  
  
## <a name="ways-to-use-the-menustrip-control"></a>使用 MenuStrip 控制項的方式  
 <xref:System.Windows.Forms.MenuStrip>使用控制項來執行下列動作:  
  
- 建立可輕鬆自訂且常用的功能表, 其支援先進的使用者介面和版面配置功能, 例如文字和影像順序和對齊、拖放作業、MDI、溢位和存取功能表命令的替代模式。  
  
- 支援作業系統的一般外觀和行為。  
  
- 針對所有容器和包含的專案, 以一致的方式處理事件, 與處理其他控制項的事件相同。  
  
 下表顯示和相關類別的<xref:System.Windows.Forms.MenuStrip>一些特別重要屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|取得或設定<xref:System.Windows.Forms.ToolStripMenuItem> , 用來顯示 MDI 子表單的清單。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|取得或設定子功能表在 MDI 應用程式中與父功能表合併的方式。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|取得或設定在 MDI 應用程式的功能表中, 合併專案的位置。|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|取得或設定值, 指出表單是否為 MDI 子表單的容器。|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|取得或設定值, 指出是否會顯示的<xref:System.Windows.Forms.MenuStrip>工具提示。|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|取得或設定值，表示 <xref:System.Windows.Forms.MenuStrip> 是否支援溢位功能。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|取得或設定與<xref:System.Windows.Forms.ToolStripMenuItem>相關聯的快速鍵。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|取得或設定值, 表示與<xref:System.Windows.Forms.ToolStripMenuItem>相關聯的快速鍵是否會顯示在旁邊。 <xref:System.Windows.Forms.ToolStripMenuItem>|  
  
 下表顯示重要<xref:System.Windows.Forms.MenuStrip>的伴隨類別。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|表示顯示在<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ContextMenuStrip>上的可選取選項。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|代表捷徑功能表。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|表示可讓使用者從清單中選取單一專案的控制項, 當使用者按一下<xref:System.Windows.Forms.ToolStripDropDownButton>或更高層級的功能表項目時, 就會顯示此清單。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|提供在按一下時, 衍生自<xref:System.Windows.Forms.ToolStripItem>該顯示下拉式專案之控制項的基本功能。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
