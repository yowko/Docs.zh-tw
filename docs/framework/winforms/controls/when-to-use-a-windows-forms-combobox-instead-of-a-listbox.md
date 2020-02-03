---
title: ComboBox 與 ListBox 的比較
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
ms.openlocfilehash: 7087760a393bb58d83d899c1741c745fb28585bb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739936"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>何時使用 Windows Form ComboBox 取代 ListBox
<xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.ListBox> 控制項具有類似的行為，而且在某些情況下可能會互換。 不過，有時候其中一個或另一個較適合某項工作。  
  
 一般來說，當有建議的挑選清單時，下拉式方塊是適當的，而且當您想要將輸入限制在清單上的內容時，清單方塊是適當的。 下拉式方塊包含文字方塊欄位，因此不在清單上的選擇可以輸入。 當 <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> 屬性設定為 <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>時，就會發生例外狀況。 在這種情況下，如果您輸入專案的第一個字母，控制項就會選取它。  
  
 此外，下拉式方塊會在表單上儲存空間。 因為在使用者按一下向下箭號之前，不會顯示完整清單，所以下拉式方塊可以輕鬆地放入清單方塊無法容納的小型空間中。 當 [<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>] 屬性設定為 [<xref:System.Windows.Forms.ComboBoxStyle.Simple>] 時，就會發生例外狀況：顯示完整清單，而下拉式方塊所佔用的空間比清單方塊還多。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](add-and-remove-items-from-a-wf-combobox.md)
- [操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)
