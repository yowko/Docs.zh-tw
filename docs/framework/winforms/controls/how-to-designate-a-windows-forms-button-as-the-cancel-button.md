---
title: HOW TO：將 Windows Form 按鈕指定為取消按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: f8eacea0d21159d30d48e48be3093ddf8ca3d7d7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722378"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>HOW TO：將 Windows Form 按鈕指定為取消按鈕
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
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [如何：回應 Windows Form Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [如何：將 Windows Form 按鈕指定為接受按鈕](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Button 控制項](button-control-windows-forms.md)
