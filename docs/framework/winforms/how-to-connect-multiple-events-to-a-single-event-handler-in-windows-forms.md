---
title: "如何：在 Windows Form 中連接多個事件至單一事件處理常式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfd955b4153c7a2bc54d8b52ff1801541c3a7559
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>如何：在 Windows Form 中連接多個事件至單一事件處理常式
設計您的應用程式，您可能會發現需要將多個事件使用單一事件處理常式，或是必須執行相同的程序的多個事件。 比方說，它通常是功能強大的節省時間讓功能表命令，您的表單上的按鈕不會公開相同的功能像引發相同的事件。 您可以使用 C# 中的 [屬性] 視窗的 [事件] 檢視或使用`Handles`關鍵字和**類別名稱**和**方法名稱**下拉式清單方塊在 Visual Basic 程式碼編輯器中。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>若要連接到單一事件處理常式，在 Visual Basic 中的多個事件  
  
1.  以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。  
  
2.  從**類別名稱**下拉式清單方塊中，選取您想要處理此事件處理常式的控制項的其中一個。  
  
3.  從**方法名稱**下拉式清單方塊中，選取其中一個要處理的事件處理常式的事件。  
  
4.  程式碼編輯器會插入適當的事件處理常式，並將插入點置於方法內。 在下列範例中，它是<xref:System.Windows.Forms.Control.Click>事件<xref:System.Windows.Forms.Button>控制項。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  新增其他您想要處理的事件至`Handles`子句。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  事件處理常式中加入適當的程式碼。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>若要連接到單一事件處理常式在 C# 中的多個事件  
  
1.  選取您要連接的事件處理常式的控制項。  
  
2.  在 [屬性] 視窗中，按一下**事件**按鈕 (![事件按鈕](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow"))。  
  
3.  按一下您想要處理之事件的名稱。  
  
4.  在事件名稱旁的 [值] 區段中，按一下下拉式按鈕，以顯示符合您想要處理事件的方法簽章的現有事件處理常式的清單。  
  
5.  從清單中選取適當的事件處理常式。  
  
     程式碼會加入至表單，以將事件繫結至現有的事件處理常式。  
  
## <a name="see-also"></a>請參閱  
 [在 Windows Forms 中建立事件處理常式](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [事件處理常式概觀](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
