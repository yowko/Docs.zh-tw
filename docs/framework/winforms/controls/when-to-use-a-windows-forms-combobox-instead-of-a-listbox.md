---
title: 何時使用 Windows Form ComboBox 取代 ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 88b6a6023fbfdd8fa315fcd434357626ea69a9ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537764"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="5f33e-102">何時使用 Windows Form ComboBox 取代 ListBox</span><span class="sxs-lookup"><span data-stu-id="5f33e-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="5f33e-103"><xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.ListBox>控制項具有類似的行為，並在某些情況下可能會互換。</span><span class="sxs-lookup"><span data-stu-id="5f33e-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="5f33e-104">但有些的時候，不過，當其中一個是更適合工作。</span><span class="sxs-lookup"><span data-stu-id="5f33e-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="5f33e-105">一般而言，下拉式方塊是適當的建議的選擇清單，而且當您想要限制清單上的輸入時，清單方塊是適當時。</span><span class="sxs-lookup"><span data-stu-id="5f33e-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="5f33e-106">下拉式方塊包含文字欄位，因此您可以依照輸入不在清單中選擇。</span><span class="sxs-lookup"><span data-stu-id="5f33e-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="5f33e-107">例外狀況是當<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>屬性設定為<xref:System.Windows.Forms.ComboBoxStyle.DropDownList>。</span><span class="sxs-lookup"><span data-stu-id="5f33e-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="5f33e-108">在此情況下，控制項就會選取項目，如果您輸入其第一個字母。</span><span class="sxs-lookup"><span data-stu-id="5f33e-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="5f33e-109">此外，下拉式方塊會節省表單空間。</span><span class="sxs-lookup"><span data-stu-id="5f33e-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="5f33e-110">未顯示的完整清單，直到使用者按一下向下箭號，因為下拉式方塊可以輕易地容納小的空間，其中不會放在清單方塊中。</span><span class="sxs-lookup"><span data-stu-id="5f33e-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="5f33e-111">例外狀況時，<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>屬性設定為<xref:System.Windows.Forms.ComboBoxStyle.Simple>： 完整的清單隨即顯示，且會佔用更多空間，而不是清單方塊的下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="5f33e-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f33e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f33e-112">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="5f33e-113">操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目</span><span class="sxs-lookup"><span data-stu-id="5f33e-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="5f33e-114">操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容</span><span class="sxs-lookup"><span data-stu-id="5f33e-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="5f33e-115">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5f33e-115">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
