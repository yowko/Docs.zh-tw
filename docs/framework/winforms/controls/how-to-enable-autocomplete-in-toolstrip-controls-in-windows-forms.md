---
title: 作法：在 Windows Forms 的 ToolStrip 控制項中啟用自動完成
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
ms.openlocfilehash: 301f1b156bbaee5c5f7be95e972ee1ebaa83777f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963618"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>作法：在 Windows Forms 的 ToolStrip 控制項中啟用自動完成
下列<xref:System.Windows.Forms.ToolStripLabel> <xref:System.Windows.Forms.ToolStripComboBox>程式會將與結合, 以顯示專案清單, 例如最近造訪的網站。 如果使用者輸入的字元符合清單中其中一個專案的第一個字元, 則會立即顯示該專案。  
  
> [!NOTE]
> 自動完成會使用`ToolStrip`控制項, 其方式與使用傳統控制項<xref:System.Windows.Forms.ComboBox> (例如和<xref:System.Windows.Forms.TextBox>) 相同。  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>若要啟用 ToolStrip 控制項中的自動完成功能  
  
1. <xref:System.Windows.Forms.ToolStrip>建立控制項並在其中新增專案。  
  
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
  
2. 將標籤和下拉式方塊的<xref:System.Windows.Forms.ToolStripItemOverflow.Never> 屬性設定為,讓清單一律可供使用,不論表單的大小為何。<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
  
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
  
3. 將文字加入至<xref:System.Windows.Forms.ToolStripComboBox>控制項的 Items 集合。  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. 將下拉式<xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>方塊的屬性設為。 <xref:System.Windows.Forms.AutoCompleteMode.Append>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. 將下拉式<xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>方塊的屬性設為。 <xref:System.Windows.Forms.AutoCompleteSource.ListItems>  
  
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
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
