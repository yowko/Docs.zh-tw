---
title: "如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f266af44f954cb8416e1f7672f6642ab7c6995b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容
當資料繫結 Windows Form 控制項將不會排序。 若要顯示已排序的資料，請使用支援排序的資料來源，然後排序的資料來源。 支援排序的資料來源是資料的檢視、 資料檢視管理員和排序陣列。  
  
 如果控制項不是資料繫結，您就可以進行排序。  
  
### <a name="to-sort-the-list"></a>若要排序的清單  
  
1.  將 `Sorted` 屬性設定為 `true`。  
  
     這項設定會依排序順序，重新調整所有現有的清單項目。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [Windows Forms 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [何時使用 Windows Forms ComboBox 取代 ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [用來列出選項的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
