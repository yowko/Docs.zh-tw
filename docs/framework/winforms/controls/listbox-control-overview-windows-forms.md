---
title: ListBox 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: d4cb423a6f32778695abeae725da9755b610d209
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537560"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.ListBox>控制項會顯示的清單，使用者可以從中選取一個或多個項目。 如果項目總數超過可以顯示的數字，捲軸會自動加入<xref:System.Windows.Forms.ListBox>控制項。 當<xref:System.Windows.Forms.ListBox.MultiColumn%2A>屬性設定為`true`，清單方塊會顯示在多個資料行中的項目，水平捲軸會顯示。 當<xref:System.Windows.Forms.ListBox.MultiColumn%2A>屬性設定為`false`，清單方塊會顯示單一資料行中的項目，而垂直捲軸會顯示。 當<xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A>設`true`，捲軸出現不論項目數目。 <xref:System.Windows.Forms.ListBox.SelectionMode%2A>屬性會決定可以一次選取清單項目數目。  
  
## <a name="ways-to-change-the-listbox-control"></a>若要變更清單方塊控制項的方式  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>屬性會傳回整數值，對應到第一個選取的項目，清單方塊中。 您可以變更，以程式設計的方式變更選取的項目<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>程式碼中的值，則為對應的項目在清單中會出現在 Windows Form 上反白顯示。 如果未不選取任何項目，則<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值為-1。 如果選取清單中的第一個項目，則<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值為 0。 多個選取項目時，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值反映會出現在清單中第一個選取的項目。 <xref:System.Windows.Forms.ListBox.SelectedItem%2A>屬性是類似於<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>，但傳回的項目本身，通常是字串值。 <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A>屬性會反映在清單中的項目數，而<xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A>屬性一律會是一個以上的最大可能<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值，因為<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>以零為起始。  
  
 若要加入或刪除的項目<xref:System.Windows.Forms.ListBox>控制，請使用<xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>， <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>，<xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A>或<xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A>方法。 或者，您可以加入項目清單使用<xref:System.Windows.Forms.ListBox.Items%2A>在設計階段屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ListBox>  
 [操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [操作說明：將 Windows Forms ComboBox 或 ListBox 控制項繫結至資料](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [ComboBox 控制項概觀](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [CheckedListBox 控制項概觀](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [用來列出選項的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [操作說明：為 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
