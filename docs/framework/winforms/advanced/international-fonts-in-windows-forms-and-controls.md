---
title: 在 Windows Form 和控制項中的國際字型
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 1f9afd575e2de04e0b11556ad34436839e13d968
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942892"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>在 Windows Form 和控制項中的國際字型

國際應用程式中，選取字型的建議的方法是盡可能使用字型遞補。 系統會決定哪些指令碼之字元的字型後援表示所屬的。

## <a name="using-font-fallback"></a>使用字型遞補

若要利用這項功能，不需要設定<xref:System.Drawing.Font>表單或任何其他項目內容。 應用程式會自動使用預設系統字型，到另一個不同的作業系統的一種當地語系化語言。 當應用程式執行時，系統會自動在作業系統中選取文化特性提供正確的字型。

沒有規則的例外狀況都不設定的字型，也就是變更字型樣式。 這可能是很重要的應用程式使用者按下按鈕，讓文字在文字方塊中顯示以粗體顯示。 若要這樣做，您會撰寫函式來變更文字方塊的字型樣式，要以粗體顯示，根據任何表單的字型。 請務必在兩個地方呼叫此函式： 在按鈕的<xref:System.Windows.Forms.Control.Click>事件處理常式和<xref:System.Windows.Forms.Control.FontChanged>事件處理常式。 如果只在呼叫此函式<xref:System.Windows.Forms.Control.Click>事件處理常式和其他一些程式碼會變更整個表單的字型家族，文字方塊中不會變更表單的其餘部分。

```vb
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
```

```csharp
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

不過，當您當地語系化您的應用程式，粗體字可能會顯示效能不佳特定語言。 如果這是需要考量，您會想要有的選項切換成一般文字的字型從粗體的當地語系化人員。 因為當地語系化人員通常不是開發人員，而且不需要存取原始程式碼，才能資源檔，此選項需要設定資源檔中。 若要這樣做，您會設定<xref:System.Drawing.Font.Bold%2A>屬性設`true`。 這會導致寫出至資源檔，當地語系化人員可以編輯的字型設定。 然後在您撰寫程式碼之後`InitializeComponent`方法來重設字型根據表單的字型，但使用的字型樣式指定的資源檔中。

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>另請參閱

- [全球化 Windows Forms 應用程式](globalizing-windows-forms.md)
- [使用字型和文字](using-fonts-and-text.md)
