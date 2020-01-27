---
title: DataGridView 控制項中的預設功能
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746128"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="dcabd-102">Windows Form DataGridView 控制項的預設功能</span><span class="sxs-lookup"><span data-stu-id="dcabd-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="dcabd-103">Windows Forms <xref:System.Windows.Forms.DataGridView> 控制項提供大量的預設功能給使用者。</span><span class="sxs-lookup"><span data-stu-id="dcabd-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="dcabd-104">預設功能</span><span class="sxs-lookup"><span data-stu-id="dcabd-104">Default Functionality</span></span>  
 <span data-ttu-id="dcabd-105">根據預設，<xref:System.Windows.Forms.DataGridView> 控制項：</span><span class="sxs-lookup"><span data-stu-id="dcabd-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <span data-ttu-id="dcabd-106">當資料表垂直捲動時，自動顯示資料行標頭和資料列標頭保持可見。</span><span class="sxs-lookup"><span data-stu-id="dcabd-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
- <span data-ttu-id="dcabd-107">具有資料列標頭，其中包含目前資料列的選取範圍指示器。</span><span class="sxs-lookup"><span data-stu-id="dcabd-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
- <span data-ttu-id="dcabd-108">在第一個資料格中有一個選取矩形。</span><span class="sxs-lookup"><span data-stu-id="dcabd-108">Has a selection rectangle in the first cell.</span></span>  
  
- <span data-ttu-id="dcabd-109">具有可在使用者按兩下資料行分隔線時自動調整大小的資料行。</span><span class="sxs-lookup"><span data-stu-id="dcabd-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
- <span data-ttu-id="dcabd-110">從應用程式的 `Main` 方法呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法時，會自動支援 Windows XP 和 Windows Server 2003 系列的視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="dcabd-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="dcabd-111">此外，預設可以編輯 <xref:System.Windows.Forms.DataGridView> 控制項的內容：</span><span class="sxs-lookup"><span data-stu-id="dcabd-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
- <span data-ttu-id="dcabd-112">如果使用者按兩下或按下儲存格的 F2，控制項會自動將儲存格置於編輯模式，並將資料格的內容更新為使用者類型。</span><span class="sxs-lookup"><span data-stu-id="dcabd-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
- <span data-ttu-id="dcabd-113">如果使用者滾動到方格的結尾，則使用者會看到加入新記錄的資料列存在。</span><span class="sxs-lookup"><span data-stu-id="dcabd-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="dcabd-114">當使用者按一下此資料列時，新的資料列就會加入至 <xref:System.Windows.Forms.DataGridView> 控制項，其中包含預設值。</span><span class="sxs-lookup"><span data-stu-id="dcabd-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="dcabd-115">當使用者按下 ESC 鍵時，這個新的資料列就會消失。</span><span class="sxs-lookup"><span data-stu-id="dcabd-115">When the user presses ESC, this new row disappears.</span></span>  
  
- <span data-ttu-id="dcabd-116">如果使用者按一下資料列標頭，則會選取整個資料列。</span><span class="sxs-lookup"><span data-stu-id="dcabd-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="dcabd-117">當您藉由設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性，將 <xref:System.Windows.Forms.DataGridView> 控制項系結至資料來源時，控制項會：</span><span class="sxs-lookup"><span data-stu-id="dcabd-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
- <span data-ttu-id="dcabd-118">會自動使用資料來源的資料行名稱做為欄標題文字。</span><span class="sxs-lookup"><span data-stu-id="dcabd-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
- <span data-ttu-id="dcabd-119">會填入資料來源的內容。</span><span class="sxs-lookup"><span data-stu-id="dcabd-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="dcabd-120">系統會針對資料來源中的每個資料行自動建立 <xref:System.Windows.Forms.DataGridView> 資料行。</span><span class="sxs-lookup"><span data-stu-id="dcabd-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
- <span data-ttu-id="dcabd-121">針對資料表中的每個可見資料列建立一個資料列。</span><span class="sxs-lookup"><span data-stu-id="dcabd-121">Creates a row for each visible row in the table.</span></span>  
  
- <span data-ttu-id="dcabd-122">當使用者按一下資料行標頭時，會自動根據基礎資料排序資料列。</span><span class="sxs-lookup"><span data-stu-id="dcabd-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcabd-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="dcabd-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="dcabd-124">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="dcabd-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
