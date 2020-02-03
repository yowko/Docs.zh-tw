---
title: 使用 NumericUpDown 控制項設定和傳回數值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: a0b264fec9619b467c293bcb96278c4517775ac3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743030"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>如何：使用 Windows Form NumericUpDown 控制項設定和傳回數值
Windows Forms <xref:System.Windows.Forms.NumericUpDown> 控制項的數值是由其 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性所決定。 您可以撰寫控制項值的條件式測試，就像使用任何其他屬性一樣。 設定 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性之後，您可以撰寫程式碼來直接調整它，以在其上執行作業，或者您可以呼叫 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> 和 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> 方法。  
  
### <a name="to-set-the-numeric-value"></a>若要設定數值  
  
1. 在程式碼或屬性視窗中，將值指派給 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性。  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     -或-  
  
2. 呼叫 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> 或 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> 方法，以 <xref:System.Windows.Forms.NumericUpDown.Increment%2A> 屬性中指定的數量來增加或減少值。  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>傳回數值  
  
- 存取程式碼中的 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [NumericUpDown 控制項](numericupdown-control-windows-forms.md)
- [NumericUpDown 控制項概觀](numericupdown-control-overview-windows-forms.md)
