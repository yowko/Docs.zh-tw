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
ms.openlocfilehash: 8a2429049acf1a22edde8d132ece17da4e91f1db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759826"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="0878e-102">何時使用 Windows Form ComboBox 取代 ListBox</span><span class="sxs-lookup"><span data-stu-id="0878e-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="0878e-103"><xref:System.Windows.Forms.ComboBox>而<xref:System.Windows.Forms.ListBox>控制項具有類似的行為，和在某些情況下可能可以互換。</span><span class="sxs-lookup"><span data-stu-id="0878e-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="0878e-104">有些的時候，不過，當其中一種是一項工作更適合。</span><span class="sxs-lookup"><span data-stu-id="0878e-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="0878e-105">一般而言，下拉式方塊時，適當沒有建議的選項清單和清單方塊適合，當您想要限制清單上的輸入。</span><span class="sxs-lookup"><span data-stu-id="0878e-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="0878e-106">下拉式方塊中將包含文字方塊欄位，因此可以在輸入不在清單上的選項。</span><span class="sxs-lookup"><span data-stu-id="0878e-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="0878e-107">例外狀況時，<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>屬性設定為<xref:System.Windows.Forms.ComboBoxStyle.DropDownList>。</span><span class="sxs-lookup"><span data-stu-id="0878e-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="0878e-108">在此情況下，控制項就會選取項目，如果您輸入其第一個字母。</span><span class="sxs-lookup"><span data-stu-id="0878e-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="0878e-109">此外，下拉式方塊會節省空間，在表單上。</span><span class="sxs-lookup"><span data-stu-id="0878e-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="0878e-110">因為未顯示的完整清單，直到使用者按一下向下箭號，下拉式方塊可以輕鬆地納入小空間，清單方塊會符合。</span><span class="sxs-lookup"><span data-stu-id="0878e-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="0878e-111">例外狀況時，<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>屬性設定為<xref:System.Windows.Forms.ComboBoxStyle.Simple>： 會顯示完整的清單，並佔用更多的空間比清單方塊的下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="0878e-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0878e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0878e-112">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="0878e-113">如何：新增和移除項目從 Windows Form 的 ComboBox、 ListBox 或 CheckedListBox 控制項</span><span class="sxs-lookup"><span data-stu-id="0878e-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="0878e-114">如何：排序內容的 Windows Forms 的 ComboBox、 ListBox 或 CheckedListBox 控制項</span><span class="sxs-lookup"><span data-stu-id="0878e-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="0878e-115">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="0878e-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
