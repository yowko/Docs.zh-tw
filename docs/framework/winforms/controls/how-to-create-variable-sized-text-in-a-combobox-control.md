---
title: "如何：在 ComboBox 控制項中建立各種大小的文字 | Microsoft Docs"
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
  - "下拉式方塊, 繪製文字"
  - "ComboBox 控制項 [Windows Form], 繪製自訂文字"
  - "ComboBox 控制項 [Windows Form], 範例 [C#]"
  - "範例 [Windows Form], ComboBox 控制項"
  - "文字, 在下拉式方塊中繪製"
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在 ComboBox 控制項中建立各種大小的文字
這個範例示範 <xref:System.Windows.Forms.ComboBox> 控制項中文字的自訂繪圖。  當項目符合特定準則時，便會以較大的字型繪製該項目並且變成紅色。  
  
## 範例  
  
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
  
## 編譯程式碼  
 這個範例需要：  
  
-   Windows Form。  
  
-   名為  `ListBox1` 、具有 <xref:System.Windows.Forms.ComboBox.Items%2A> 屬性中三個項目的 <xref:System.Windows.Forms.ComboBox> 控制項。  在此範例中，這三個項目名為  `"One", Two", and Three"`。   `ComboBox1`  的 <xref:System.Windows.Forms.ComboBox.DrawMode%2A> 屬性必須設定為 <xref:System.Windows.Forms.DrawMode>。  
  
    > [!NOTE]
    >  這項技術也適用於 <xref:System.Windows.Forms.ListBox> 控制項 — 您可以將 <xref:System.Windows.Forms.ComboBox> 取代為 <xref:System.Windows.Forms.ListBox>。  
  
-   <xref:System.Windows.Forms?displayProperty=fullName> 和 <xref:System.Drawing?displayProperty=fullName> 命名空間的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.ComboBox.DrawItem>   
 <xref:System.Windows.Forms.DrawItemEventArgs>   
 <xref:System.Windows.Forms.ComboBox.MeasureItem>   
 [使用內建主控描繪支援的控制項](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)   
 [ListBox 控制項](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)   
 [ComboBox 控制項](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)