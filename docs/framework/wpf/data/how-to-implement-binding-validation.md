---
title: HOW TO：實作繫結驗證
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: eefdb3b1205a64221e3e9352f70e3d06dc074eff
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368541"
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="de3aa-102">HOW TO：實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="de3aa-102">How to: Implement Binding Validation</span></span>
<span data-ttu-id="de3aa-103">此範例示範如何使用<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>和樣式觸發程序提供視覺化回應以通知使用者，當您輸入了無效的值，根據自訂驗證規則。</span><span class="sxs-lookup"><span data-stu-id="de3aa-103">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de3aa-104">範例</span><span class="sxs-lookup"><span data-stu-id="de3aa-104">Example</span></span>  
 <span data-ttu-id="de3aa-105">文字內容<xref:System.Windows.Controls.TextBox>在下列範例會繫結至`Age`名為繫結來源物件的屬性 （型別 int) `ods`。</span><span class="sxs-lookup"><span data-stu-id="de3aa-105">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="de3aa-106">繫結是設為使用名為 `AgeRangeRule` 的驗證規則，因此如果使用者輸入非數值字元或小於 21 或大於 130 的值，文字方塊旁邊會出現紅色驚嘆號，並在使用者移動滑鼠到文字方塊上方時出現具有錯誤訊息的工具提示。</span><span class="sxs-lookup"><span data-stu-id="de3aa-106">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>  
  
 [!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="de3aa-107">下列範例示範實作`AgeRangeRule`，該項則繼承自<xref:System.Windows.Controls.ValidationRule>，並覆寫<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="de3aa-107">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="de3aa-108">Int32.Parse() 方法會針對值呼叫，以確認當中沒有包含任何無效的字元。</span><span class="sxs-lookup"><span data-stu-id="de3aa-108">The Int32.Parse() method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="de3aa-109"><xref:System.Windows.Controls.ValidationRule.Validate%2A>方法會傳回<xref:System.Windows.Controls.ValidationResult>，指出值是否有效根據是否在剖析期間攔截到例外狀況以及年齡值是外部的下限和上限。</span><span class="sxs-lookup"><span data-stu-id="de3aa-109">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>  
  
 [!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 <span data-ttu-id="de3aa-110">下列範例顯示的自訂<xref:System.Windows.Controls.ControlTemplate> `validationTemplate` ，會建立紅色驚嘆號，通知使用者的驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="de3aa-110">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="de3aa-111">控制項樣板是用於重新定義控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="de3aa-111">Control templates are used to redefine the appearance of a control.</span></span>  
  
 [!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 <span data-ttu-id="de3aa-112">下列範例所示<xref:System.Windows.Controls.ToolTip>所顯示的錯誤訊息會建立名為樣式`textBoxInError`。</span><span class="sxs-lookup"><span data-stu-id="de3aa-112">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="de3aa-113">如果值<xref:System.Windows.Controls.Validation.HasError%2A>已`true`，觸發程序的工具提示設定目前的<xref:System.Windows.Controls.TextBox>到其第一個驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="de3aa-113">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="de3aa-114"><xref:System.Windows.Data.Binding.RelativeSource%2A>設為<xref:System.Windows.Data.RelativeSourceMode.Self>，參照目前的項目。</span><span class="sxs-lookup"><span data-stu-id="de3aa-114">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>  
  
 [!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 <span data-ttu-id="de3aa-115">如需完整範例，請參閱[繫結驗證範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159972)。</span><span class="sxs-lookup"><span data-stu-id="de3aa-115">For the complete example, see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
 <span data-ttu-id="de3aa-116">請注意，如果您未提供自訂<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>預設錯誤範本會出現驗證錯誤時，提供視覺化回饋給使用者。</span><span class="sxs-lookup"><span data-stu-id="de3aa-116">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="de3aa-117">如需詳細資訊，請參閱[資料繫結概觀](data-binding-overview.md)中的＜資料驗證＞。</span><span class="sxs-lookup"><span data-stu-id="de3aa-117">See "Data Validation" in [Data Binding Overview](data-binding-overview.md) for more information.</span></span> <span data-ttu-id="de3aa-118">除此之外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的內建驗證規則，會攔截繫結來源屬性更新期間所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="de3aa-118">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="de3aa-119">如需詳細資訊，請參閱<xref:System.Windows.Controls.ExceptionValidationRule>。</span><span class="sxs-lookup"><span data-stu-id="de3aa-119">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3aa-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de3aa-120">See also</span></span>
- [<span data-ttu-id="de3aa-121">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="de3aa-121">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="de3aa-122">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="de3aa-122">How-to Topics</span></span>](data-binding-how-to-topics.md)
