---
title: HOW TO：在 Windows Forms 中將多個事件連接到單一事件處理常式
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: eec6a754b885cd169e5542221caefb3233c4c8af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967010"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>HOW TO：在 Windows Forms 中將多個事件連接到單一事件處理常式
在您的應用程式的設計，您可能會發現需要使用多個事件的單一事件處理常式，或有多個執行相同的程序的事件。 比方說，它通常是功能強大時間的好幫手能夠引發相同的事件，如您在表單上的按鈕執行作業，如果它們在相同的功能公開 （expose） 的功能表命令。 您可以使用 [事件] 檢視中的 [屬性] 視窗的C#或使用`Handles`關鍵字和**類別名稱**並**方法名稱**下拉式清單方塊，在 Visual Basic 程式碼編輯器中。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>若要將多個事件連線至 Visual Basic 中的單一事件處理常式  
  
1. 以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。  
  
2. 從**類別名稱**下拉式清單方塊中，選取其中一個您想要處理的事件處理常式的控制項。  
  
3. 從**方法名稱**下拉式清單方塊中，選取其中一個您想要處理的事件處理常式的事件。  
  
4. 程式碼編輯器會插入適當的事件處理常式，並將插入點置於方法中。 在下列範例中，很<xref:System.Windows.Forms.Control.Click>事件<xref:System.Windows.Forms.Button>控制項。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. 附加其他您想要處理的事件至`Handles`子句。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. 事件處理常式中加入適當的程式碼。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>若要將多個事件連線至在 C 中的單一事件處理常式\#
  
1. 選取您要連接的事件處理常式的控制項。  
  
2. 在 [屬性] 視窗中，按一下**事件** 按鈕 (![事件按鈕](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow"))。  
  
3. 按一下您想要處理之事件的名稱。  
  
4. 在 事件名稱旁的 值 區段中，按一下下拉式按鈕，以顯示符合您想要處理事件的方法簽章的現有事件處理常式的清單。  
  
5. 從清單中選取適當的事件處理常式。  
  
     程式碼會加入至表單，以將事件繫結至現有的事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- [在 Windows Forms 中建立事件處理常式](creating-event-handlers-in-windows-forms.md)
- [事件處理常式概觀](event-handlers-overview-windows-forms.md)
