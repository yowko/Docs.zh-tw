---
title: "如何：使用 Windows Form TextBox 控制項建立密碼文字方塊"
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
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: caf5cef9e23134715101545902e32e72d63c0aac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>如何：使用 Windows Form TextBox 控制項建立密碼文字方塊
密碼方塊是 Windows 表單文字方塊顯示預留位置字元，而使用者輸入的字串。  
  
### <a name="to-create-a-password-text-box"></a>若要建立密碼文字方塊  
  
1.  設定<xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性<xref:System.Windows.Forms.TextBox>控制項的特殊字元。  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性會指定顯示在文字方塊中的字元。 例如，如果您希望顯示在 密碼 方塊中，指定 * 的<xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性 視窗中的屬性。 然後，不論何種使用者會在文字方塊中輸入的字元，會顯示一個星號。  
  
2.  （選擇性）設定<xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>屬性。 屬性會決定可以在文字方塊中輸入多少個字元。 如果超過最大長度時，系統會發出嗶聲，文字方塊不接受任何多個字元。 請注意，您可能不想要執行這項操作，因為密碼的最大長度可能會用來決定駭客嘗試猜測密碼。  
  
     下列程式碼範例示範如何初始化文字方塊中，將會接受最多 14 個字元長的字串，並且以星號取代字串。 `InitializeMyControl`程序將不會自動執行，它必須進行呼叫。  
  
    > [!IMPORTANT]
    >  使用<xref:System.Windows.Forms.TextBox.PasswordChar%2A>文字方塊上的屬性可以協助確保其他人將無法判斷使用者的密碼，如果它們觀察到使用者輸入。 此安全性措施並不包含任何類型的儲存或傳送的密碼，可能是因為應用程式邏輯。 因為輸入的文字不以任何方式加密，您應該將其視為機密資料。 即使沒有出現在這種情況，密碼已仍視為純文字字串 （除非您已實作其他安全性措施）。  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [操作說明：控制 Windows Forms TextBox 控制項中的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [操作說明：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [操作說明：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [操作說明：在 Windows Forms TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [操作說明：在 Windows Forms TextBox 控制項中檢視多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
