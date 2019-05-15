---
title: 作法：Windows Forms DataGridView 儲存格的主控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 20b9f33b31df9145205a13b8649153e51d840a6c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592435"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="00ef8-102">HOW TO：Windows Forms DataGridView 儲存格的主控制項</span><span class="sxs-lookup"><span data-stu-id="00ef8-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="00ef8-103"><xref:System.Windows.Forms.DataGridView> 控制項提供許多資料行類型，讓使用者以各種不同的方式輸入和編輯值。</span><span class="sxs-lookup"><span data-stu-id="00ef8-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="00ef8-104">如果這些資料行類型不符合您輸入資料的需求，則您仍可用裝載您所選擇的控制項之儲存格來建立自己的資料行類型。</span><span class="sxs-lookup"><span data-stu-id="00ef8-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="00ef8-105">若要這樣做，您必須定義衍生自 <xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.Windows.Forms.DataGridViewCell> 的類別。</span><span class="sxs-lookup"><span data-stu-id="00ef8-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="00ef8-106">您也必須定義衍生自 <xref:System.Windows.Forms.Control> 的類別，並實作 <xref:System.Windows.Forms.IDataGridViewEditingControl> 介面。</span><span class="sxs-lookup"><span data-stu-id="00ef8-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="00ef8-107">下列程式碼範例示範如何建立行事曆資料行。</span><span class="sxs-lookup"><span data-stu-id="00ef8-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="00ef8-108">這個資料行的儲存格會在一般文字方塊中的儲存格顯示日期，但是當使用者編輯儲存格時，<xref:System.Windows.Forms.DateTimePicker> 控制項就會出現。</span><span class="sxs-lookup"><span data-stu-id="00ef8-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="00ef8-109">若要避免再次實作文字方塊顯示功能，則 `CalendarCell` 類別要衍生自 <xref:System.Windows.Forms.DataGridViewTextBoxCell> 類別，而不是直接繼承 <xref:System.Windows.Forms.DataGridViewCell> 類別。</span><span class="sxs-lookup"><span data-stu-id="00ef8-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00ef8-110">當您自 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 中衍生時，以及在衍生類別中加入新的屬性時，請務必覆寫 `Clone` 方法，在複製作業期間複製新的屬性。</span><span class="sxs-lookup"><span data-stu-id="00ef8-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="00ef8-111">您也應該呼叫基底類別的 `Clone` 方法，以便將基底類別的屬性複製到新的儲存格或資料行。</span><span class="sxs-lookup"><span data-stu-id="00ef8-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00ef8-112">範例</span><span class="sxs-lookup"><span data-stu-id="00ef8-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00ef8-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="00ef8-113">Compiling the Code</span></span>  
 <span data-ttu-id="00ef8-114">下列範例需要：</span><span class="sxs-lookup"><span data-stu-id="00ef8-114">The following example requires:</span></span>  
  
- <span data-ttu-id="00ef8-115">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="00ef8-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ef8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00ef8-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="00ef8-117">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="00ef8-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="00ef8-118">DataGridView 控制項架構</span><span class="sxs-lookup"><span data-stu-id="00ef8-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="00ef8-119">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="00ef8-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
