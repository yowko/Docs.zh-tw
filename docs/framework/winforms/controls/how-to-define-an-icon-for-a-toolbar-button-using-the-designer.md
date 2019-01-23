---
title: HOW TO：定義使用設計工具的工具列按鈕的圖示
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: bfd84913015eaf45674b3cd0c7a3d53a202874c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527064"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>HOW TO：定義使用設計工具的工具列按鈕的圖示
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 <xref:System.Windows.Forms.ToolBar> 按鈕可顯示使用者能方便識別其中的圖示。 這透過將影像加入至達成<xref:System.Windows.Forms.ImageList>元件，並將它與<xref:System.Windows.Forms.ToolBar>控制項。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ToolBar>控制項和<xref:System.Windows.Forms.ImageList>元件。 如需這類專案的設定資訊，請參閱[How to:建立 Windows 應用程式專案](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to:將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>若要在設計階段設定的工具列按鈕的圖示  
  
1.  新增映像發佈至<xref:System.Windows.Forms.ImageList>元件。 如需詳細資訊，請參閱[＜How to：新增或移除 ImageList 影像與設計工具](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md)。  
  
2.  選取<xref:System.Windows.Forms.ToolBar>您表單上的控制項。  
  
3.  在 **屬性**視窗中，將<xref:System.Windows.Forms.ToolBar>控制項的<xref:System.Windows.Forms.ToolBar.ImageList%2A>屬性設<xref:System.Windows.Forms.ImageList>元件。  
  
4.  按一下 <xref:System.Windows.Forms.ToolBar>控制項的<xref:System.Windows.Forms.ToolBar.Buttons%2A>屬性來加以選取，然後按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕，開啟**ToolBarButton 集合編輯器**。  
  
5.  使用**新增** 按鈕，將按鈕加入<xref:System.Windows.Forms.ToolBar>控制項。  
  
6.  在**屬性**出現在右側窗格中的視窗**ToolBarButton 集合編輯器**，將<xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A>的每個工具列按鈕，以在清單中，值的其中一個屬性的您加入的映像會取自<xref:System.Windows.Forms.ImageList>元件。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ToolBar>
- [如何：觸發程序的工具列按鈕的功能表事件](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar 控制項](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
- [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
