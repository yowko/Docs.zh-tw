---
title: HOW TO：設定和傳回數值的值，使用 Windows Forms NumericUpDown 控制項
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
ms.openlocfilehash: 166b14fca2009d0609fa48a5f07912b33f074071
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703197"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>HOW TO：設定和傳回數值的值，使用 Windows Forms NumericUpDown 控制項
Windows Form 的數值<xref:System.Windows.Forms.NumericUpDown>控制項由其<xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性。 您可以撰寫條件式測試控制項的值，如同任何其他屬性。 一次<xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性設定，您可以調整它直接撰寫程式碼來執行作業，或您可以呼叫<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>和<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>方法。  
  
### <a name="to-set-the-numeric-value"></a>若要設定的數值  
  
1.  指派值給<xref:System.Windows.Forms.NumericUpDown.Value%2A>在程式碼，或在 [屬性] 視窗中的屬性。  
  
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
  
2.  呼叫<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>或是<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>方法，以增加或減少值中指定的數量<xref:System.Windows.Forms.NumericUpDown.Increment%2A>屬性。  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>傳回數字的值  
  
-   存取<xref:System.Windows.Forms.NumericUpDown.Value%2A>在程式碼中的屬性。  
  
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
