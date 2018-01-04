---
title: "Windows Form DataGridView 控制項中的資料格式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6ff3452a60d9cb80a71dacd5841b120b5efbf82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4eff6-102">Windows Form DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="4eff6-102">Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4eff6-103"><xref:System.Windows.Forms.DataGridView>控制項提供自動資料格的值與父資料行顯示的資料類型之間轉換。</span><span class="sxs-lookup"><span data-stu-id="4eff6-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic conversion between cell values and the data types that the parent columns display.</span></span> <span data-ttu-id="4eff6-104">文字方塊資料行，例如顯示的日期、 時間、 數字和列舉值的字串表示法，並將使用者輸入的字串值轉換為資料存放區所需的類型。</span><span class="sxs-lookup"><span data-stu-id="4eff6-104">Text box columns, for example, display string representations of date, time, number, and enumeration values, and convert user-entered string values to the types required by the data store.</span></span>  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a><span data-ttu-id="4eff6-105">格式化與 DataGridViewCellStyle 類別</span><span class="sxs-lookup"><span data-stu-id="4eff6-105">Formatting with the DataGridViewCellStyle class</span></span>  
 <span data-ttu-id="4eff6-106"><xref:System.Windows.Forms.DataGridView>控制項提供基本的資料格式的資料格值透過<xref:System.Windows.Forms.DataGridViewCellStyle>類別。</span><span class="sxs-lookup"><span data-stu-id="4eff6-106">The <xref:System.Windows.Forms.DataGridView> control provides basic data formatting of cell values through the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span> <span data-ttu-id="4eff6-107">您可以使用<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>屬性來格式化日期、 時間、 數字和列舉值目前使用中所述的格式規範的預設文化特性[格式化型別](../../../../docs/standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4eff6-107">You can use the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property to format date, time, number, and enumeration values for the current default culture using the format specifiers described in [Formatting Types](../../../../docs/standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="4eff6-108">您也可以格式化特定文化特性使用的這些值<xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4eff6-108">You can also format these values for specific cultures using the <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> property.</span></span> <span data-ttu-id="4eff6-109">指定的格式用來顯示資料，並剖析使用者輸入中指定的格式的資料。</span><span class="sxs-lookup"><span data-stu-id="4eff6-109">The specified format is used both to display data and to parse data that the user enters in the specified format.</span></span>  
  
 <span data-ttu-id="4eff6-110"><xref:System.Windows.Forms.DataGridViewCellStyle>類別自動換行、 文字對齊方式，以及資料庫 null 值的自訂顯示提供額外的格式化屬性。</span><span class="sxs-lookup"><span data-stu-id="4eff6-110">The <xref:System.Windows.Forms.DataGridViewCellStyle> class provides additional formatting properties for wordwrap, text alignment, and the custom display of null database values.</span></span> <span data-ttu-id="4eff6-111">如需詳細資訊，請參閱[如何：格式化 Windows Forms DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="4eff6-111">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="formatting-with-the-cellformatting-event"></a><span data-ttu-id="4eff6-112">格式化與 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="4eff6-112">Formatting with the CellFormatting Event</span></span>  
 <span data-ttu-id="4eff6-113">如果基本的格式不符合您的需求，您可以提供自訂中的資料格式的處理常式<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="4eff6-113">If the basic formatting does not meet your needs, you can provide custom data formatting in a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="4eff6-114"><xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>傳遞至處理常式具有<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>屬性一開始不包含儲存格的值。</span><span class="sxs-lookup"><span data-stu-id="4eff6-114">The <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passed to the handler has a <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property that initially contains the cell value.</span></span> <span data-ttu-id="4eff6-115">一般來說，這個值會自動轉換為顯示類型。</span><span class="sxs-lookup"><span data-stu-id="4eff6-115">Normally, this value is automatically converted to the display type.</span></span> <span data-ttu-id="4eff6-116">若要自行轉換值，設定<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>屬性設為顯示類型的值。</span><span class="sxs-lookup"><span data-stu-id="4eff6-116">To convert the value yourself, set the <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property to a value of the display type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4eff6-117">如果格式字串是作用中的儲存格，它會覆寫您的變更<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>屬性值，除非您將設定<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="4eff6-117">If a format string is in effect for the cell, it overrides your change of the <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property value unless you set the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="4eff6-118"><xref:System.Windows.Forms.DataGridView.CellFormatting>事件時也很有用您想要設定<xref:System.Windows.Forms.DataGridViewCellStyle>個別資料格的內容會根據它們的值。</span><span class="sxs-lookup"><span data-stu-id="4eff6-118">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event is also useful when you want to set <xref:System.Windows.Forms.DataGridViewCellStyle> properties for individual cells based on their values.</span></span> <span data-ttu-id="4eff6-119">如需詳細資訊，請參閱[How to： 在 Windows Form DataGridView 控制項中自訂格式化資料](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="4eff6-119">For more information, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="4eff6-120">如果使用者指定值的預設值剖析不符合您的需求，您可以處理<xref:System.Windows.Forms.DataGridView.CellParsing>事件<xref:System.Windows.Forms.DataGridView>控制項來提供自訂剖析。</span><span class="sxs-lookup"><span data-stu-id="4eff6-120">If the default parsing of user-specified values does not meet your needs, you can handle the <xref:System.Windows.Forms.DataGridView.CellParsing> event of the <xref:System.Windows.Forms.DataGridView> control to provide custom parsing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eff6-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="4eff6-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="4eff6-122">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="4eff6-122">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="4eff6-123">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="4eff6-123">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="4eff6-124">操作說明：格式化 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="4eff6-124">How to: Format Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="4eff6-125">操作說明：自訂 Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="4eff6-125">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
