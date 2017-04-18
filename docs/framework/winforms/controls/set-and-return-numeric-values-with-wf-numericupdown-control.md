---
title: "如何：使用 Windows Form NumericUpDown 控制項設定和傳回數值 | Microsoft Docs"
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
  - "數值, Windows Form"
  - "NumericUpDown 控制項 [Windows Form], 設定和傳回值"
  - "Windows Form 控制項, NumericUpDown"
  - "Windows Form, 數值"
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用 Windows Form NumericUpDown 控制項設定和傳回數值
Windows Form <xref:System.Windows.Forms.NumericUpDown> 控制項的數值，是由它的 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性決定。  如同其他屬性一般，您可以為這個控制項的值撰寫條件式測試。  設定 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性後，您可以撰寫程式碼對它執行作業來直接調整其值，也可以呼叫 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> 和 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> 方法進行調整。  
  
### 若要設定數值  
  
1.  在程式碼或 \[屬性\] 視窗中，將值指派給 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性。  
  
    ```vb  
    NumericUpDown1.Value = 55  
  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     \-或\-  
  
2.  呼叫 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> 或 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> 方法，依 <xref:System.Windows.Forms.NumericUpDown.Increment%2A> 屬性指定的數量增加或減少值。  
  
    ```vb  
    NumericUpDown1.UpButton()  
  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### 若要傳回數值  
  
-   在程式碼中存取 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性。  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.NumericUpDown>   
 <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=fullName>   
 [NumericUpDown 控制項](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)   
 [NumericUpDown 控制項概觀](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)