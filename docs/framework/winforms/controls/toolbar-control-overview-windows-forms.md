---
title: ToolBar 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: f364e052258703331496f8103b48953a90aa3a9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735478"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar 控制項概觀 (Windows Form)
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 Windows Form <xref:System.Windows.Forms.ToolBar> 控制項在表單中，是當做顯示下拉式功能表其中一列的控制列和啟動命令的點陣圖按鈕使用。 因此，按一下工具列按鈕相當於選擇功能表命令。 您可將這些按鈕設定成與按鈕、下拉式功能表或分隔符號一樣地顯示和運作。 一般而言，工具列包含對應至應用程式功能表結構中項目的按鈕和功能表，可以快速存取應用程式中最常使用的功能和命令。  
  
## <a name="working-with-the-toolbar-control"></a>使用 ToolBar 控制項  
 <xref:System.Windows.Forms.ToolBar> 控制項通常會沿著其父視窗的頂端「停駐」，但也可以停駐于視窗的任何一邊。 當使用者將滑鼠指標指向工具列按鈕時，工具列可以顯示工具提示。 工具提示是一個小型快顯視窗，用於簡短描述按鈕或功能表的用途。 若要顯示工具提示，<xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> 屬性必須設定為 [`true`]。  
  
> [!NOTE]
> 特定應用程式功能控制項十分類似可以「浮動」在應用程式視窗上方和重新定位的工具列。 Windows Forms ToolBar 控制項無法執行這些動作。  
  
 當 [<xref:System.Windows.Forms.ToolBar.Appearance%2A>] 屬性設定為 [<xref:System.Windows.Forms.ToolBarAppearance>] 時，工具列按鈕會顯示為 [已引發] 和 [三維]。 您可以將工具列的 [<xref:System.Windows.Forms.ToolBar.Appearance%2A>] 屬性設定為 [<xref:System.Windows.Forms.ToolBarAppearance>]，將工具列和其按鈕呈現為一般外觀。 將滑鼠指標移到一般按鈕上方時，按鈕的外觀會變更為三維。 工具列按鈕可以使用分隔符號來分割為邏輯群組。 [分隔符號] 是 <xref:System.Windows.Forms.ToolBarButton.Style%2A> 屬性設定為 [<xref:System.Windows.Forms.ToolBarButtonStyle>] 的工具列按鈕。 它在工具列上會顯示為空白空間。 工具列具有一般外觀時，按鈕分隔符號在按鈕之間會顯示為線條，而不是空格。  
  
 <xref:System.Windows.Forms.ToolBar> 控制項可讓您藉由將 <xref:System.Windows.Forms.Button> 物件新增至 <xref:System.Windows.Forms.ToolBar.Buttons%2A> 集合來建立工具列。 您可以使用 [集合編輯器]，將按鈕新增至 <xref:System.Windows.Forms.ToolBar> 控制項;每個 <xref:System.Windows.Forms.Button> 物件都應該指派文字或影像，雖然您可以同時指派兩者。 相關聯 [ImageList](imagelist-component-windows-forms.md) 元件所提供的影像。 在執行時間，您可以使用 <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> 和 <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> 方法，在 <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> 中新增或移除按鈕。 若要為 <xref:System.Windows.Forms.ToolBar>的按鈕編寫程式碼，請使用 <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> 類別的 <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> 屬性，來判斷已按下哪一個按鈕，將程式碼加入 <xref:System.Windows.Forms.ToolBar>的 <xref:System.Windows.Forms.ToolBar.ButtonClick> 事件中。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ToolBar>
- [ToolBar 控制項](toolbar-control-windows-forms.md)
- [操作說明：將按鈕新增至工具列控制項](how-to-add-buttons-to-a-toolbar-control.md)
- [操作說明：定義工具列按鈕的圖示](how-to-define-an-icon-for-a-toolbar-button.md)
- [如何：觸發工具列按鈕的功能表事件](how-to-trigger-menu-events-for-toolbar-buttons.md)
