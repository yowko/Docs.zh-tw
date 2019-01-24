---
title: HOW TO：啟用 Windows Form 中 ToolStrip 控制項的 AutoComplete
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
ms.openlocfilehash: cc3ec2dd0bdd7f83b2cd6b8cfaf0cad37238707b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514812"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>HOW TO：啟用 Windows Form 中 ToolStrip 控制項的 AutoComplete
下列程序結合<xref:System.Windows.Forms.ToolStripLabel>與<xref:System.Windows.Forms.ToolStripComboBox>可被拉顯示一份項目，例如最近瀏覽的網站。 如果使用者輸入的字元符合其中一個項目清單中的第一個字元，會立即顯示的項目。  
  
> [!NOTE]
>  適用於自動完成`ToolStrip`中相同的方式，它適用於傳統控制項這類控制項<xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.TextBox>。  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>若要啟用自動完成中的 ToolStrip 控制項  
  
1.  建立<xref:System.Windows.Forms.ToolStrip>控制項，並將項目加入它。  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]   
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2.  設定<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>屬性的標籤和下拉式方塊<xref:System.Windows.Forms.ToolStripItemOverflow.Never>使清單一律可用，而不論表單的大小為何。  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3.  將文字加入至項目集合的<xref:System.Windows.Forms.ToolStripComboBox>控制項。  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4.  設定<xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>屬性的下拉式方塊<xref:System.Windows.Forms.AutoCompleteMode.Append>。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5.  設定<xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>屬性的下拉式方塊<xref:System.Windows.Forms.AutoCompleteSource.ListItems>。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
