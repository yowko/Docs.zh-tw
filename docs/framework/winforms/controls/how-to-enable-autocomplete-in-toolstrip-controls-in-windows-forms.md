---
title: 如何：使用 ToolStrip 控制項中的工具提示
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
ms.openlocfilehash: 18b17aaea9d2354c03bb43f3fdd8d3779697cf58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142014"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a><span data-ttu-id="6f310-102">如何：啟用 Windows Form 中 ToolStrip 控制項的 AutoComplete</span><span class="sxs-lookup"><span data-stu-id="6f310-102">How to: Enable AutoComplete in ToolStrip Controls in Windows Forms</span></span>
<span data-ttu-id="6f310-103">以下過程將 和<xref:System.Windows.Forms.ToolStripLabel><xref:System.Windows.Forms.ToolStripComboBox>可以向下刪除的 將 合併為 顯示專案清單（如最近訪問的網站）。</span><span class="sxs-lookup"><span data-stu-id="6f310-103">The following procedure combines a <xref:System.Windows.Forms.ToolStripLabel> with a <xref:System.Windows.Forms.ToolStripComboBox> that can be dropped down to show a list of items, such as recently visited Web sites.</span></span> <span data-ttu-id="6f310-104">如果使用者鍵入與清單中某一項的第一個字元匹配的字元，則該項將立即顯示。</span><span class="sxs-lookup"><span data-stu-id="6f310-104">If the user types a character that matches the first character of one of the items in the list, the item is immediately displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f310-105">自動完成的工作方式`ToolStrip`與使用傳統控制項（如 和<xref:System.Windows.Forms.ComboBox><xref:System.Windows.Forms.TextBox>） 相同。</span><span class="sxs-lookup"><span data-stu-id="6f310-105">Automatic completion works with `ToolStrip` controls in the same way that it works with traditional controls such as <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a><span data-ttu-id="6f310-106">在工具條控制項中啟用自動完成</span><span class="sxs-lookup"><span data-stu-id="6f310-106">To enable AutoComplete in a ToolStrip control</span></span>  
  
1. <span data-ttu-id="6f310-107">創建控制項<xref:System.Windows.Forms.ToolStrip>並將其添加項。</span><span class="sxs-lookup"><span data-stu-id="6f310-107">Create a <xref:System.Windows.Forms.ToolStrip> control and add items to it.</span></span>  
  
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
  
2. <span data-ttu-id="6f310-108">將<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>標籤和下拉式列示方塊的屬性設置為<xref:System.Windows.Forms.ToolStripItemOverflow.Never>，以便無論表單的大小如何，清單始終可用。</span><span class="sxs-lookup"><span data-stu-id="6f310-108">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the label and the combo box to <xref:System.Windows.Forms.ToolStripItemOverflow.Never> so that the list is always available regardless of the form's size.</span></span>  
  
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
  
3. <span data-ttu-id="6f310-109">向<xref:System.Windows.Forms.ToolStripComboBox>控制項的"項"集合添加單詞。</span><span class="sxs-lookup"><span data-stu-id="6f310-109">Add words to the Items collection of the <xref:System.Windows.Forms.ToolStripComboBox> control.</span></span>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. <span data-ttu-id="6f310-110">將<xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>下拉式列示方塊的屬性設置為<xref:System.Windows.Forms.AutoCompleteMode.Append>。</span><span class="sxs-lookup"><span data-stu-id="6f310-110">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. <span data-ttu-id="6f310-111">將<xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>下拉式列示方塊的屬性設置為<xref:System.Windows.Forms.AutoCompleteSource.ListItems>。</span><span class="sxs-lookup"><span data-stu-id="6f310-111">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6f310-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f310-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [<span data-ttu-id="6f310-113">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="6f310-113">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="6f310-114">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="6f310-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="6f310-115">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="6f310-115">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
