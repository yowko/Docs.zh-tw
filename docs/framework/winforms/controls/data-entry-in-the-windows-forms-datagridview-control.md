---
title: DataGridView 控制項中的資料輸入
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
ms.openlocfilehash: e95095624f45cc1507735083a87293730e9133e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744003"
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="677d0-102">Windows Form DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="677d0-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="677d0-103">`DataGridView` 控制項提供數項功能，可讓您變更使用者在控制項中加入或修改資料的方式。</span><span class="sxs-lookup"><span data-stu-id="677d0-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="677d0-104">例如，您可以藉由提供新資料列的預設值，並在發生錯誤時警示使用者，讓資料項目更有效率。</span><span class="sxs-lookup"><span data-stu-id="677d0-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="677d0-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="677d0-105">In This Section</span></span>  
 [<span data-ttu-id="677d0-106">操作說明：指定 Windows Forms DataGridView 控制項的編輯模式</span><span class="sxs-lookup"><span data-stu-id="677d0-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="677d0-107">描述如何變更使用者開始編輯資料格的方式。</span><span class="sxs-lookup"><span data-stu-id="677d0-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="677d0-108">操作說明：指定 Windows Forms DataGridView 控制項新資料列的預設值</span><span class="sxs-lookup"><span data-stu-id="677d0-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="677d0-109">描述如何預先填入新記錄的資料列，以儲存資料輸入時間。</span><span class="sxs-lookup"><span data-stu-id="677d0-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="677d0-110">使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列</span><span class="sxs-lookup"><span data-stu-id="677d0-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="677d0-111">詳細描述新記錄的資料列，包括隱藏它的資訊、自訂其外觀，以及與 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合的關聯。</span><span class="sxs-lookup"><span data-stu-id="677d0-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="677d0-112">逐步解說：驗證 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="677d0-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="677d0-113">描述如何驗證使用者輸入，以防止資料輸入格式錯誤。</span><span class="sxs-lookup"><span data-stu-id="677d0-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="677d0-114">逐步解說：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="677d0-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="677d0-115">描述當使用者嘗試認可新的值時，如何處理來自資料來源的資料輸入錯誤。</span><span class="sxs-lookup"><span data-stu-id="677d0-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="677d0-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="677d0-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="677d0-117">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="677d0-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="677d0-118">提供 <xref:System.Windows.Forms.DataGridView.EditMode%2A> 屬性的參考檔。</span><span class="sxs-lookup"><span data-stu-id="677d0-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="677d0-119">提供 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> 事件的參考檔。</span><span class="sxs-lookup"><span data-stu-id="677d0-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="677d0-120">提供 <xref:System.Windows.Forms.DataGridView.DataError> 事件的參考檔。</span><span class="sxs-lookup"><span data-stu-id="677d0-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="677d0-121">提供 <xref:System.Windows.Forms.DataGridView.CellValidating> 事件的參考檔。</span><span class="sxs-lookup"><span data-stu-id="677d0-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="677d0-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="677d0-122">Related Sections</span></span>  
 [<span data-ttu-id="677d0-123">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="677d0-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="677d0-124">提供主題，說明如何以手動方式或從外部資料源，將資料填入控制項。</span><span class="sxs-lookup"><span data-stu-id="677d0-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677d0-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="677d0-125">See also</span></span>

- [<span data-ttu-id="677d0-126">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="677d0-126">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="677d0-127">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="677d0-127">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
