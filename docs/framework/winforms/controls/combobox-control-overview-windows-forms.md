---
title: "ComboBox 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 801ebb97c6ee52ce52bbb8f96a07d55e68ca6f1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="combobox-control-overview-windows-forms"></a><span data-ttu-id="d3c6b-102">ComboBox 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="d3c6b-102">ComboBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="d3c6b-103">Windows Form<xref:System.Windows.Forms.ComboBox>控制項用來在下拉式清單方塊中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-103">The Windows Forms <xref:System.Windows.Forms.ComboBox> control is used to display data in a drop-down combo box.</span></span> <span data-ttu-id="d3c6b-104">根據預設，<xref:System.Windows.Forms.ComboBox>控制項出現在兩個部分： 上半部是文字方塊，可讓使用者輸入的清單項目。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-104">By default, the <xref:System.Windows.Forms.ComboBox> control appears in two parts: the top part is a text box that allows the user to type a list item.</span></span> <span data-ttu-id="d3c6b-105">第二個部分是清單方塊會顯示，使用者可以從中選取一個項目清單。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-105">The second part is a list box that displays a list of items from which the user can select one.</span></span> <span data-ttu-id="d3c6b-106">如需其他樣式組合方塊的詳細資訊，請參閱[何時使用 Windows Form ComboBox Instead of ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-106">For more information on other styles of combo box, see [When to Use a Windows Forms ComboBox Instead of a ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).</span></span>  
  
 <span data-ttu-id="d3c6b-107"><xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>屬性會傳回整數值，對應至選取的清單項目。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-107">The <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> property returns an integer value that corresponds to the selected list item.</span></span> <span data-ttu-id="d3c6b-108">您可以變更，以程式設計的方式變更選取的項目<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>程式碼中的值，則為對應的項目在清單中會出現在下拉式方塊的文字方塊部分。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-108">You can programmatically change the selected item by changing the <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> value in code; the corresponding item in the list will appear in the text box portion of the combo box.</span></span> <span data-ttu-id="d3c6b-109">如果未不選取任何項目，則<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>值為-1。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-109">If no item is selected, the <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> value is -1.</span></span> <span data-ttu-id="d3c6b-110">如果選取清單中的第一個項目，然後在<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>值為 0。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-110">If the first item in the list is selected, then the <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> value is 0.</span></span> <span data-ttu-id="d3c6b-111"><xref:System.Windows.Forms.ComboBox.SelectedItem%2A>屬性是類似於<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>，但傳回的項目本身，通常是字串值。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-111">The <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property is similar to <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , but returns the item itself, usually a string value.</span></span> <span data-ttu-id="d3c6b-112"><xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A>屬性會反映在清單中的項目數，而<xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A>屬性一律會是一個以上的最大可能<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>值，因為<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>以零為起始。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-112">The <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> property reflects the number of items in the list, and the value of the <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> property is always one more than the largest possible <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> value because <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> is zero-based.</span></span>  
  
 <span data-ttu-id="d3c6b-113">若要加入或刪除的項目<xref:System.Windows.Forms.ComboBox>控制，請使用<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>， <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>，<xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A>或<xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-113">To add or delete items in a <xref:System.Windows.Forms.ComboBox> control, use the <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> or <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> method.</span></span> <span data-ttu-id="d3c6b-114">或者，您可以加入項目清單使用<xref:System.Windows.Forms.ComboBox.Items%2A>設計工具中的屬性。</span><span class="sxs-lookup"><span data-stu-id="d3c6b-114">Alternatively, you can add items to the list by using the <xref:System.Windows.Forms.ComboBox.Items%2A> property in the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c6b-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d3c6b-115">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 [<span data-ttu-id="d3c6b-116">ListBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="d3c6b-116">ListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="d3c6b-117">何時使用 Windows Forms ComboBox 取代 ListBox</span><span class="sxs-lookup"><span data-stu-id="d3c6b-117">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="d3c6b-118">操作說明：從 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目</span><span class="sxs-lookup"><span data-stu-id="d3c6b-118">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="d3c6b-119">操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容</span><span class="sxs-lookup"><span data-stu-id="d3c6b-119">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="d3c6b-120">操作說明：在 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定的項目</span><span class="sxs-lookup"><span data-stu-id="d3c6b-120">How to: Access Specific Items in a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)  
 [<span data-ttu-id="d3c6b-121">操作說明：將 Windows Forms ComboBox 或 ListBox 控制項繫結至資料</span><span class="sxs-lookup"><span data-stu-id="d3c6b-121">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [<span data-ttu-id="d3c6b-122">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="d3c6b-122">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [<span data-ttu-id="d3c6b-123">操作說明：為 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表</span><span class="sxs-lookup"><span data-stu-id="d3c6b-123">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
