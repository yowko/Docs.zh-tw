---
title: HOW TO：使用設計工具設定 Windows Forms 面板的背景
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 6927a7118c43ced03623a9764a3ef1e0814c95cb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211634"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>HOW TO：設定使用設計工具的 Windows Form 面板的背景

Windows Form<xref:System.Windows.Forms.Panel>控制項可以顯示的背景色彩和背景影像。 <xref:System.Windows.Forms.Control.BackColor%2A>屬性會設定包含在窗格中，例如標籤和選項按鈕控制項的背景色彩。 如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>未設定屬性，<xref:System.Windows.Forms.Control.BackColor%2A>選取項目將會填滿所有面板。 如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性設定，將控制項台中包含後面顯示的影像。

下列程序需要**Windows 應用程式**專案，其表單包含<xref:System.Windows.Forms.Panel>控制項。 如需有關如何設定這類專案在 Visual Studio 中的資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。

## <a name="set-the-background-in-the-windows-forms-designer"></a>在 Windows Form 設計工具設定背景

1. 在 Visual Studio 中開啟專案，然後選取<xref:System.Windows.Forms.Panel>控制項。

2. 在 **屬性**視窗中，按一下旁邊的箭號按鈕<xref:System.Windows.Forms.Control.BackColor%2A>屬性以顯示具有三個索引標籤的視窗。

3. 選取 **自訂**索引標籤，顯示色的調色盤。

4. 選取  **Web**或是**系統**tab 鍵移至顯示的預先定義的色彩名稱清單，然後再選取色彩。

5. 在 **屬性**視窗中，按一下旁邊的箭號按鈕<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性。

6. 在 **開啟**對話方塊方塊中，選取您想要顯示的檔案。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel 控制項](panel-control-windows-forms.md)
- [Panel 控制項概觀](panel-control-overview-windows-forms.md)
- [如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項](group-controls-with-wf-panel-control-using-the-designer.md)
