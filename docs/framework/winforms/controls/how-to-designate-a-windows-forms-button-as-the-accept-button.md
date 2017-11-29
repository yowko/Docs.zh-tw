---
title: "如何：將 Windows Form 中的 Button 指定為接受按鈕"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bf5f8dbf8718cb6a30883395d54c5cbc6bafaff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>如何：將 Windows Form 中的 Button 指定為接受按鈕
您可以在任何 Windows 表單上，指定<xref:System.Windows.Forms.Button>控制項為接受按鈕，也稱為預設按鈕。 每當使用者按下 ENTER 鍵，是按下無論哪個表單上的其他控制項具有焦點的預設按鈕。  
  
> [!NOTE]
>  例外狀況是另一個按鈕具有焦點的控制項時，會在此情況下，按一下具有焦點按鈕，或多行文字方塊中或自訂控制項的 ENTER 鍵。  
  
### <a name="to-designate-the-accept-button"></a>若要指定接受按鈕  
  
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
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Button 控制項概觀](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [選取 Windows Forms Button 控制項的方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [操作說明：回應 Windows Forms Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [操作說明：將 Windows Forms 中的 Button 指定為取消按鈕](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
