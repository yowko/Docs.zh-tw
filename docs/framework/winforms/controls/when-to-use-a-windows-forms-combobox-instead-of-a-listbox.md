---
title: ComboBox 與 ListBox 的比較
description: 瞭解如何使用 Windows Forms ComboBox 和 Windows Forms ListBox，並瞭解如何判斷其中一個或另一個較適合某項工作。
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
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174415"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="592d2-103">何時使用 Windows Form ComboBox 取代 ListBox</span><span class="sxs-lookup"><span data-stu-id="592d2-103">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="592d2-104"><xref:System.Windows.Forms.ComboBox>和 <xref:System.Windows.Forms.ListBox> 控制項具有類似的行為，在某些情況下可互換。</span><span class="sxs-lookup"><span data-stu-id="592d2-104">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="592d2-105">不過，有時候其中一個或另一個較適合某項工作。</span><span class="sxs-lookup"><span data-stu-id="592d2-105">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="592d2-106">一般來說，當有建議的挑選清單時，下拉式方塊是適當的，而且當您想要將輸入限制在清單上的內容時，清單方塊是適當的。</span><span class="sxs-lookup"><span data-stu-id="592d2-106">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="592d2-107">下拉式方塊包含文字方塊欄位，因此不在清單上的選擇可以輸入。</span><span class="sxs-lookup"><span data-stu-id="592d2-107">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="592d2-108">當屬性設定為時，就會發生例外狀況 <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> 。</span><span class="sxs-lookup"><span data-stu-id="592d2-108">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="592d2-109">在這種情況下，如果您輸入專案的第一個字母，控制項就會選取它。</span><span class="sxs-lookup"><span data-stu-id="592d2-109">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="592d2-110">此外，下拉式方塊會在表單上儲存空間。</span><span class="sxs-lookup"><span data-stu-id="592d2-110">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="592d2-111">因為在使用者按一下向下箭號之前，不會顯示完整清單，所以下拉式方塊可以輕鬆地放入清單方塊無法容納的小型空間中。</span><span class="sxs-lookup"><span data-stu-id="592d2-111">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="592d2-112">當屬性設定為時，就會發生例外狀況 <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> <xref:System.Windows.Forms.ComboBoxStyle.Simple> ：顯示完整清單，而下拉式方塊所佔用的空間比清單方塊還多。</span><span class="sxs-lookup"><span data-stu-id="592d2-112">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="592d2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="592d2-113">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="592d2-114">操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目</span><span class="sxs-lookup"><span data-stu-id="592d2-114">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="592d2-115">如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容</span><span class="sxs-lookup"><span data-stu-id="592d2-115">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="592d2-116">用來列出選項的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="592d2-116">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
