---
title: HOW TO：Windows Form NumericUpDown 控制項設定格式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: e5c387fe593082e08ad39cb4582c946ca986a79e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713926"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>HOW TO：Windows Form NumericUpDown 控制項設定格式
您可以設定 Windows Form 中值的顯示方式<xref:System.Windows.Forms.NumericUpDown>控制項。 <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>屬性可決定多少數字的小數點後，預設值為 0。 <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>屬性會決定是否會每隔三個十進位數字之間插入分隔符號; 預設值是`false`。 控制項可以顯示值以十六進位方式而不是十進位格式，如果<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>屬性設定為`true`; 預設值是`false`。  
  
### <a name="to-format-the-numeric-value"></a>若要格式化的數值  
  
-   藉由設定顯示十進位值<xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>屬性設為整數並設定<xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>屬性設`true`或`false`。  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     -或-  
  
-   藉由設定顯示十六進位值<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>屬性設`true`。  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    >  即使值顯示為十六進位形式，任何測試您對<xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性將會測試其十進位值。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown 控制項](numericupdown-control-windows-forms.md)
- [NumericUpDown 控制項概觀](numericupdown-control-overview-windows-forms.md)
