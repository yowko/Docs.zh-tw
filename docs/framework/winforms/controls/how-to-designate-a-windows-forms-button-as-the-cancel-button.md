---
title: HOW TO：將 Windows Forms 的按鈕指定為取消按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: ad95a527ea72858cc106c87d8712110e018e97b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231431"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>HOW TO：將 Windows Forms 的按鈕指定為取消按鈕
在任何 Windows 表單上，您可以指定<xref:System.Windows.Forms.Button>設為 [取消] 按鈕的控制項。 每當使用者按下 ESC 鍵，不論哪一個表單上的其他控制項具有焦點時，按一下 [取消] 按鈕。 這類按鈕通常被設計成讓使用者快速結束作業，而不需要認可至任何動作。  
  
### <a name="to-designate-the-cancel-button"></a>若要指定 [取消] 按鈕  
  
1.  將表單的<xref:System.Windows.Forms.Form.CancelButton%2A>屬性為適當<xref:System.Windows.Forms.Button>控制項。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [選取 Windows Form Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [HOW TO：回應 Windows Forms 按鈕的按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [HOW TO：將 Windows Forms 的按鈕指定為接受按鈕](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Button 控制項](button-control-windows-forms.md)
