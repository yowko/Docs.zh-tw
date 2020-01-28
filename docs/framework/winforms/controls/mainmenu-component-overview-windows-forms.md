---
title: MainMenu 元件概觀
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745123"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu 元件概觀 (Windows Form)
> [!IMPORTANT]
> 雖然 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 將功能取代並加入舊版的 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 控制項，但如果您選擇，<xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 會保留供回溯相容性及未來使用。  
  
 Windows Forms <xref:System.Windows.Forms.MainMenu> 元件會在執行時間顯示功能表。 主功能表和個別專案的所有子功能表都是 <xref:System.Windows.Forms.MenuItem> 物件。  
  
## <a name="key-properties"></a>索引鍵內容  
 將 [<xref:System.Windows.Forms.MenuItem.DefaultItem%2A>] 屬性設定為 [`true`]，即可將功能表項目指定為預設專案。 按一下功能表時，預設專案會以粗體文字顯示。 功能表項目的 [<xref:System.Windows.Forms.MenuItem.Checked%2A>] 屬性為 [`true`] 或 [`false`]，並指出是否已選取功能表項目。 功能表項目的 <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> 屬性會自訂所選項目的外觀：如果 <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> 設定為 [`true`]，則會在專案旁顯示選項按鈕;如果 <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> 設定為 `false`，則專案旁邊會出現核取記號。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
