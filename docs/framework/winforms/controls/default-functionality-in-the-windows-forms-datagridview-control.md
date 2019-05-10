---
title: Windows Form DataGridView 控制項的預設功能
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b84d5a279bfe7cd99262ca904daeceabc9d0355d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648062"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fe4a8-102">Windows Form DataGridView 控制項的預設功能</span><span class="sxs-lookup"><span data-stu-id="fe4a8-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fe4a8-103">Windows Form<xref:System.Windows.Forms.DataGridView>控制項提供使用者一段很長的預設功能。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="fe4a8-104">預設功能</span><span class="sxs-lookup"><span data-stu-id="fe4a8-104">Default Functionality</span></span>  
 <span data-ttu-id="fe4a8-105">根據預設，<xref:System.Windows.Forms.DataGridView>控制項：</span><span class="sxs-lookup"><span data-stu-id="fe4a8-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <span data-ttu-id="fe4a8-106">會自動顯示資料行標頭和保持可見的因為資料表垂直捲動的資料列行首。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
- <span data-ttu-id="fe4a8-107">有資料列標頭，其中包含目前資料列選取範圍指標。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
- <span data-ttu-id="fe4a8-108">第一個資料格中有選取矩形。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-108">Has a selection rectangle in the first cell.</span></span>  
  
- <span data-ttu-id="fe4a8-109">有可以使用者按兩下資料行分隔線時，自動調整大小的資料行。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
- <span data-ttu-id="fe4a8-110">會自動在 Windows XP 和 Windows Server 2003 系列支援視覺化樣式時<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法從應用程式的呼叫`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="fe4a8-111">此外，內容<xref:System.Windows.Forms.DataGridView>控制項可以編輯預設值：</span><span class="sxs-lookup"><span data-stu-id="fe4a8-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
- <span data-ttu-id="fe4a8-112">如果使用者按兩下，或按下 f2 鍵在資料格中，控制項將會自動將儲存格進入編輯模式並更新資料格內容，當使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
- <span data-ttu-id="fe4a8-113">如果使用者捲動至方格的結尾時，使用者會看到加入新資料錄的資料列會出現。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="fe4a8-114">當使用者按一下此資料列時，要將新的資料列加入至<xref:System.Windows.Forms.DataGridView>控制，使用預設值。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="fe4a8-115">當使用者按下 esc 鍵時，這個新的資料列就會消失。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-115">When the user presses ESC, this new row disappears.</span></span>  
  
- <span data-ttu-id="fe4a8-116">如果使用者按一下資料列行首時，會選取整個資料列。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="fe4a8-117">當您繫結<xref:System.Windows.Forms.DataGridView>藉由設定資料來源的控制項及其<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性、 控制項：</span><span class="sxs-lookup"><span data-stu-id="fe4a8-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
- <span data-ttu-id="fe4a8-118">會自動為資料行標頭文字中使用資料來源的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
- <span data-ttu-id="fe4a8-119">填入資料來源的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="fe4a8-120"><xref:System.Windows.Forms.DataGridView> 每個資料行的資料來源中，會自動建立資料行。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
- <span data-ttu-id="fe4a8-121">建立資料表中的每個可見的資料列的資料列。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-121">Creates a row for each visible row in the table.</span></span>  
  
- <span data-ttu-id="fe4a8-122">自動排序依據的基礎資料，當使用者按一下資料行標頭的資料列。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4a8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe4a8-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="fe4a8-124">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="fe4a8-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
