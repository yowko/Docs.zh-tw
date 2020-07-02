---
title: 如何：將多個事件連接到單一事件處理常式
description: '瞭解如何使用 c # 中屬性視窗的事件檢視，將多個事件連接到 Windows Forms 中的單一事件處理常式。'
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
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621882"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>作法：在 Windows Forms 中將多個事件連接到單一事件處理常式
在您的應用程式設計中，您可能會發現需要針對多個事件使用單一事件處理常式，或有多個事件執行相同程式。 例如，這通常是一種強大的時間保護，讓功能表命令引發相同的事件，就像表單上的按鈕一樣，如果它們公開相同的功能。 若要這麼做，您可以使用 c # 中屬性視窗的 [事件] 視圖，或在 `Handles` [Visual Basic 程式碼編輯器] 中使用關鍵字和 [**類別名稱**] 和 [**方法名稱**] 下拉式方塊。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>若要在 Visual Basic 中將多個事件連接到單一事件處理常式  
  
1. 以滑鼠右鍵按一下表單，然後選擇 [ **View Code**]。  
  
2. 從 [**類別名稱**] 下拉方塊中，選取您想要讓事件處理常式處理的其中一個控制項。  
  
3. 從 [**方法名稱**] 下拉方塊中，選取您想要事件處理常式處理的其中一個事件。  
  
4. [程式碼編輯器] 會插入適當的事件處理常式，並將插入點置於方法內。 在下列範例中，這是 <xref:System.Windows.Forms.Control.Click> 控制項的事件 <xref:System.Windows.Forms.Button> 。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. 將您想要處理的其他事件附加至 `Handles` 子句。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. 將適當的程式碼加入事件處理常式。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>若要將多個事件連接到 C 中的單一事件處理常式\#
  
1. 選取您要連接事件處理常式的控制項。  
  
2. 在 [屬性視窗中，按一下 [**事件**] 按鈕（[![事件] 按鈕](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")）。  
  
3. 按一下您要處理的事件名稱。  
  
4. 在事件名稱旁的 [值] 區段中，按一下下拉式按鈕，顯示符合您要處理之事件之方法簽章的現有事件處理常式清單。  
  
5. 從清單中選取適當的事件處理常式。  
  
     系統會將程式碼加入至表單，以將事件系結至現有的事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- [在 Windows Form 中建立事件處理常式](creating-event-handlers-in-windows-forms.md)
- [事件處理常式概觀](event-handlers-overview-windows-forms.md)
