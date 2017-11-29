---
title: "如何：在 ComboBox 控制項中建立各種大小的文字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6f0dcfd24414ef868a1a5414af4fcde1b9a14ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>如何：在 ComboBox 控制項中建立各種大小的文字
這個範例會示範自訂繪圖中的文字<xref:System.Windows.Forms.ComboBox>控制項。 當項目符合特定準則時，它是在較大的字型中繪製，變成紅色。  
  
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
  
-   Windows form。  
  
-   A<xref:System.Windows.Forms.ComboBox>控制項，名為`ListBox1`與中的三個項目<xref:System.Windows.Forms.ComboBox.Items%2A>屬性。 在此範例中，三個項目會命名為`"One", Two", and Three"`。 <xref:System.Windows.Forms.ComboBox.DrawMode%2A>屬性`ComboBox1`必須設為<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>。  
  
    > [!NOTE]
    >  這項技術也會適用於<xref:System.Windows.Forms.ListBox>控制項，您可以取代<xref:System.Windows.Forms.ListBox>如<xref:System.Windows.Forms.ComboBox>。  
  
-   <xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ComboBox.DrawItem>  
 <xref:System.Windows.Forms.DrawItemEventArgs>  
 <xref:System.Windows.Forms.ComboBox.MeasureItem>  
 [使用內建主控描繪支援的控制項](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [ListBox 控制項](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)  
 [ComboBox 控制項](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
