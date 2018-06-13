---
title: 如何：啟用 Windows Form 中 ToolStrip 控制項的 AutoComplete
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
ms.openlocfilehash: c5836b03ad185d4a31a24dfea46db54214ac54b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532534"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a><span data-ttu-id="bf845-102">如何：啟用 Windows Form 中 ToolStrip 控制項的 AutoComplete</span><span class="sxs-lookup"><span data-stu-id="bf845-102">How to: Enable AutoComplete in ToolStrip Controls in Windows Forms</span></span>
<span data-ttu-id="bf845-103">下列程序結合<xref:System.Windows.Forms.ToolStripLabel>與<xref:System.Windows.Forms.ToolStripComboBox>，可以卸除向下顯示項目清單，例如最近瀏覽的網站。</span><span class="sxs-lookup"><span data-stu-id="bf845-103">The following procedure combines a <xref:System.Windows.Forms.ToolStripLabel> with a <xref:System.Windows.Forms.ToolStripComboBox> that can be dropped down to show a list of items, such as recently visited Web sites.</span></span> <span data-ttu-id="bf845-104">如果使用者輸入的字元符合其中一個項目在清單中的第一個字元，也會立即顯示項目。</span><span class="sxs-lookup"><span data-stu-id="bf845-104">If the user types a character that matches the first character of one of the items in the list, the item is immediately displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf845-105">自動完成可搭配`ToolStrip`控制項相同的方式，將它用於傳統控制項例如<xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="bf845-105">Automatic completion works with `ToolStrip` controls in the same way that it works with traditional controls such as <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a><span data-ttu-id="bf845-106">ToolStrip 控制項中啟用 「 自動完成 」</span><span class="sxs-lookup"><span data-stu-id="bf845-106">To enable AutoComplete in a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="bf845-107">建立<xref:System.Windows.Forms.ToolStrip>控制和項目加入。</span><span class="sxs-lookup"><span data-stu-id="bf845-107">Create a <xref:System.Windows.Forms.ToolStrip> control and add items to it.</span></span>  
  
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
  
2.  <span data-ttu-id="bf845-108">設定<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>標籤與下拉式方塊，以屬性<xref:System.Windows.Forms.ToolStripItemOverflow.Never>，因此清單一律會使用不論表單的大小。</span><span class="sxs-lookup"><span data-stu-id="bf845-108">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the label and the combo box to <xref:System.Windows.Forms.ToolStripItemOverflow.Never> so that the list is always available regardless of the form's size.</span></span>  
  
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
  
3.  <span data-ttu-id="bf845-109">將單字加入到項目集合的<xref:System.Windows.Forms.ToolStripComboBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="bf845-109">Add words to the Items collection of the <xref:System.Windows.Forms.ToolStripComboBox> control.</span></span>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4.  <span data-ttu-id="bf845-110">設定<xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>屬性的下拉式方塊，以<xref:System.Windows.Forms.AutoCompleteMode.Append>。</span><span class="sxs-lookup"><span data-stu-id="bf845-110">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5.  <span data-ttu-id="bf845-111">設定<xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>屬性的下拉式方塊，以<xref:System.Windows.Forms.AutoCompleteSource.ListItems>。</span><span class="sxs-lookup"><span data-stu-id="bf845-111">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bf845-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf845-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripLabel>  
 <xref:System.Windows.Forms.ToolStripComboBox>  
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>  
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>  
 [<span data-ttu-id="bf845-113">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="bf845-113">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="bf845-114">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="bf845-114">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="bf845-115">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="bf845-115">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
