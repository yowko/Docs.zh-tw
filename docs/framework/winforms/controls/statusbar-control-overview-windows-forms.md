---
title: StatusBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 5fdefa7d7e7c7ef543f677be7beb61dfee54e077
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077312"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar 控制項概觀 (Windows Form)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>及<xref:System.Windows.Forms.ToolStripStatusLabel>控制項會取代及新增功能<xref:System.Windows.Forms.StatusBar>並<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項保留回溯相容性和未來使用，如果您選擇。  
  
 Windows Forms [StatusBar 控制項](statusbar-control-windows-forms.md)可在表單區域的區域，通常會顯示在視窗中，以何種應用程式可以顯示各種狀態資訊的底部。 <xref:System.Windows.Forms.StatusBar> 控制項可以有狀態列面板上顯示的文字或圖示以表示狀態或一系列的動畫表示正在處理程序; 的圖示比方說，[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]表示正在儲存文件。  
  
## <a name="using-the-statusbar-control"></a>使用 StatusBar 控制項  
 Internet Explorer 使用狀態列來表示頁面的 URL，當滑鼠跨過超連結;[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]提供您資訊所在位置、 區段的位置，以及編輯模式，例如取代和修訂追蹤; 和 Visual Studio 的 [狀態] 列則會提供內容相關的資訊，例如告訴您如何操作可停駐視窗使用為停駐或浮動。  
  
 您可以在狀態列上顯示的單一訊息，藉由設定<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性，以`false`（預設值） 和設定<xref:System.Windows.Forms.StatusBar.Text%2A>狀態列以您想要出現在狀態列中文字的屬性。 您可以將 [狀態] 列分成面板，以藉由設定顯示多個類型的資訊<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性，以`true`並使用<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A>方法<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [如何：判斷按下 Windows Forms StatusBar 控制項中的面板](determine-which-panel-wf-statusbar-control-was-clicked.md)
