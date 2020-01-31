---
title: 將按鈕指定為 [取消] 按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 123b3e275065efadd24815320ea7d855808e60b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743255"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>如何：將 Windows Form 中的 Button 指定為取消按鈕
在任何 Windows Form 上，您都可以將 <xref:System.Windows.Forms.Button> 控制項指定為 [取消] 按鈕。 每當使用者按下 ESC 鍵時，就會按一下 [取消] 按鈕，而不論表單上的其他控制項有哪些焦點。 這類按鈕通常是程式設計的，可讓使用者快速結束作業，而不需要認可任何動作。  
  
### <a name="to-designate-the-cancel-button"></a>若要指定取消按鈕  
  
1. 將表單的 <xref:System.Windows.Forms.Form.CancelButton%2A> 屬性設定為適當的 <xref:System.Windows.Forms.Button> 控制項。  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [操作說明：回應 Windows Forms Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [操作說明：將 Windows Forms 中的 Button 指定為接受按鈕](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Button 控制項](button-control-windows-forms.md)
