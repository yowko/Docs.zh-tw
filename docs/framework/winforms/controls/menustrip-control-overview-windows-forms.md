---
title: MenuStrip 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 41688dce0e645b643d7a10a5cf330f1f3a5f9cc8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653706"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip 控制項概觀 (Windows Form)
功能表功能公開給您使用者按住乃依一般主題的命令。  
  
 <xref:System.Windows.Forms.MenuStrip>控制項是此版本的 Visual Studio 和.NET Framework 的新功能。 與控制項，您可以輕鬆地建立類似 Microsoft Office 中的功能表。  
  
 <xref:System.Windows.Forms.MenuStrip>控制項支援多重文件介面 (MDI) 和功能表合併功能、 工具提示和溢位。 您可以新增 存取金鑰、 快速鍵、 核取記號、 影像和分隔線，來增強可用性和您的功能表的可讀性。  
  
 <xref:System.Windows.Forms.MenuStrip>會取代並將功能加入至<xref:System.Windows.Forms.MainMenu>控制; 不過，<xref:System.Windows.Forms.MainMenu>如果您選擇，將會保留回溯相容性以及供未來使用的控制項。  
  
## <a name="ways-to-use-the-menustrip-control"></a>如何使用 MenuStrip 控制項  
 使用<xref:System.Windows.Forms.MenuStrip>控制項：  
  
-   建立容易自訂、 常採用的功能表可支援進階的使用者介面和版面配置功能，例如文字和影像的排序和對齊方式、 拖放作業、 MDI、 溢位，以及存取功能表命令的替代模式。  
  
-   支援的一般外觀和行為的作業系統。  
  
-   處理事件一致地對所有容器和包含的項目，您可以在相同的方式處理其他控制項的事件。  
  
 下表顯示一些特別重要的屬性<xref:System.Windows.Forms.MenuStrip>和相關聯的類別。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|取得或設定<xref:System.Windows.Forms.ToolStripMenuItem>用來顯示 MDI 子表單的清單。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|取得或設定子功能表要如何與 MDI 應用程式中的父功能表合併。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|取得或設定 MDI 應用程式中的功能表中的合併項目的位置。|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|取得或設定值，指出表單是否為 MDI 子表單的容器。|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|取得或設定值，這個值指出是否會顯示工具提示<xref:System.Windows.Forms.MenuStrip>。|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|取得或設定值，表示 <xref:System.Windows.Forms.MenuStrip> 是否支援溢位功能。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|取得或設定與相關聯的快速鍵<xref:System.Windows.Forms.ToolStripMenuItem>。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|取得或設定值，指出是否快速鍵的相關聯<xref:System.Windows.Forms.ToolStripMenuItem>旁會顯示<xref:System.Windows.Forms.ToolStripMenuItem>。|  
  
 下表顯示重要<xref:System.Windows.Forms.MenuStrip>附屬類別。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|表示可選取的選項，顯示在<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ContextMenuStrip>。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|代表捷徑功能表。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|表示控制項，可讓使用者選取單一項目從清單中會顯示當使用者按一下<xref:System.Windows.Forms.ToolStripDropDownButton>或更高層級的功能表項目。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|提供基本功能，控制項衍生自<xref:System.Windows.Forms.ToolStripItem>顯示時按下的下拉式清單項目。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
