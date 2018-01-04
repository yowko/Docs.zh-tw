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
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="9c404-102">如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容</span><span class="sxs-lookup"><span data-stu-id="9c404-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="9c404-103">當資料繫結 Windows Form 控制項將不會排序。</span><span class="sxs-lookup"><span data-stu-id="9c404-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="9c404-104">若要顯示已排序的資料，請使用支援排序的資料來源，然後排序的資料來源。</span><span class="sxs-lookup"><span data-stu-id="9c404-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="9c404-105">支援排序的資料來源是資料的檢視、 資料檢視管理員和排序陣列。</span><span class="sxs-lookup"><span data-stu-id="9c404-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="9c404-106">如果控制項不是資料繫結，您就可以進行排序。</span><span class="sxs-lookup"><span data-stu-id="9c404-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="9c404-107">若要排序的清單</span><span class="sxs-lookup"><span data-stu-id="9c404-107">To sort the list</span></span>  
  
1.  <span data-ttu-id="9c404-108">將 `Sorted` 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9c404-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="9c404-109">這項設定會依排序順序，重新調整所有現有的清單項目。</span><span class="sxs-lookup"><span data-stu-id="9c404-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c404-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="9c404-110">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="9c404-111">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="9c404-111">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="9c404-112">操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目</span><span class="sxs-lookup"><span data-stu-id="9c404-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="9c404-113">何時使用 Windows Forms ComboBox 取代 ListBox</span><span class="sxs-lookup"><span data-stu-id="9c404-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="9c404-114">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="9c404-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
