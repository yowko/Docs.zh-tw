---
title: HOW TO：排序 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項內容
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: 4db1c133aabe39232a891183356e9c1b712f5cc8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150601"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>HOW TO：排序 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項內容
在資料繫結時，請不要排序 Windows Form 控制項。 若要顯示已排序的資料，請使用支援排序的資料來源，則有 排序的資料來源。 支援排序的資料來源是資料的檢視，檢視管理員，與排序陣列的資料。  
  
 如果控制項不是資料繫結，您就可以進行排序。  
  
### <a name="to-sort-the-list"></a>若要排序的清單  
  
1.  將 `Sorted` 屬性設定為 `true`。  
  
     此設定會依排序順序，重新調整所有現有的清單項目。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Windows Form 資料繫結](../windows-forms-data-binding.md)
- [HOW TO：在 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項中新增和移除項目](add-and-remove-items-from-a-wf-combobox.md)
- [何時使用 Windows Form ComboBox 取代 ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [用來列出選項的 Windows Form 控制項](windows-forms-controls-used-to-list-options.md)
