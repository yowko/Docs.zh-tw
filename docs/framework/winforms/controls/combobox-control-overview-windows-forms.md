---
title: "ComboBox 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 801ebb97c6ee52ce52bbb8f96a07d55e68ca6f1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.ComboBox>控制項用來在下拉式清單方塊中顯示資料。 根據預設，<xref:System.Windows.Forms.ComboBox>控制項出現在兩個部分： 上半部是文字方塊，可讓使用者輸入的清單項目。 第二個部分是清單方塊會顯示，使用者可以從中選取一個項目清單。 如需其他樣式組合方塊的詳細資訊，請參閱[何時使用 Windows Form ComboBox Instead of ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)。  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>屬性會傳回整數值，對應至選取的清單項目。 您可以變更，以程式設計的方式變更選取的項目<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>程式碼中的值，則為對應的項目在清單中會出現在下拉式方塊的文字方塊部分。 如果未不選取任何項目，則<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>值為-1。 如果選取清單中的第一個項目，然後在<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>值為 0。 <xref:System.Windows.Forms.ComboBox.SelectedItem%2A>屬性是類似於<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>，但傳回的項目本身，通常是字串值。 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A>屬性會反映在清單中的項目數，而<xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A>屬性一律會是一個以上的最大可能<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>值，因為<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>以零為起始。  
  
 若要加入或刪除的項目<xref:System.Windows.Forms.ComboBox>控制，請使用<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>， <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>，<xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A>或<xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A>方法。 或者，您可以加入項目清單使用<xref:System.Windows.Forms.ComboBox.Items%2A>設計工具中的屬性。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.ComboBox>  
 [ListBox 控制項概觀](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [何時使用 Windows Forms ComboBox 取代 ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [操作說明：在 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定的項目](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)  
 [操作說明：將 Windows Forms ComboBox 或 ListBox 控制項繫結至資料](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [用來列出選項的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [操作說明：為 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
