---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 910ce09bfad6a46e3d96784b980ee4175c3d26a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550058"
---
# <a name="datepicker"></a><span data-ttu-id="49210-102">DatePicker</span><span class="sxs-lookup"><span data-stu-id="49210-102">DatePicker</span></span>
<span data-ttu-id="49210-103"><xref:System.Windows.Controls.DatePicker>控制項可讓使用者選取日期，可能輸入到文字欄位，或使用下拉式清單<xref:System.Windows.Controls.Calendar>控制項。</span><span class="sxs-lookup"><span data-stu-id="49210-103">The <xref:System.Windows.Controls.DatePicker> control allows the user to select a date by either typing it into a text field or by using a drop-down <xref:System.Windows.Controls.Calendar> control.</span></span>  
  
 <span data-ttu-id="49210-104">下圖顯示<xref:System.Windows.Controls.DatePicker>。</span><span class="sxs-lookup"><span data-stu-id="49210-104">The following illustration shows a <xref:System.Windows.Controls.DatePicker>.</span></span>  
  
 <span data-ttu-id="49210-105">![DatePicker 控制項](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span><span class="sxs-lookup"><span data-stu-id="49210-105">![DatePicker control](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span></span>  
<span data-ttu-id="49210-106">日期選擇器控制項</span><span class="sxs-lookup"><span data-stu-id="49210-106">DatePicker Control</span></span>  
  
 <span data-ttu-id="49210-107">許多<xref:System.Windows.Controls.DatePicker>控制項的屬性是用於管理內建的<xref:System.Windows.Controls.Calendar>，以及相同 function 中的相等屬性<xref:System.Windows.Controls.Calendar>。</span><span class="sxs-lookup"><span data-stu-id="49210-107">Many of a <xref:System.Windows.Controls.DatePicker> control's properties are for managing its built-in <xref:System.Windows.Controls.Calendar>, and function identically to the equivalent property in <xref:System.Windows.Controls.Calendar>.</span></span> <span data-ttu-id="49210-108">特別是， <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>，和<xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType>屬性函式和其<xref:System.Windows.Controls.Calendar>對應項目。</span><span class="sxs-lookup"><span data-stu-id="49210-108">In particular, the <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, and <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> properties function identically to their <xref:System.Windows.Controls.Calendar> counterparts.</span></span> <span data-ttu-id="49210-109">如需詳細資訊，請參閱<xref:System.Windows.Controls.Calendar>。</span><span class="sxs-lookup"><span data-stu-id="49210-109">For more information, see <xref:System.Windows.Controls.Calendar>.</span></span>  
  
 <span data-ttu-id="49210-110">使用者可以直接在文字欄位中，設定輸入日期<xref:System.Windows.Controls.DatePicker.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="49210-110">Users can type a date directly into a text field, which sets the <xref:System.Windows.Controls.DatePicker.Text%2A> property.</span></span> <span data-ttu-id="49210-111">如果<xref:System.Windows.Controls.DatePicker>無法將輸入的字串轉換成有效的日期，<xref:System.Windows.Controls.DatePicker.DateValidationError>會引發事件。</span><span class="sxs-lookup"><span data-stu-id="49210-111">If the <xref:System.Windows.Controls.DatePicker> cannot convert the entered string to a valid date, the <xref:System.Windows.Controls.DatePicker.DateValidationError> event will be raised.</span></span> <span data-ttu-id="49210-112">根據預設，這會導致例外狀況，但事件處理常式<xref:System.Windows.Controls.DatePicker.DateValidationError>可以設定<xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A>屬性`false`並防止所引發的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="49210-112">By default, this causes an exception, but an event handler for <xref:System.Windows.Controls.DatePicker.DateValidationError> can set the <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> property to `false` and prevent an exception from being raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49210-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49210-113">See Also</span></span>  
 [<span data-ttu-id="49210-114">控制項</span><span class="sxs-lookup"><span data-stu-id="49210-114">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="49210-115">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="49210-115">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
