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
ms.openlocfilehash: e90732329a0d78421d09da1c405ed93d5cb82f23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527530"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>如何：使用設計工具在工具列控制項中加入按鈕
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 不可或缺的一部分<xref:System.Windows.Forms.ToolBar>控制項是您加入的按鈕。 這些可以用來讓您輕鬆存取功能表命令或者，或者，也可置於另一個區域中的命令公開給您的使用者無法使用功能表結構中的應用程式的使用者介面。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.ToolBar>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-add-buttons-at-design-time"></a>若要在設計階段加入按鈕  
  
1.  選取 <xref:System.Windows.Forms.ToolBar> 控制項。  
  
2.  在**屬性**視窗中，按一下 <xref:System.Windows.Forms.ToolBar.Buttons%2A>屬性來選取它，然後按一下 **省略**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕來開啟**ToolBarButton 集合編輯器**。  
  
3.  使用**新增**和**移除**按鈕來加入和移除按鈕等，從<xref:System.Windows.Forms.ToolBar>控制項。  
  
4.  設定的屬性中的個別按鈕**屬性**出現在編輯器的右側窗格中的視窗。 下表顯示一些要考慮的重要屬性。  
  
    |屬性|描述|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|設定要顯示在下拉式清單工具列按鈕的功能表。 工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>。 這個屬性可接受的執行個體<xref:System.Windows.Forms.ContextMenu>類別做為參考。|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|設定是否為部分壓下切換樣式工具列按鈕。 工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>。|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|設定切換樣式工具列按鈕目前是否在按下的狀態。 工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>或<xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>。|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|工具列按鈕的樣式設定。 必須是其中一個值在<xref:System.Windows.Forms.ToolBarButtonStyle>列舉型別。|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|按鈕所顯示的文字字串。|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|顯示按鈕的工具提示文字。|  
  
5.  按一下**確定**關閉對話方塊並建立指定的面板。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolBar>  
 [操作說明：定義工具列按鈕的圖示](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [操作說明：觸發工具列按鈕的功能表事件](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [工具列控制項概觀](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [ToolBar 控制項](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
