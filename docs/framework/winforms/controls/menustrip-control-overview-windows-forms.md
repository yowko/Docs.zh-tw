---
title: "MenuStrip 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eb27503fffc798b644f95fd213f8f23bdb3e228a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip 控制項概觀 (Windows Form)
功能表會公開給您的使用者功能，藉由在一般情況下分組的命令。  
  
 <xref:System.Windows.Forms.MenuStrip>控制項是此版本的 Visual Studio 和.NET Framework 的新功能。 與控制項，您可以輕鬆建立類似 Microsoft Office 中的功能表。  
  
 <xref:System.Windows.Forms.MenuStrip>控制項支援多重文件介面 (MDI) 和功能表合併、 工具提示和溢位。 您可以加入便捷鍵、 快速鍵、 核取記號、 影像和分隔線來增強可用性和功能表的可讀性。  
  
 <xref:System.Windows.Forms.MenuStrip>控制項取代，並將功能加入<xref:System.Windows.Forms.MainMenu>控制項等控制項，不過，<xref:System.Windows.Forms.MainMenu>如果您選擇，將會保留以提供回溯相容性及未來使用的控制項。  
  
## <a name="ways-to-use-the-menustrip-control"></a>MenuStrip 控制項的使用方式  
 使用<xref:System.Windows.Forms.MenuStrip>控制權傳輸至：  
  
-   建立易於自訂，常採用的功能表支援的進階使用者介面及版面配置功能，例如文字和影像的排序和對齊方式、 拖放作業、 MDI、 溢位，以及存取功能表命令的替代模式。  
  
-   支援的典型的外觀和行為的作業系統。  
  
-   處理事件的所有容器和包含的項目，以一致的方式，您可以在相同的方式處理其他控制項的事件。  
  
 下表顯示一些特別重要的屬性<xref:System.Windows.Forms.MenuStrip>和相關聯的類別。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|取得或設定<xref:System.Windows.Forms.ToolStripMenuItem>用來顯示 MDI 子表單的清單。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|取得或設定子功能表要如何與 MDI 應用程式中的父功能表合併。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|取得或設定 MDI 應用程式中的合併功能表中項目的位置。|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|取得或設定值，指出表單是否為 MDI 子表單的容器。|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|取得或設定值，指出是否顯示工具提示<xref:System.Windows.Forms.MenuStrip>。|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|取得或設定值，表示 <xref:System.Windows.Forms.MenuStrip> 是否支援溢位功能。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|取得或設定與相關聯的快速鍵<xref:System.Windows.Forms.ToolStripMenuItem>。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|取得或設定值，指出是否快速鍵的相關聯<xref:System.Windows.Forms.ToolStripMenuItem>旁會顯示<xref:System.Windows.Forms.ToolStripMenuItem>。|  
  
 下表顯示重要<xref:System.Windows.Forms.MenuStrip>附屬類別。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|表示可選取選項，顯示在<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ContextMenuStrip>。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|代表捷徑功能表。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|代表控制項，可讓使用者從顯示當使用者按一下清單中選取單一項目<xref:System.Windows.Forms.ToolStripDropDownButton>或更高層級的功能表項目。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|提供基本功能的控制項衍生自<xref:System.Windows.Forms.ToolStripItem>顯示時按下的下拉式清單項目。|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
