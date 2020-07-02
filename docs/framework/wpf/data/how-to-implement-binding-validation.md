---
title: 操作說明：實作繫結驗證
description: 瞭解如何使用系結驗證，在 Windows Presentation Foundation （WPF）中輸入不正確值時，為使用者提供視覺化回饋。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 0813be9f79a83a9dae26db1dadb58b5e973339fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617878"
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="0b761-103">操作說明：實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="0b761-103">How to: Implement Binding Validation</span></span>

<span data-ttu-id="0b761-104">這個範例示範如何使用 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和樣式觸發程式來提供視覺效果意見反應，以根據自訂驗證規則輸入不正確值來通知使用者。</span><span class="sxs-lookup"><span data-stu-id="0b761-104">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>

## <a name="example"></a><span data-ttu-id="0b761-105">範例</span><span class="sxs-lookup"><span data-stu-id="0b761-105">Example</span></span>

<span data-ttu-id="0b761-106">下列範例中的文字內容系結 <xref:System.Windows.Controls.TextBox> 至 `Age` 名為之系結來源物件的屬性（類型為 int） `ods` 。</span><span class="sxs-lookup"><span data-stu-id="0b761-106">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="0b761-107">繫結是設為使用名為 `AgeRangeRule` 的驗證規則，因此如果使用者輸入非數值字元或小於 21 或大於 130 的值，文字方塊旁邊會出現紅色驚嘆號，並在使用者移動滑鼠到文字方塊上方時出現具有錯誤訊息的工具提示。</span><span class="sxs-lookup"><span data-stu-id="0b761-107">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

<span data-ttu-id="0b761-108">下列範例顯示的實作為 `AgeRangeRule` 繼承自的， <xref:System.Windows.Controls.ValidationRule> 並覆寫 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0b761-108">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="0b761-109">`Int32.Parse`會在值上呼叫方法，以確保它不包含任何不正確字元。</span><span class="sxs-lookup"><span data-stu-id="0b761-109">The `Int32.Parse` method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="0b761-110">方法會傳回 <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationResult> ，指出值是否有效，取決於剖析期間是否攔截到例外狀況，以及存留期值是否在下限和上限外。</span><span class="sxs-lookup"><span data-stu-id="0b761-110">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

<span data-ttu-id="0b761-111">下列範例顯示的自訂 <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` 會建立紅色驚嘆號，以通知使用者驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="0b761-111">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="0b761-112">控制項樣板是用於重新定義控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="0b761-112">Control templates are used to redefine the appearance of a control.</span></span>

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

<span data-ttu-id="0b761-113">如下列範例所示， <xref:System.Windows.Controls.ToolTip> 顯示錯誤訊息的會使用名為的樣式來建立 `textBoxInError` 。</span><span class="sxs-lookup"><span data-stu-id="0b761-113">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="0b761-114">如果的值 <xref:System.Windows.Controls.Validation.HasError%2A> 為 `true` ，則觸發程式會將目前的工具提示設定 <xref:System.Windows.Controls.TextBox> 為其第一個驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="0b761-114">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="0b761-115"><xref:System.Windows.Data.Binding.RelativeSource%2A>會設定為 <xref:System.Windows.Data.RelativeSourceMode.Self> ，並參考目前的元素。</span><span class="sxs-lookup"><span data-stu-id="0b761-115">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

<span data-ttu-id="0b761-116">如需完整範例，請參閱系結[驗證範例](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation)。</span><span class="sxs-lookup"><span data-stu-id="0b761-116">For the complete example, see [Bind Validation sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>
  
<span data-ttu-id="0b761-117">請注意，如果您未提供自訂 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ，則會顯示預設錯誤範本，以便在發生驗證錯誤時，提供視覺化的意見反應給使用者。</span><span class="sxs-lookup"><span data-stu-id="0b761-117">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="0b761-118">如需詳細資訊，請參閱[資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)中的＜資料驗證＞。</span><span class="sxs-lookup"><span data-stu-id="0b761-118">See "Data Validation" in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="0b761-119">除此之外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的內建驗證規則，會攔截繫結來源屬性更新期間所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0b761-119">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="0b761-120">如需詳細資訊，請參閱 <xref:System.Windows.Controls.ExceptionValidationRule> 。</span><span class="sxs-lookup"><span data-stu-id="0b761-120">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b761-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b761-121">See also</span></span>

- [<span data-ttu-id="0b761-122">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="0b761-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="0b761-123">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="0b761-123">How-to Topics</span></span>](data-binding-how-to-topics.md)
