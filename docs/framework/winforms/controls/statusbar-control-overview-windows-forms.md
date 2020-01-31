---
title: StatusBar 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: b0b97bc3cb0291871e1fd113d82d0b480b53cdba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742873"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar 控制項概觀 (Windows Form)
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> 和 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項的功能，並將其加入。不過，如果您選擇，<xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項都會保留，以提供回溯相容性及未來使用。  
  
 [Windows Forms[狀態列] 控制項](statusbar-control-windows-forms.md)用於表單上作為區域，通常會顯示在視窗底部，應用程式可以在其中顯示各種類型的狀態資訊。 <xref:System.Windows.Forms.StatusBar> 控制項可以有狀態列面板，它們會顯示文字或圖示來表示狀態，或是動畫中表示進程正在運作的一系列圖示。例如，表示正在儲存檔的 Microsoft Word。  
  
## <a name="using-the-statusbar-control"></a>使用狀態列控制項  
 當滑鼠變換超連結時，Internet Explorer 會使用狀態列來指出頁面的 URL;Microsoft Word 提供頁面位置、區段位置和編輯模式的資訊，例如改寫和修訂追蹤;和 Visual Studio 會使用狀態列來提供內容相關資訊，例如，告訴您如何將可停駐的視窗操作為停駐或浮動。  
  
 您可以將 [<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>] 屬性設定為 [`false`] （預設值），並將狀態列的 [<xref:System.Windows.Forms.StatusBar.Text%2A>] 屬性設定為您要顯示在狀態列中的文字，以在狀態列上顯示單一訊息。 您可以將 [<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>] 屬性設定為 [`true`]，然後使用 <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>的 <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> 方法，將狀態列分割成面板，以顯示一種以上的資訊。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [操作說明：判斷在 Windows Forms StatusBar 控制項中按下的面板](determine-which-panel-wf-statusbar-control-was-clicked.md)
