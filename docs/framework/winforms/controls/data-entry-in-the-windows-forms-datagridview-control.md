---
title: Windows Form DataGridView 控制項中的資料輸入
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
ms.openlocfilehash: 4f0dbb99b1005cfea165439f4c08db64ecb18fed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550340"
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ca432-102">Windows Form DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="ca432-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ca432-103">`DataGridView`控制項提供數個功能，可讓您變更使用者如何新增或修改控制項中的資料。</span><span class="sxs-lookup"><span data-stu-id="ca432-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="ca432-104">比方說，您可以使資料輸入更有效率地藉由提供預設值的新資料列和發生錯誤時警示使用者。</span><span class="sxs-lookup"><span data-stu-id="ca432-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca432-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="ca432-105">In This Section</span></span>  
 [<span data-ttu-id="ca432-106">如何：Windows Form DataGridView 控制項中指定的編輯模式</span><span class="sxs-lookup"><span data-stu-id="ca432-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ca432-107">描述如何變更使用者開始編輯儲存格的方式。</span><span class="sxs-lookup"><span data-stu-id="ca432-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="ca432-108">如何：指定 Windows Form DataGridView 控制項中的新資料列的預設值</span><span class="sxs-lookup"><span data-stu-id="ca432-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="ca432-109">描述如何儲存輸入資料的時間的新記錄的資料列，預先填入。</span><span class="sxs-lookup"><span data-stu-id="ca432-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="ca432-110">使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列</span><span class="sxs-lookup"><span data-stu-id="ca432-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ca432-111">描述在 詳細資料，包括資訊上隱藏它、 自訂其外觀，以及它與新記錄的資料列<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="ca432-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="ca432-112">逐步解說：驗證 Windows Form DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="ca432-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ca432-113">描述如何驗證使用者輸入，以避免資料輸入格式錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca432-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="ca432-114">逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="ca432-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="ca432-115">描述如何處理來自資料來源，當使用者嘗試認可新值的資料輸入錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca432-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ca432-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="ca432-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="ca432-117">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="ca432-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="ca432-118">提供參考文件<xref:System.Windows.Forms.DataGridView.EditMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ca432-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="ca432-119">提供參考文件<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。</span><span class="sxs-lookup"><span data-stu-id="ca432-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="ca432-120">提供參考文件<xref:System.Windows.Forms.DataGridView.DataError>事件。</span><span class="sxs-lookup"><span data-stu-id="ca432-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="ca432-121">提供參考文件<xref:System.Windows.Forms.DataGridView.CellValidating>事件。</span><span class="sxs-lookup"><span data-stu-id="ca432-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ca432-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="ca432-122">Related Sections</span></span>  
 [<span data-ttu-id="ca432-123">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="ca432-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ca432-124">提供主題描述如何以手動方式或從外部資料來源填入資料控制項。</span><span class="sxs-lookup"><span data-stu-id="ca432-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca432-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca432-125">See also</span></span>
- [<span data-ttu-id="ca432-126">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="ca432-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [<span data-ttu-id="ca432-127">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="ca432-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
