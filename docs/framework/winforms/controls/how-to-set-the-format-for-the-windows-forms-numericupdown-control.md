---
title: 作法：設定 Windows Forms NumericUpDown 控制項的格式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949155"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>HOW TO：設定 Windows Forms NumericUpDown 控制項的格式
您可以設定在 Windows Forms <xref:System.Windows.Forms.NumericUpDown>控制項中顯示值的方式。 <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>屬性會決定小數點後出現多少數位, 預設值為0。 屬性會決定是否要在每三個小數位數之間插入分隔符號, 預設值`false`為。 <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> 如果<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>屬性設定為`true`, 控制項可以顯示十六進位而不是十進位格式的值; 預設值為`false`。  
  
### <a name="to-format-the-numeric-value"></a>若要格式化數值  
  
- 將<xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>屬性設定為整數, 並<xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>將屬性設定為`true`或`false`, 以顯示十進位值。  
  
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
  
- 將<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>屬性設定為, 以`true`顯示十六進位值。  
  
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
    > 即使值在表單上顯示為十六進位, 在<xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性上執行的任何測試都會測試其十進位值。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown 控制項](numericupdown-control-windows-forms.md)
- [NumericUpDown 控制項概觀](numericupdown-control-overview-windows-forms.md)
