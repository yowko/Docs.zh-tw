---
title: 排序 ComboBox、ListBox 或 CheckedListBox 控制項的內容
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: dee969d777edf76434622fe632f7e934987a1dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742961"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容
Windows Forms 控制項不會在資料系結時排序。 若要顯示已排序的資料，請使用支援排序的資料來源，然後讓資料來源進行排序。 支援排序的資料來源包括資料檢視、資料檢視管理員和已排序陣列。  
  
 如果控制項不是資料系結，您可以排序它。  
  
### <a name="to-sort-the-list"></a>排序清單  
  
1. 將 `Sorted` 屬性設定為 `true`。  
  
     此設定會重新置放所有現有清單專案的排序次序。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Windows Forms 資料繫結](../windows-forms-data-binding.md)
- [操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](add-and-remove-items-from-a-wf-combobox.md)
- [何時使用 Windows Forms ComboBox 取代 ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)
