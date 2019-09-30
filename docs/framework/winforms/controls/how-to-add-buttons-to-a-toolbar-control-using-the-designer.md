---
title: 作法：使用設計工具將按鈕新增至 ToolBar 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: 4d7a49633599aabc96153e4793e50c1a4d6d092d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666212"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>作法：使用設計工具將按鈕新增至 ToolBar 控制項

> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。

<xref:System.Windows.Forms.ToolBar>控制項的整數部分是您加入其中的按鈕。 這些可以用來提供功能表命令的輕鬆存取, 或者將它們放在應用程式使用者介面的另一個區域, 以向您的使用者公開功能表結構中無法使用的命令。

下列程式需要具有包含<xref:System.Windows.Forms.ToolBar>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

### <a name="to-add-buttons-at-design-time"></a>若要在設計階段加入按鈕

1. 選取 <xref:System.Windows.Forms.ToolBar> 控制項。

2. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.ToolBar.Buttons%2A>按一下屬性來選取它, 然後按一下省略號![屬性視窗中 Visual Studio](./media/visual-studio-ellipsis-button.png) 按鈕的省略號按鈕 (...), 以開啟**ToolBarButton集合編輯器**。

3. 使用 [**新增**] 和 [**移除**] 按鈕, 即可在<xref:System.Windows.Forms.ToolBar>控制項中加入和移除按鈕。

4. 在編輯器右側窗格中的 [**屬性**] 視窗中, 設定個別按鈕的屬性。 下表顯示一些要考慮的重要屬性。

    |屬性|描述|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|設定要顯示在下拉式工具列按鈕中的功能表。 工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>。 這個屬性會將<xref:System.Windows.Forms.ContextMenu>類別的實例當做參考。|
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|設定是否要部分推送轉場樣式的工具列按鈕。 工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>。|
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|設定轉場樣式的工具列按鈕目前是否處於已推送狀態。 工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>或<xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>。|
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|設定工具列按鈕的樣式。 必須是<xref:System.Windows.Forms.ToolBarButtonStyle>列舉中的其中一個值。|
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|按鈕所顯示的文字字串。|
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|顯示為按鈕工具提示的文字。|

5. 按一下 **[確定**] 關閉對話方塊, 並建立您指定的面板。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolBar>
- [如何：定義工具列按鈕的圖示](how-to-define-an-icon-for-a-toolbar-button.md)
- [如何：觸發工具列按鈕的功能表事件](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [工具列控制項概觀](toolbar-control-overview-windows-forms.md)
- [ToolBar 控制項](toolbar-control-windows-forms.md)
