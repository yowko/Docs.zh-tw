---
title: Windows Form 應用程式中的使用者輸入
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 351c1e42bb775331cbe0e2005b6bea284716de75
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711924"
---
# <a name="user-input-in-a-windows-forms-application"></a>Windows Form 應用程式中的使用者輸入
在 Windows Forms 中，使用者輸入會傳送至應用程式的 Windows 訊息格式。 一系列的可覆寫的方法會處理在應用程式時，表單中，這些訊息，並控制層級。 當這些方法會接收滑鼠和鍵盤訊息時，它們就會引發可處理以取得有關滑鼠或鍵盤輸入的事件。 在許多情況下，Windows Forms 應用程式能夠處理所有的使用者輸入，只要在處理這些事件。 在其他情況下，應用程式可能需要覆寫其中一個處理訊息，以便攔截特定的訊息之前收到應用程式、 表單或控制項的方法。  
  
## <a name="mouse-and-keyboard-events"></a>滑鼠和鍵盤事件  
 所有 Windows Forms 控制項都繼承一組滑鼠和鍵盤輸入相關的事件。 例如，控制項可以處理<xref:System.Windows.Forms.Control.KeyPress>事件，以判斷已按下的索引鍵的字元碼或控制項可以處理<xref:System.Windows.Forms.Control.MouseClick>事件，以判斷滑鼠的位置按一下。 如需有關滑鼠和鍵盤事件的詳細資訊，請參閱[使用鍵盤事件](using-keyboard-events.md)並[Windows Forms 中的滑鼠事件](mouse-events-in-windows-forms.md)。  
  
## <a name="methods-that-process-user-input-messages"></a>處理使用者輸入的訊息的方法  
 表單和控制項可以存取<xref:System.Windows.Forms.IMessageFilter>介面和一組處理 Windows 訊息的訊息佇列中的不同點的可覆寫方法。 這些方法都有<xref:System.Windows.Forms.Message>參數，其會封裝 Windows 訊息的低層級的詳細資料。 您可以實作或覆寫這些方法來檢查訊息，然後使用訊息，或將它傳遞到訊息佇列中下一個取用者。 下表提供處理 Windows Form 中的所有 Windows 訊息的方法。  
  
|方法|注意|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|這個方法會攔截已排入佇列 （也稱為已發佈） 應用程式層級的 Windows 訊息。|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|在處理它們之前，這個方法會攔截在表單和控制項的層級的 Windows 訊息。|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|這個方法會處理 Windows 訊息，在表單和控制項的層級。|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|這個方法會執行表單和控制項的層級的 Windows 訊息的預設處理。 這可提供最小視窗的功能。|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|已處理之後，這個方法會攔截表單和控制項的層級的訊息。 <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage>樣式位元必須設定要呼叫這個方法。|  
  
 鍵盤和滑鼠訊息也會處理由一組額外的可覆寫的方法專屬於這些類型的訊息。 如需詳細資訊，請參閱 <<c0> [ 鍵盤輸入的運作方式](how-keyboard-input-works.md)並[滑鼠輸入的運作方式在 Windows Form 中](how-mouse-input-works-in-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱
- [Windows Forms 中的使用者輸入](user-input-in-windows-forms.md)
- [Windows Forms 應用程式中的鍵盤輸入](keyboard-input-in-a-windows-forms-application.md)
- [Windows Forms 應用程式中的滑鼠輸入](mouse-input-in-a-windows-forms-application.md)
