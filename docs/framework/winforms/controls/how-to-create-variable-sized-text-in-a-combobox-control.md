---
title: HOW TO：建立下拉式方塊控制項中的變數文字大小
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: 2a9f6e8a1c96c2a9bf9e56c1c6acefc4181a18dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526986"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>HOW TO：建立下拉式方塊控制項中的變數文字大小
此範例示範自訂繪圖中的文字<xref:System.Windows.Forms.ComboBox>控制項。 當項目符合特定準則時，它是以較大的字型繪製，而且變成紅色。  
  
## <a name="example"></a>範例  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   Windows 表單。  
  
-   A<xref:System.Windows.Forms.ComboBox>控制項，名為`ListBox1`中的三個項目與<xref:System.Windows.Forms.ComboBox.Items%2A>屬性。 在此範例中，三個項目會命名為`"One", Two", and Three"`。 <xref:System.Windows.Forms.ComboBox.DrawMode%2A>的屬性`ComboBox1`必須設為<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>。  
  
    > [!NOTE]
    >  這項技術也是適用於<xref:System.Windows.Forms.ListBox>控制項，您可以使用替代<xref:System.Windows.Forms.ListBox>如<xref:System.Windows.Forms.ComboBox>。  
  
-   <xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [使用內建主控描繪支援的控制項](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)
- [ListBox 控制項](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)
- [ComboBox 控制項](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
