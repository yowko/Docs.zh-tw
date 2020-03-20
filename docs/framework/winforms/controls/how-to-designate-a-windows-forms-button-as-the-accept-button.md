---
title: 將按鈕指定為"接受按鈕"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: ca5f691fb26db5c4adcb48405c9600b54827104c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142143"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>如何：將 Windows Form 中的 Button 指定為接受按鈕
在任何 Windows 表單上，都可以將<xref:System.Windows.Forms.Button>控制項指定為接受按鈕，也稱為預設按鈕。 每當使用者按下 ENTER 鍵時，無論表單上哪個其他控制項具有焦點，都會按一下預設按鈕。  
  
> [!NOTE]
> 例外情況是，具有焦點的控制項是另一個按鈕（在這種情況下，將按一下具有焦點的按鈕）或多行文字方塊或捕獲 ENTER 鍵的自訂控制項。  
  
### <a name="to-designate-the-accept-button"></a>指定接受按鈕  
  
1. 將表單的屬性<xref:System.Windows.Forms.Form.AcceptButton%2A>設置為相應的<xref:System.Windows.Forms.Button>控制項。  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [如何：回應 Windows Form Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [如何：將 Windows Form 中的 Button 指定為取消按鈕](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button 控制項](button-control-windows-forms.md)
