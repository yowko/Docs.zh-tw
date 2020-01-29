---
title: 使用設計工具設定面板的背景
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731928"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>如何：使用設計工具設定 Windows Forms 面板的背景

Windows Forms <xref:System.Windows.Forms.Panel> 控制項可以同時顯示背景色彩和背景影像。 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性會設定面板中所包含控制項的背景色彩，例如標籤和選項按鈕。 如果未設定 [<xref:System.Windows.Forms.Control.BackgroundImage%2A>] 屬性，<xref:System.Windows.Forms.Control.BackColor%2A> 選取專案就會填滿所有的面板。 如果已設定 [<xref:System.Windows.Forms.Control.BackgroundImage%2A>] 屬性，影像就會顯示在面板所包含的控制項後方。

下列程式需要具有包含 <xref:System.Windows.Forms.Panel> 控制項之表單的**Windows 應用程式**專案。 如需如何在 Visual Studio 中設定這類專案的詳細資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。

## <a name="set-the-background-in-the-windows-forms-designer"></a>設定 Windows Form 設計工具中的背景

1. 在 Visual Studio 中開啟專案，然後選取 [<xref:System.Windows.Forms.Panel>] 控制項。

2. 在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.Control.BackColor%2A>] 屬性旁的箭號按鈕，以顯示具有三個索引標籤的視窗。

3. 選取 [**自訂**] 索引標籤以顯示色彩的調色板。

4. 選取 [ **Web** ] 或 [**系統**] 索引標籤，以顯示色彩的預先定義名稱清單，然後選取色彩。

5. 在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.Control.BackgroundImage%2A>] 屬性旁的箭號按鈕。

6. 在 [**開啟**] 對話方塊中，選取您要顯示的檔案。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel 控制項](panel-control-windows-forms.md)
- [Panel 控制項概觀](panel-control-overview-windows-forms.md)
- [操作說明：搭配 Windows Forms Panel 控制項使用設計工具群組控制項](group-controls-with-wf-panel-control-using-the-designer.md)
