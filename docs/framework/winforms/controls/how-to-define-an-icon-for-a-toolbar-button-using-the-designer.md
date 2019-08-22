---
title: 作法：使用設計工具定義工具列按鈕的圖示
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 49e93f12bebbf409e6b3a06634556b9103c85f44
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666210"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>HOW TO：使用設計工具定義工具列按鈕的圖示

> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。

<xref:System.Windows.Forms.ToolBar>按鈕可以在其中顯示圖示, 供使用者輕鬆識別。 這可以透過將影像新增至<xref:System.Windows.Forms.ImageList>元件, 並將它<xref:System.Windows.Forms.ToolBar>與控制項產生關聯來達成。

下列程式需要具有包含<xref:System.Windows.Forms.ToolBar>控制項和<xref:System.Windows.Forms.ImageList>元件之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>在設計階段設定工具列按鈕的圖示

1. 將影像新增至<xref:System.Windows.Forms.ImageList>元件。 如需詳細資訊，請參閱[如何：使用設計](how-to-add-or-remove-imagelist-images-with-the-designer.md)工具加入或移除 ImageList 影像。

2. 選取窗<xref:System.Windows.Forms.ToolBar>體上的控制項。

3. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.ToolBar>將控制項<xref:System.Windows.Forms.ToolBar.ImageList%2A> <xref:System.Windows.Forms.ImageList>的屬性設定為元件。

4. <xref:System.Windows.Forms.ToolBar.Buttons%2A> ![ ](./media/visual-studio-ellipsis-button.png)按一下控制項的屬性來選取它, 然後按一下省略號 ([屬性視窗中 Visual Studio] 按鈕的省略號按鈕 (...), 以開啟 [ **ToolBarButton 集合編輯器**]。 <xref:System.Windows.Forms.ToolBar>

5. 使用 [**加入**] 按鈕, 將按鈕<xref:System.Windows.Forms.ToolBar>加入控制項。

6. 在 [ **ToolBarButton 集合編輯器**] 右側窗格中出現的 [ <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> **屬性**] 視窗中, 將每個工具列按鈕的屬性設定為清單中的其中一個值, 這是從您新增至的影像所繪製<xref:System.Windows.Forms.ImageList>元件。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolBar>
- [如何：觸發工具列按鈕的功能表事件](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar 控制項](toolbar-control-windows-forms.md)
- [ImageList 元件](imagelist-component-windows-forms.md)
