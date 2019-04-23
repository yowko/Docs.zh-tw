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
ms.openlocfilehash: bd26d396c238bfc53858320b8f4487df84b3436a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312575"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="a6d0d-102">HOW TO：排序 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項內容</span><span class="sxs-lookup"><span data-stu-id="a6d0d-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="a6d0d-103">在資料繫結時，請不要排序 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="a6d0d-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="a6d0d-104">若要顯示已排序的資料，請使用支援排序的資料來源，則有 排序的資料來源。</span><span class="sxs-lookup"><span data-stu-id="a6d0d-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="a6d0d-105">支援排序的資料來源是資料的檢視，檢視管理員，與排序陣列的資料。</span><span class="sxs-lookup"><span data-stu-id="a6d0d-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="a6d0d-106">如果控制項不是資料繫結，您就可以進行排序。</span><span class="sxs-lookup"><span data-stu-id="a6d0d-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="a6d0d-107">若要排序的清單</span><span class="sxs-lookup"><span data-stu-id="a6d0d-107">To sort the list</span></span>  
  
1. <span data-ttu-id="a6d0d-108">將 `Sorted` 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a6d0d-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="a6d0d-109">此設定會依排序順序，重新調整所有現有的清單項目。</span><span class="sxs-lookup"><span data-stu-id="a6d0d-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6d0d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6d0d-110">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="a6d0d-111">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="a6d0d-111">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="a6d0d-112">如何：新增和移除項目從 Windows Form 的 ComboBox、 ListBox 或 CheckedListBox 控制項</span><span class="sxs-lookup"><span data-stu-id="a6d0d-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="a6d0d-113">何時使用 Windows Forms ComboBox 取代 ListBox</span><span class="sxs-lookup"><span data-stu-id="a6d0d-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="a6d0d-114">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="a6d0d-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
