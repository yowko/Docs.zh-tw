---
title: ToolBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: c7c19783963bb315a0356979797c6f4d4e3b9e08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929586"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar 控制項概觀 (Windows Form)
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 Windows Form <xref:System.Windows.Forms.ToolBar> 控制項在表單中，是當做顯示下拉式功能表其中一列的控制列和啟動命令的點陣圖按鈕使用。 因此，按一下工具列按鈕相當於選擇功能表命令。 您可將這些按鈕設定成與按鈕、下拉式功能表或分隔符號一樣地顯示和運作。 一般而言，工具列包含對應至應用程式功能表結構中項目的按鈕和功能表，可以快速存取應用程式中最常使用的功能和命令。  
  
## <a name="working-with-the-toolbar-control"></a>使用 ToolBar 控制項  
 <xref:System.Windows.Forms.ToolBar>控制項通常會沿著其父視窗的頂端「停駐」, 但也可以停駐于視窗的任何一邊。 當使用者將滑鼠指標指向工具列按鈕時，工具列可以顯示工具提示。 工具提示是一個小型快顯視窗，用於簡短描述按鈕或功能表的用途。 若要顯示工具提示<xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> , 屬性必須設定為`true`。  
  
> [!NOTE]
> 特定應用程式功能控制項十分類似可以「浮動」在應用程式視窗上方和重新定位的工具列。 Windows Forms ToolBar 控制項無法執行這些動作。  
  
 當屬性設定為時, <xref:System.Windows.Forms.ToolBarAppearance>工具列按鈕會顯示為 [已引發] 和 [三維]。 <xref:System.Windows.Forms.ToolBar.Appearance%2A> 您可以將工具列<xref:System.Windows.Forms.ToolBar.Appearance%2A>的屬性設定為<xref:System.Windows.Forms.ToolBarAppearance> , 讓工具列和其按鈕具有平面外觀。 將滑鼠指標移到一般按鈕上方時，按鈕的外觀會變更為三維。 工具列按鈕可以使用分隔符號來分割為邏輯群組。 [ <xref:System.Windows.Forms.ToolBarButton.Style%2A>分隔符號] 是將屬性設定為<xref:System.Windows.Forms.ToolBarButtonStyle>的工具列按鈕。 它在工具列上會顯示為空白空間。 工具列具有一般外觀時，按鈕分隔符號在按鈕之間會顯示為線條，而不是空格。  
  
 控制項可讓您藉由將物件加入<xref:System.Windows.Forms.Button>至<xref:System.Windows.Forms.ToolBar.Buttons%2A>集合來建立工具列。 <xref:System.Windows.Forms.ToolBar> 您可以使用 [集合編輯器] 將按鈕新增至<xref:System.Windows.Forms.ToolBar>控制項; 每<xref:System.Windows.Forms.Button>個物件都應該指派文字或影像, 雖然您可以同時指派兩者。 相關聯 [ImageList](imagelist-component-windows-forms.md) 元件所提供的影像。 在執行時間, 您可以<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A>使用和<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A>方法, 在中新增或移除按鈕。 若<xref:System.Windows.Forms.ToolBar>要對的按鈕進行程式設計, 請使用<xref:System.Windows.Forms.ToolBar.ButtonClick> <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>類別的屬性來判斷所按的按鈕, 以將程式碼加入的事件中。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolBar>
- [ToolBar 控制項](toolbar-control-windows-forms.md)
- [如何：將按鈕加入至工具列控制項](how-to-add-buttons-to-a-toolbar-control.md)
- [如何：定義工具列按鈕的圖示](how-to-define-an-icon-for-a-toolbar-button.md)
- [如何：觸發工具列按鈕的功能表事件](how-to-trigger-menu-events-for-toolbar-buttons.md)
