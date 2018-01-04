---
title: "Windows Form DataGridView 控制項中的資料輸入"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399520738c53e149e7a5539a62a5d4599e26a8da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b9b95-102">Windows Form DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="b9b95-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b9b95-103">`DataGridView`控制項提供數種功能，可讓您變更使用者加入或修改控制項中的資料的方式。</span><span class="sxs-lookup"><span data-stu-id="b9b95-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="b9b95-104">比方說，您可以讓資料輸入更有效率的新資料列中提供預設值和錯誤發生時警示使用者。</span><span class="sxs-lookup"><span data-stu-id="b9b95-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9b95-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="b9b95-105">In This Section</span></span>  
 [<span data-ttu-id="b9b95-106">操作說明：指定 Windows Forms DataGridView 控制項的編輯模式</span><span class="sxs-lookup"><span data-stu-id="b9b95-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b9b95-107">描述如何變更使用者開始編輯儲存格的方式。</span><span class="sxs-lookup"><span data-stu-id="b9b95-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="b9b95-108">操作說明：指定 Windows Forms DataGridView 控制項新資料列的預設值</span><span class="sxs-lookup"><span data-stu-id="b9b95-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="b9b95-109">描述如何預先填入新的記錄，以節省資料輸入時間的資料列。</span><span class="sxs-lookup"><span data-stu-id="b9b95-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="b9b95-110">使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列</span><span class="sxs-lookup"><span data-stu-id="b9b95-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b9b95-111">描述新的記錄詳細資料，包括隱藏它、 自訂其外觀，以及它如何與資訊中的資料列<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="b9b95-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="b9b95-112">逐步解說：驗證 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="b9b95-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b9b95-113">描述如何驗證使用者輸入，以避免資料輸入格式錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9b95-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="b9b95-114">逐步解說：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="b9b95-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="b9b95-115">描述如何處理來自資料來源，當使用者嘗試認可新值的資料輸入錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9b95-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b9b95-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="b9b95-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b9b95-117">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="b9b95-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="b9b95-118">提供參考文件<xref:System.Windows.Forms.DataGridView.EditMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b9b95-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="b9b95-119">提供參考文件<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。</span><span class="sxs-lookup"><span data-stu-id="b9b95-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="b9b95-120">提供參考文件<xref:System.Windows.Forms.DataGridView.DataError>事件。</span><span class="sxs-lookup"><span data-stu-id="b9b95-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="b9b95-121">提供參考文件<xref:System.Windows.Forms.DataGridView.CellValidating>事件。</span><span class="sxs-lookup"><span data-stu-id="b9b95-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9b95-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="b9b95-122">Related Sections</span></span>  
 [<span data-ttu-id="b9b95-123">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="b9b95-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b9b95-124">提供主題描述如何以手動方式或從外部資料來源填入資料控制項。</span><span class="sxs-lookup"><span data-stu-id="b9b95-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b95-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9b95-125">See Also</span></span>  
 [<span data-ttu-id="b9b95-126">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="b9b95-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="b9b95-127">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="b9b95-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
