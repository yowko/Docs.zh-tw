---
title: HOW TO：將 Windows Form 按鈕指定為接受按鈕
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
ms.openlocfilehash: 00d9f4acffb88b5047b40df91799cea1caaf2cf2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714693"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>HOW TO：將 Windows Form 按鈕指定為接受按鈕
在任何 Windows 表單上，您可以指定<xref:System.Windows.Forms.Button>設為接受按鈕，也就是預設按鈕的控制項。 每當使用者按下 ENTER 鍵，不論哪一個表單上的其他控制項具有焦點按一下預設按鈕。  
  
> [!NOTE]
>  例外狀況是另一個按鈕具有焦點的控制項時，會被按一下的按鈕，並將焦點放在此情況下，-多行文字方塊中或自訂控制項的設陷 ENTER 鍵。  
  
### <a name="to-designate-the-accept-button"></a>若要指定為接受按鈕  
  
1.  將表單的<xref:System.Windows.Forms.Form.AcceptButton%2A>屬性為適當<xref:System.Windows.Forms.Button>控制項。  
  
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
- [如何：將 Windows Form 按鈕指定為取消按鈕](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button 控制項](button-control-windows-forms.md)
