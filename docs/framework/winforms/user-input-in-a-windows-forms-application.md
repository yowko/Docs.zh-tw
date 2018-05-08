---
title: Windows Forms 應用程式中的使用者輸入
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 4f1b96ab53b30d045a315b43abd0e38157e26c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="user-input-in-a-windows-forms-application"></a>Windows Forms 應用程式中的使用者輸入
在 Windows Form 使用者輸入會傳送至應用程式的 Windows 訊息的形式。 一系列的可覆寫方法處理這些訊息的應用程式表單，並控制層級。 當這些方法會接收滑鼠和鍵盤訊息時，它們就會引發事件，可取得資訊滑鼠或鍵盤輸入來處理。 在許多情況下，Windows Forms 應用程式將能夠處理所有的使用者輸入，只要處理這些事件。 在其他情況下，應用程式可能需要覆寫其中一個處理訊息才能攔截特定的訊息之前收到由應用程式、 表單或控制項的方法。  
  
## <a name="mouse-and-keyboard-events"></a>滑鼠和鍵盤事件  
 所有 Windows Form 控制項都繼承一組滑鼠和鍵盤輸入的相關事件。 控制項可以處理，例如<xref:System.Windows.Forms.Control.KeyPress>可以處理事件，以判斷已按下按鍵的字元碼或控制項<xref:System.Windows.Forms.Control.MouseClick>事件，以判斷按一下滑鼠的位置。 如需有關滑鼠和鍵盤事件的詳細資訊，請參閱[使用鍵盤事件](../../../docs/framework/winforms/using-keyboard-events.md)和[Windows Form 中的滑鼠事件](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)。  
  
## <a name="methods-that-process-user-input-messages"></a>處理使用者輸入的訊息的方法  
 表單和控制項有存取權<xref:System.Windows.Forms.IMessageFilter>介面和一組可覆寫處理 Windows 訊息的訊息佇列中的不同時期的方法。 這些方法都有<xref:System.Windows.Forms.Message>參數，封裝的 Windows 訊息的低層級詳細資料。 您可以實作，或覆寫這些方法來檢查訊息，然後使用訊息或將它傳遞至訊息佇列中下一個取用者。 下表提供處理 Windows Form 中的所有 Windows 訊息的方法。  
  
|方法|注意|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|這個方法會攔截排入佇列 （也稱為已發佈） 應用程式層級的 Windows 訊息。|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|已處理之前，這個方法會攔截在表單和控制項的層級的 Windows 訊息。|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|這個方法會處理 Windows 訊息，在表單和控制項的層級。|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|這個方法會執行預設處理 Windows 訊息，在表單和控制項的層級。 這可提供視窗的最少的功能。|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|經過處理後，這個方法會攔截在表單和控制項層級的訊息。 <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage>樣式位元必須設定要呼叫這個方法。|  
  
 鍵盤和滑鼠訊息也會處理一組額外的可覆寫的方法專屬於這些類型的訊息。 如需詳細資訊，請參閱[鍵盤輸入的運作方式](../../../docs/framework/winforms/how-keyboard-input-works.md)和[滑鼠輸入的運作方式在 Windows Form 中](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 中的使用者輸入](../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 [Windows Forms 應用程式中的鍵盤輸入](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Windows Forms 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
