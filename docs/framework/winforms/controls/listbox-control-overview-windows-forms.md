---
title: ListBox 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: 1abf8bea5c786f2ce326631370fa294ada09a92c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745176"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.ListBox> 控制項會顯示使用者可以從中選取一個或多個專案的清單。 如果專案總數超過可顯示的數目，捲軸就會自動加入至 [<xref:System.Windows.Forms.ListBox>] 控制項。 當 [<xref:System.Windows.Forms.ListBox.MultiColumn%2A>] 屬性設定為 [`true`] 時，清單方塊會顯示多個資料行中的專案，而且會顯示水準捲軸。 當 [<xref:System.Windows.Forms.ListBox.MultiColumn%2A>] 屬性設定為 [`false`] 時，清單方塊會顯示單一資料行中的專案，並顯示垂直捲動條。 當 <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> 設定為 [`true`] 時，不論專案的數目為何，都會出現捲軸。 <xref:System.Windows.Forms.ListBox.SelectionMode%2A> 屬性會決定一次可以選取多少個清單專案。  
  
## <a name="ways-to-change-the-listbox-control"></a>變更 ListBox 控制項的方式  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 屬性會傳回對應到清單方塊中第一個選取專案的整數值。 您可以藉由變更程式碼中的 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值，以程式設計方式變更選取的專案。清單中的對應專案會在 Windows Form 上以反白顯示。 如果未選取任何專案，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值為-1。 如果選取清單中的第一個專案，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值為0。 選取多個專案時，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值會反映清單中第一個出現的選取專案。 <xref:System.Windows.Forms.ListBox.SelectedItem%2A> 屬性類似于 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>，但會傳回專案本身，通常是字串值。 [<xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A>] 屬性會反映清單中的專案數，而 [<xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A>] 屬性的值一律會超過最大的可能 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 值，因為 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 是以零為基底。  
  
 若要加入或刪除 <xref:System.Windows.Forms.ListBox> 控制項中的專案，請使用 <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>、<xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>、<xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> 或 <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> 方法。 或者，您也可以在設計階段使用 <xref:System.Windows.Forms.ListBox.Items%2A> 屬性，將專案加入至清單。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ListBox>
- [操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](add-and-remove-items-from-a-wf-combobox.md)
- [操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [操作說明：將 Windows Forms ComboBox 或 ListBox 控制項繫結至資料](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [ComboBox 控制項概觀](combobox-control-overview-windows-forms.md)
- [CheckedListBox 控制項概觀](checkedlistbox-control-overview-windows-forms.md)
- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)
- [操作說明：為 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表](create-a-lookup-table-for-a-wf-combobox-listbox.md)
