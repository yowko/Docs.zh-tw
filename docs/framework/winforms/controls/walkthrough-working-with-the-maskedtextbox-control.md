---
title: "逐步解說：使用 MaskedTextBox 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "輸入, 控制來確定有效性"
  - "MaskedTextBox 控制項 [Windows Form], 驗證"
  - "MaskedTextBox 控制項 [Windows Form], 逐步解說"
  - "文字, 輸入的控制項"
  - "使用者輸入, 控制"
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 逐步解說：使用 MaskedTextBox 控制項
逐步解說將說明的工作包括：  
  
-   初始化 <xref:System.Windows.Forms.MaskedTextBox> 控制項  
  
-   當輸入的字元不符合遮罩時，使用 <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> 事件處理常式來提醒使用者  
  
-   指派型別給 <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> 屬性，並使用 <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> 事件處理常式在嘗試認可的值對該型別無效時提醒使用者  
  
## 建立專案並加入控制項  
  
#### 若要將 MaskedTextBox 控制項加入至表單  
  
1.  開啟您要放置 <xref:System.Windows.Forms.MaskedTextBox> 控制項的表單。  
  
2.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.MaskedTextBox> 控制項拖曳至表單。  
  
3.  以滑鼠右鍵按一下控制項，並選擇 \[**屬性**\]。  在 \[**屬性**\] 視窗中，按一下 \[**Mask**\] 屬性並按一下屬性名稱旁邊的 **...** \(省略符號\) 按鈕。  
  
4.  在 \[**輸入遮罩**\] 對話方塊中，選取 \[**簡短日期**\] 遮罩，再按一下 \[**確定**\]。  
  
5.  在 \[**屬性**\] 視窗中，將 <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> 屬性設定為 `true`。  每當使用者試圖輸入違反遮罩定義的字元時，這個屬性就會發出短的嗶聲。  
  
 如需 Mask 屬性支援的字元摘要，請參閱 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> 屬性的＜備註＞一節。  
  
## 提醒使用者輸入的錯誤  
  
#### 為遭拒的遮罩輸入加上汽球提示  
  
1.  回到 \[**工具箱**\]，在表單中加入一個 <xref:System.Windows.Forms.ToolTip>。  
  
2.  為 <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> 事件建立一個事件處理常式，當發生輸入錯誤時即引發 <xref:System.Windows.Forms.ToolTip>。  汽球提示會在畫面上停留五秒鐘，或到使用者按它為止。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
  
    ```  
  
## 提醒使用者型別無效  
  
#### 為無效的資料型別建立汽球提示  
  
1.  在表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式中，將一個代表 <xref:System.DateTime> 型別的 <xref:System.Type> 物件指派到 <xref:System.Windows.Forms.MaskedTextBox> 控制項的 <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> 屬性：  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  加入 <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> 事件的事件處理常式：  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.MaskedTextBox>   
 [MaskedTextBox 控制項](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)