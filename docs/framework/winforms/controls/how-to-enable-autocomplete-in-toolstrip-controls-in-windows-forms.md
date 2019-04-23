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
ms.openlocfilehash: d7919bf87444ef6c4a64ee236356e762da14853f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307895"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a><span data-ttu-id="035bb-102">HOW TO：啟用 Windows Form 中 ToolStrip 控制項的 AutoComplete</span><span class="sxs-lookup"><span data-stu-id="035bb-102">How to: Enable AutoComplete in ToolStrip Controls in Windows Forms</span></span>
<span data-ttu-id="035bb-103">下列程序結合<xref:System.Windows.Forms.ToolStripLabel>與<xref:System.Windows.Forms.ToolStripComboBox>可被拉顯示一份項目，例如最近瀏覽的網站。</span><span class="sxs-lookup"><span data-stu-id="035bb-103">The following procedure combines a <xref:System.Windows.Forms.ToolStripLabel> with a <xref:System.Windows.Forms.ToolStripComboBox> that can be dropped down to show a list of items, such as recently visited Web sites.</span></span> <span data-ttu-id="035bb-104">如果使用者輸入的字元符合其中一個項目清單中的第一個字元，會立即顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="035bb-104">If the user types a character that matches the first character of one of the items in the list, the item is immediately displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="035bb-105">適用於自動完成`ToolStrip`中相同的方式，它適用於傳統控制項這類控制項<xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="035bb-105">Automatic completion works with `ToolStrip` controls in the same way that it works with traditional controls such as <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a><span data-ttu-id="035bb-106">若要啟用自動完成中的 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="035bb-106">To enable AutoComplete in a ToolStrip control</span></span>  
  
1. <span data-ttu-id="035bb-107">建立<xref:System.Windows.Forms.ToolStrip>控制項，並將項目加入它。</span><span class="sxs-lookup"><span data-stu-id="035bb-107">Create a <xref:System.Windows.Forms.ToolStrip> control and add items to it.</span></span>  
  
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
  
2. <span data-ttu-id="035bb-108">設定<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>屬性的標籤和下拉式方塊<xref:System.Windows.Forms.ToolStripItemOverflow.Never>使清單一律可用，而不論表單的大小為何。</span><span class="sxs-lookup"><span data-stu-id="035bb-108">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the label and the combo box to <xref:System.Windows.Forms.ToolStripItemOverflow.Never> so that the list is always available regardless of the form's size.</span></span>  
  
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
  
3. <span data-ttu-id="035bb-109">將文字加入至項目集合的<xref:System.Windows.Forms.ToolStripComboBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="035bb-109">Add words to the Items collection of the <xref:System.Windows.Forms.ToolStripComboBox> control.</span></span>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. <span data-ttu-id="035bb-110">設定<xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>屬性的下拉式方塊<xref:System.Windows.Forms.AutoCompleteMode.Append>。</span><span class="sxs-lookup"><span data-stu-id="035bb-110">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. <span data-ttu-id="035bb-111">設定<xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>屬性的下拉式方塊<xref:System.Windows.Forms.AutoCompleteSource.ListItems>。</span><span class="sxs-lookup"><span data-stu-id="035bb-111">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="035bb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="035bb-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [<span data-ttu-id="035bb-113">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="035bb-113">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="035bb-114">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="035bb-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="035bb-115">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="035bb-115">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
