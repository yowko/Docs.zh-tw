---
title: "何時使用 Windows Form ComboBox 取代 ListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b4eb1ce70b1ec4b249eb126b608c9f8578d327c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>何時使用 Windows Form ComboBox 取代 ListBox
<xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.ListBox>控制項具有類似的行為，並在某些情況下可能會互換。 但有些的時候，不過，當其中一個是更適合工作。  
  
 一般而言，下拉式方塊是適當的建議的選擇清單，而且當您想要限制清單上的輸入時，清單方塊是適當時。 下拉式方塊包含文字欄位，因此您可以依照輸入不在清單中選擇。 例外狀況是當<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>屬性設定為<xref:System.Windows.Forms.ComboBoxStyle.DropDownList>。 在此情況下，控制項就會選取項目，如果您輸入其第一個字母。  
  
 此外，下拉式方塊會節省表單空間。 未顯示的完整清單，直到使用者按一下向下箭號，因為下拉式方塊可以輕易地容納小的空間，其中不會放在清單方塊中。 例外狀況時，<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>屬性設定為<xref:System.Windows.Forms.ComboBoxStyle.Simple>： 完整的清單隨即顯示，且會佔用更多空間，而不是清單方塊的下拉式方塊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [用來列出選項的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
