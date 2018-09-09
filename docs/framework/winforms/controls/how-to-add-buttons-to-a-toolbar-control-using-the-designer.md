---
title: 如何：使用設計工具在工具列控制項中加入按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: b96f112c83d2296356e3eb566a24315bcefeff1f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253165"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>如何：使用設計工具在工具列控制項中加入按鈕
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 不可或缺的一部分<xref:System.Windows.Forms.ToolBar>控制項是您加入的按鈕。 這些可以用來讓您輕鬆存取功能表命令，或者，或者，他們可以放在您的應用程式的命令公開給您的使用者功能表結構中所沒有的使用者介面的另一個區域。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ToolBar>控制項。 如需這類專案的設定資訊，請參閱[如何： 建立 Windows 應用程式專案](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)並[如何： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-buttons-at-design-time"></a>若要在設計階段加入按鈕  
  
1.  選取 <xref:System.Windows.Forms.ToolBar> 控制項。  
  
2.  在 [**屬性**] 視窗中，按一下<xref:System.Windows.Forms.ToolBar.Buttons%2A>屬性，以選取它，然後按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕，即可開啟**ToolBarButton 集合編輯器**。  
  
3.  使用**新增**並**移除**按鈕來新增和移除按鈕等，從<xref:System.Windows.Forms.ToolBar>控制項。  
  
4.  設定個別的按鈕中的屬性**屬性**出現在編輯器的右邊窗格中的視窗。 下表顯示一些要考慮的重要屬性。  
  
    |屬性|描述|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|設定要顯示在下拉式工具列按鈕的功能表。 工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設為<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>。 這個屬性可接受的執行個體<xref:System.Windows.Forms.ContextMenu>做為參考的類別。|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|設定是否部分壓下切換式工具列按鈕。 工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>。|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|設定是否切換式工具列按鈕目前為按下狀態。 工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>或<xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>。|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|將工具列按鈕的樣式設定。 必須是其中一個值在<xref:System.Windows.Forms.ToolBarButtonStyle>列舉型別。|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|按鈕所顯示的文字字串。|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|會顯示為按鈕的工具提示文字。|  
  
5.  按一下 **確定**關閉對話方塊並建立指定的面板。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolBar>  
 [操作說明：定義工具列按鈕的圖示](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [操作說明：觸發工具列按鈕的功能表事件](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [工具列控制項概觀](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [ToolBar 控制項](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
