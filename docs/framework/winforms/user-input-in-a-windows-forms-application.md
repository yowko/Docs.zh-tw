---
title: Windows Forms 應用程式中的使用者輸入
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 8e82276f14519c4ef54948744c93014232bdff52
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734802"
---
# <a name="user-input-in-a-windows-forms-application"></a>Windows Form 應用程式中的使用者輸入
在 Windows Forms 中，使用者輸入會以 Windows 訊息的形式傳送至應用程式。 一系列可覆寫的方法會在應用程式、表單和控制項層級處理這些訊息。 當這些方法收到滑鼠和鍵盤訊息時，它們會引發可處理的事件，以取得滑鼠或鍵盤輸入的相關資訊。 在許多情況下，Windows Forms 應用程式只要處理這些事件，就能夠處理所有使用者輸入。 在其他情況下，應用程式可能需要覆寫處理訊息的其中一個方法，以便在應用程式、表單或控制項收到特定訊息之前加以攔截。  
  
## <a name="mouse-and-keyboard-events"></a>滑鼠和鍵盤事件  
 所有 Windows Forms 控制項都會繼承一組與滑鼠和鍵盤輸入相關的事件。 例如，控制項可以處理 <xref:System.Windows.Forms.Control.KeyPress> 事件來判斷所按下按鍵的字元碼，或是控制項可以處理 <xref:System.Windows.Forms.Control.MouseClick> 事件來判斷滑鼠點按的位置。 如需滑鼠和鍵盤事件的詳細資訊，請參閱[在 Windows Forms 中](mouse-events-in-windows-forms.md)[使用鍵盤事件](using-keyboard-events.md)和滑鼠事件。  
  
## <a name="methods-that-process-user-input-messages"></a>處理使用者輸入訊息的方法  
 表單和控制項可以存取 <xref:System.Windows.Forms.IMessageFilter> 介面，以及一組可覆寫的方法，在訊息佇列中的不同時間點處理 Windows 訊息。 這些方法都有一個 <xref:System.Windows.Forms.Message> 參數，可封裝 Windows 訊息的低層級詳細資料。 您可以執行或覆寫這些方法來檢查訊息，然後取用訊息，或將它傳遞給訊息佇列中的下一個取用者。 下表提供處理 Windows Forms 中所有 Windows 訊息的方法。  
  
|方法|注意事項|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|這個方法會在應用層級攔截已排入佇列（也稱為已張貼）的 Windows 訊息。|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|這個方法會在處理之前，先攔截表單和控制項層級的 Windows 訊息。|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|這個方法會處理表單和控制項層級的 Windows 訊息。|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|這個方法會在表單和控制項層級執行 Windows 訊息的預設處理。 這會提供視窗的最小功能。|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|這個方法在處理之後，會在表單和控制項層級攔截訊息。 必須設定 <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> 的樣式位，才能呼叫這個方法。|  
  
 鍵盤和滑鼠訊息也是由一組額外的可覆寫方法所處理，這是一種特定類型的訊息。 如需詳細資訊，請參閱[鍵盤輸入的運作方式](how-keyboard-input-works.md)和[滑鼠輸入在 Windows Forms 中的運作](how-mouse-input-works-in-windows-forms.md)方式。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 中的使用者輸入](user-input-in-windows-forms.md)
- [Windows Forms 應用程式中的鍵盤輸入](keyboard-input-in-a-windows-forms-application.md)
- [Windows Forms 應用程式中的滑鼠輸入](mouse-input-in-a-windows-forms-application.md)
