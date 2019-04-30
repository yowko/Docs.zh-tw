---
title: ListBox 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: f70246d4a4d158815ee9662036eca8edeb891d85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012889"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.ListBox>控制項顯示使用者可以從中選取一或多個項目清單。 如果項目總數超過可顯示的數字，捲軸會自動新增至<xref:System.Windows.Forms.ListBox>控制項。 當<xref:System.Windows.Forms.ListBox.MultiColumn%2A>屬性設定為`true`，清單方塊會顯示在多個資料行中的項目，且水平捲軸會顯示。 當<xref:System.Windows.Forms.ListBox.MultiColumn%2A>屬性設定為`false`，清單方塊會顯示單一資料行中的項目，而垂直捲軸會顯示。 當<xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A>設為`true`，捲軸出現，不論項目數目。 <xref:System.Windows.Forms.ListBox.SelectionMode%2A>屬性會決定可以一次選取多少個清單項目。  
  
## <a name="ways-to-change-the-listbox-control"></a>若要變更清單方塊控制項的方式  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>屬性會傳回整數值，對應到第一個選取的項目，在清單方塊中。 您可以變更，以程式設計方式變更選取的項目<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>程式碼中的值; 將 Windows Form 上反白顯示清單中對應的項目。 如果未不選取任何項目，則<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值為-1。 如果選取清單中的第一個項目，則<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值為 0。 多個選取項目時，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值會反映會出現在清單中第一個選取的項目。 <xref:System.Windows.Forms.ListBox.SelectedItem%2A>屬性是類似於<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>，但傳回的項目本身，通常是字串值。 <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A>屬性會反映在清單中的項目數，而<xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A>屬性一律為一個以上的最大的可能<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值，因為<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>以零為起始。  
  
 若要加入或刪除中的項目<xref:System.Windows.Forms.ListBox>控制，請使用<xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>， <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>，<xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A>或<xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A>方法。 或者，您可以將項目加入清單使用<xref:System.Windows.Forms.ListBox.Items%2A>在設計階段屬性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListBox>
- [如何：新增和移除項目從 Windows Form 的 ComboBox、 ListBox 或 CheckedListBox 控制項](add-and-remove-items-from-a-wf-combobox.md)
- [如何：排序內容的 Windows Forms 的 ComboBox、 ListBox 或 CheckedListBox 控制項](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [ComboBox 控制項概觀](combobox-control-overview-windows-forms.md)
- [CheckedListBox 控制項概觀](checkedlistbox-control-overview-windows-forms.md)
- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)
- [如何：Windows form 的 ComboBox、 ListBox 或 CheckedListBox 控制項建立查閱資料表](create-a-lookup-table-for-a-wf-combobox-listbox.md)
