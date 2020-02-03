---
title: ComboBox 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: 9fb270d7787902872a32a87c140316f756bd48aa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743842"
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.ComboBox> 控制項是用來在下拉式方塊中顯示資料。 根據預設，<xref:System.Windows.Forms.ComboBox> 控制項會出現在兩個部分中：最上方的部分是允許使用者輸入清單專案的文字方塊。 第二個部分是清單方塊，其中顯示使用者可以從中選取一個專案的清單。 如需下拉式方塊其他樣式的詳細資訊，請參閱[When To Use a Windows Forms ComboBox，而不是 ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)。  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 屬性會傳回對應于所選取清單專案的整數值。 您可以藉由變更程式碼中的 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 值，以程式設計方式變更選取的專案。清單中的對應專案會出現在下拉式方塊的文字方塊部分中。 如果未選取任何專案，<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 值為-1。 如果選取清單中的第一個專案，則 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 值為0。 <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> 屬性類似于 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>，但會傳回專案本身，通常是字串值。 [<xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A>] 屬性會反映清單中的專案數，而 [<xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A>] 屬性的值一律會超過最大的可能 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 值，因為 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 是以零為基底。  
  
 若要加入或刪除 <xref:System.Windows.Forms.ComboBox> 控制項中的專案，請使用 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> 或 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> 方法。 或者，您可以使用設計工具中的 [<xref:System.Windows.Forms.ComboBox.Items%2A>] 屬性，將專案加入至清單中。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ComboBox>
- [ListBox 控制項概觀](listbox-control-overview-windows-forms.md)
- [何時使用 Windows Forms ComboBox 取代 ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](add-and-remove-items-from-a-wf-combobox.md)
- [操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [操作說明：在 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定的項目](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [操作說明：將 Windows Forms ComboBox 或 ListBox 控制項繫結至資料](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)
- [操作說明：為 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表](create-a-lookup-table-for-a-wf-combobox-listbox.md)
