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
# <a name="how-to-implement-binding-validation"></a>操作說明：實作繫結驗證

這個範例示範如何使用 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和樣式觸發程式來提供視覺效果意見反應，以根據自訂驗證規則輸入不正確值來通知使用者。

## <a name="example"></a>範例

下列範例中的文字內容系結 <xref:System.Windows.Controls.TextBox> 至 `Age` 名為之系結來源物件的屬性（類型為 int） `ods` 。 繫結是設為使用名為 `AgeRangeRule` 的驗證規則，因此如果使用者輸入非數值字元或小於 21 或大於 130 的值，文字方塊旁邊會出現紅色驚嘆號，並在使用者移動滑鼠到文字方塊上方時出現具有錯誤訊息的工具提示。

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

下列範例顯示的實作為 `AgeRangeRule` 繼承自的， <xref:System.Windows.Controls.ValidationRule> 並覆寫 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法。 `Int32.Parse`會在值上呼叫方法，以確保它不包含任何不正確字元。 方法會傳回 <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationResult> ，指出值是否有效，取決於剖析期間是否攔截到例外狀況，以及存留期值是否在下限和上限外。

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

下列範例顯示的自訂 <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` 會建立紅色驚嘆號，以通知使用者驗證錯誤。 控制項樣板是用於重新定義控制項的外觀。

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

如下列範例所示， <xref:System.Windows.Controls.ToolTip> 顯示錯誤訊息的會使用名為的樣式來建立 `textBoxInError` 。 如果的值 <xref:System.Windows.Controls.Validation.HasError%2A> 為 `true` ，則觸發程式會將目前的工具提示設定 <xref:System.Windows.Controls.TextBox> 為其第一個驗證錯誤。 <xref:System.Windows.Data.Binding.RelativeSource%2A>會設定為 <xref:System.Windows.Data.RelativeSourceMode.Self> ，並參考目前的元素。

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

如需完整範例，請參閱系結[驗證範例](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation)。
  
請注意，如果您未提供自訂 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ，則會顯示預設錯誤範本，以便在發生驗證錯誤時，提供視覺化的意見反應給使用者。 如需詳細資訊，請參閱[資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)中的＜資料驗證＞。 除此之外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的內建驗證規則，會攔截繫結來源屬性更新期間所擲回的例外狀況。 如需詳細資訊，請參閱 <xref:System.Windows.Controls.ExceptionValidationRule> 。

## <a name="see-also"></a>另請參閱

- [資料系結總覽](../../../desktop-wpf/data/data-binding-overview.md)
- [操作說明主題](data-binding-how-to-topics.md)
