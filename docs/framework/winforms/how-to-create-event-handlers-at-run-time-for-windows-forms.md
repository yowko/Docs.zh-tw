---
title: 作法：在執行階段建立 Windows Forms 的事件處理常式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 440086bfd5384fc46aec2997dbdd9937f7a1b65f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964323"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>HOW TO：在執行階段建立 Windows Forms 的事件處理常式

除了使用 Visual Studio 中的 Windows Form 設計工具來建立事件以外, 您也可以在執行時間建立事件處理常式。 這個動作可讓您在執行階段根據程式碼中的條件來連接事件處理常式，而不需要程式一開始啟動時進行連接。

## <a name="create-an-event-handler-at-run-time"></a>在執行時間建立事件處理常式

1. 開啟您想要加入事件處理常式的表單。

2. 使用您要處理之事件的方法簽章，將方法新增至您的表單。

     例如, 如果您正在處理<xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Button>控制項的事件, 您會建立如下的方法:

    ```vb
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)
       ' Add event handler code here.
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
    // Add event handler code here.
    }
    ```

    ```cpp
    private:
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          // Add event handler code here.
       }
    ```

3. 將程式碼新增至您的應用程式的適當事件處理常式。

4. 決定您要為其建立事件處理常式的表單或控制項。

5. 在您表單類別內的方法中，新增程式碼以指定要處理事件的事件處理常式。 例如, 下列程式碼會指定事件處理常式`button1_Click` <xref:System.Windows.Forms.Control.Click>處理<xref:System.Windows.Forms.Button>控制項的事件:

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     上述<xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Visual Basic 程式碼中所示範的方法會建立按鈕的 click 事件處理常式。

## <a name="see-also"></a>另請參閱

- [在 Windows Forms 中建立事件處理常式](creating-event-handlers-in-windows-forms.md)
- [事件處理常式概觀](event-handlers-overview-windows-forms.md)
- [Visual Basic 中的繼承事件處理常式疑難排解](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
