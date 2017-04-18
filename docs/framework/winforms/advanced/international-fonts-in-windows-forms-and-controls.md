---
title: "Windows Form 和控制項中的國際字型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows Form 中的字型備用"
  - "字型, 全球化的考量"
  - "字型, 國際化"
  - "全球化 [Windows Form], 字元集"
  - "國際應用程式 [Windows Form], 字元顯示"
  - "當地語系化 [Windows Form], 字型"
  - "Windows Form 控制項, 標籤"
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Windows Form 和控制項中的國際字型
在國際應用程式中，選取字型的建議方法是盡可能使用字型後援。  字型後援表示系統決定字元所屬的指令碼。  
  
## 使用字型後援  
 若要利用這個功能，請不要設定表單或任何其他項目的 <xref:System.Drawing.Font> 屬性。  應用程式會自動使用預設系統字型，這會因作業系統的當地語系化語言而異。  當應用程式執行時，系統會針對作業系統中所選的文化特性來自動提供正確的字型。  
  
 上述不設定字型的規則有一項例外，這便是變更字型樣式的狀況。  對於使用者按一下按鈕以使用粗體顯示文字方塊中的文字的應用程式而言，這可能非常重要。  若要如此執行，您必須撰寫函式，依據表單的字型將文字方塊的字型樣式變更成粗體。  在下列兩個位置呼叫這個函式非常重要：在按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式中和在 <xref:System.Windows.Forms.Control.FontChanged> 事件處理常式中。  如果只在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中呼叫這個函式，而其他某個程式碼片段會變更整個表單的字型系列，則文字方塊不會隨著其餘的表單而變更。  
  
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
  
 然而，當您當地語系化您的應用程式時，某些語言的粗體字型顯示效果可能不佳。  如果這點非常重要，則您會希望當地語系化工程師具備將字型從粗體變更成標準文字的選項。  因為當地語系化工程師通常不是開發人員，並且不具有原始程式碼的存取權，而只有資源檔的存取權，所以必須在資源檔中設定這個選項。  若要這麼做，您必須將 <xref:System.Drawing.Font.Bold%2A> 屬性設定為 `true`。  字型設定中的結果會寫入至當地語系化工程師可編輯的資源檔。  然後請在 `InitializeComponent`  方法之後撰寫程式碼，以便依據表單的字型來重設字型，但是使用資源檔中所指定的字型樣式。  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## 請參閱  
 [全球化 Windows Form](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)   
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)