---
title: "Windows Form DataGridView 控制項的預設功能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d6b15085c301f074ef6fcf9e60a75299c4b245b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ec858-102">Windows Form DataGridView 控制項的預設功能</span><span class="sxs-lookup"><span data-stu-id="ec858-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ec858-103">Windows Form<xref:System.Windows.Forms.DataGridView>控制為使用者提供相當大的預設功能。</span><span class="sxs-lookup"><span data-stu-id="ec858-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="ec858-104">預設功能</span><span class="sxs-lookup"><span data-stu-id="ec858-104">Default Functionality</span></span>  
 <span data-ttu-id="ec858-105">根據預設，<xref:System.Windows.Forms.DataGridView>控制項：</span><span class="sxs-lookup"><span data-stu-id="ec858-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="ec858-106">會自動顯示資料行標頭和表格垂直捲動時保持可見的資料列標頭。</span><span class="sxs-lookup"><span data-stu-id="ec858-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="ec858-107">有資料列標題，其中包含目前資料列之選取項目指標。</span><span class="sxs-lookup"><span data-stu-id="ec858-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="ec858-108">已選取矩形中第一個資料格。</span><span class="sxs-lookup"><span data-stu-id="ec858-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="ec858-109">有使用者按兩下資料行分隔線時要自動調整的資料行。</span><span class="sxs-lookup"><span data-stu-id="ec858-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="ec858-110">會自動在 Windows XP 和 Windows Server 2003 系列上支援視覺化樣式時<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法從應用程式的呼叫`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="ec858-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="ec858-111">此外，內容<xref:System.Windows.Forms.DataGridView>控制項可以編輯預設值：</span><span class="sxs-lookup"><span data-stu-id="ec858-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="ec858-112">如果使用者按兩下，或按 F2，在資料格中，控制項自動儲存格置於編輯模式，並更新資料格內容，做為使用者型別。</span><span class="sxs-lookup"><span data-stu-id="ec858-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="ec858-113">如果使用者捲動至方格的結尾，使用者會看到加入新資料錄的資料列，會顯示。</span><span class="sxs-lookup"><span data-stu-id="ec858-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="ec858-114">當使用者按一下此資料列時，加入新的資料列<xref:System.Windows.Forms.DataGridView>控制項，使用預設值。</span><span class="sxs-lookup"><span data-stu-id="ec858-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="ec858-115">當使用者按下 esc 鍵時，這個新的資料列就會消失。</span><span class="sxs-lookup"><span data-stu-id="ec858-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="ec858-116">如果使用者按一下資料列標頭時，會選取整個資料列。</span><span class="sxs-lookup"><span data-stu-id="ec858-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="ec858-117">當您繫結<xref:System.Windows.Forms.DataGridView>控制項至資料來源，藉由設定其<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性、 控制項：</span><span class="sxs-lookup"><span data-stu-id="ec858-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="ec858-118">會自動使用資料來源的資料行名稱做為資料行標頭文字。</span><span class="sxs-lookup"><span data-stu-id="ec858-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="ec858-119">填入資料來源的內容。</span><span class="sxs-lookup"><span data-stu-id="ec858-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="ec858-120"><xref:System.Windows.Forms.DataGridView>每個資料行的資料來源中，會自動建立資料行。</span><span class="sxs-lookup"><span data-stu-id="ec858-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="ec858-121">在資料表中建立每個可見資料列的資料列。</span><span class="sxs-lookup"><span data-stu-id="ec858-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="ec858-122">自動排序依據基礎資料，當使用者按一下資料行標頭的資料列。</span><span class="sxs-lookup"><span data-stu-id="ec858-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec858-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec858-123">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="ec858-124">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="ec858-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
