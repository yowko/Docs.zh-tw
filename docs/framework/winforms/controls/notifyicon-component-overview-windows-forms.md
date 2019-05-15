---
title: NotifyIcon 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: def109799ddfb25b6f56a4f18d52bb19f62842f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645714"
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon 元件概觀 (Windows Form)

Windows Form <xref:System.Windows.Forms.NotifyIcon> 元件大多時候通常會用來顯示在背景執行的處理序圖示，而不會顯示使用者介面。 防毒保護程式即為一例，您可以在工作列的狀態通知區域中，按一下圖示來存取這個程式。

## <a name="key-properties-of-notifyicons"></a>NotifyIcons 的主要屬性

每個 <xref:System.Windows.Forms.NotifyIcon> 元件會在狀態區域中顯示一個圖示。 如果您有三個背景處理序，而且每個都需要顯示圖示，則您必須將三個 <xref:System.Windows.Forms.NotifyIcon> 元件加入表單。 <xref:System.Windows.Forms.NotifyIcon> 元件的主要屬性為 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.Visible%2A>。 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 屬性會設定在狀態區域中顯示的圖示。 若要顯示圖示，<xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性必須設定為 `true`。

## <a name="notifyicons-options"></a>NotifyIcons 選項

您可以將汽球提示、捷徑功能表和工具提示與 <xref:System.Windows.Forms.NotifyIcon> 產生關聯以協助使用者。

您可以呼叫 <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> 方法來指定要顯示汽球提示的時間範圍，為 <xref:System.Windows.Forms.NotifyIcon> 顯示汽球提示。 您也可以分別使用 <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>、<xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>，來指定汽球提示的文字、圖示和標題。 <xref:System.Windows.Forms.NotifyIcon> 元件也可以有關聯的工具提示和捷徑功能表。 如需詳細資訊，請參閱 < [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)並[ContextMenu 元件概觀](contextmenu-component-overview-windows-forms.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.NotifyIcon>
- [NotifyIcon 元件](notifyicon-component-windows-forms.md)
