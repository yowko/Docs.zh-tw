---
title: 作法：在 ComboBox 控制項中建立各種大小的文字
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
ms.openlocfilehash: 7c0dc40f6cac0af1f88e72089865caa3a17fcf2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914740"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>作法：在 ComboBox 控制項中建立各種大小的文字
這個範例示範<xref:System.Windows.Forms.ComboBox>控制項中文字的自訂繪製。 當專案符合特定準則時, 它會以較大的字型繪製並變成紅色。  
  
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
  
- Windows form。  
  
- 名<xref:System.Windows.Forms.ComboBox>為`ListBox1`的控制項<xref:System.Windows.Forms.ComboBox.Items%2A> , 其屬性中有三個專案。 在此範例中, 這三個專案`"One", Two", and Three"`的名稱為。 的<xref:System.Windows.Forms.ComboBox.DrawMode%2A> <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>屬性必須設定為。`ComboBox1`  
  
    > [!NOTE]
    > 這項技術也適用于<xref:System.Windows.Forms.ListBox>控制項, 您可以將<xref:System.Windows.Forms.ListBox>取代為<xref:System.Windows.Forms.ComboBox>。  
  
- <xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [使用內建主控描繪支援的控制項](controls-with-built-in-owner-drawing-support.md)
- [ListBox 控制項](listbox-control-windows-forms.md)
- [ComboBox 控制項](combobox-control-windows-forms.md)
