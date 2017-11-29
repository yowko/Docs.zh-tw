---
title: "Windows Form 和控制項中的國際字型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5901113021deffd601b5325ff9a1b8912e74329d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Windows Form 和控制項中的國際字型
國際應用程式中選取字型的建議的方法是盡可能使用字型遞補。 所屬字型遞補表示系統決定指令碼字元。  
  
## <a name="using-font-fallback"></a>使用字型遞補  
 若要利用這項功能，請勿設定<xref:System.Drawing.Font>表單或其他任何項目屬性。 應用程式會自動使用預設系統字型，這與不同作業系統的當地語系化語言到另一個。 應用程式執行時，系統將會自動提供正確的字型，在作業系統中選取的文化特性。  
  
 沒有規則的例外狀況都不設定字型，這是變更字型樣式。 這可能是很重要的應用程式中的使用者按一下按鈕，以粗體文字在文字方塊中出現。 若要這樣做，您可以撰寫函式來變更文字方塊的字型樣式，要以粗體顯示，根據表單的字型是。 請務必呼叫此函式在兩個地方： 在按鈕的<xref:System.Windows.Forms.Control.Click>事件處理常式並在<xref:System.Windows.Forms.Control.FontChanged>事件處理常式。 如果只有在呼叫此函式<xref:System.Windows.Forms.Control.Click>事件處理常式和其他一些程式碼變更整個表單的字型系列，文字方塊中不會變更表單的其餘部分。  
  
```  
' Visual Basic  
Private Sub MakeBold()  
   ' Change the TextBox to a bold version of the form font  
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
   ' Clicking this button makes the TextBox bold  
   MakeBold()  
End Sub  
  
Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged  
   ' If the TextBox is already bold and the form's font changes,  
   ' change the TextBox to a bold version of the new form font  
   If (TextBox1.Font.Style = FontStyle.Bold) Then  
      MakeBold()  
   End If  
End Sub  
  
// C#  
private void button1_Click(object sender, System.EventArgs e)  
{  
   // Clicking this button makes the TextBox bold  
   MakeBold();  
}  
  
private void MakeBold()   
{  
   // Change the TextBox to a bold version of the form's font  
   textBox1.Font = new Font(this.Font, FontStyle.Bold);  
}  
  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
   // If the TextBox is already bold and the form's font changes,  
   // change the TextBox to a bold version of the new form font  
   if (textBox1.Font.Style == FontStyle.Bold)   
   {  
      MakeBold();  
   }  
}  
```  
  
 不過，當當地語系化您的應用程式時，粗體字型可能會顯示特定狀況不佳的語言。 如果這是一項考量，您會希望當地語系化切換成一般文字的字型從粗體的選項。 因為當地語系化人員通常不是開發人員，而且不需要存取原始程式碼，只以資源檔，這個選項必須設定資源檔中。 若要這樣做，您會設定<xref:System.Drawing.Font.Bold%2A>屬性`true`。 這樣會寫入至資源檔，當地語系化人員可以編輯的字型設定。 接著，您撰寫程式碼之後`InitializeComponent`方法來重設字型根據表單的字型，但使用的字型樣式資源檔中指定。  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## <a name="see-also"></a>另請參閱  
 [全球化 Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
