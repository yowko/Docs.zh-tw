---
title: 操作說明：實作繫結驗證
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 5e91ab9fbd2fdeb0aa5d836a1eedfb5e0b45ecba
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425793"
---
# <a name="how-to-implement-binding-validation"></a>操作說明：實作繫結驗證
此範例示範如何使用<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>和樣式觸發程序提供視覺化回應以通知使用者，當您輸入了無效的值，根據自訂驗證規則。  
  
## <a name="example"></a>範例  
 文字內容<xref:System.Windows.Controls.TextBox>在下列範例會繫結至`Age`名為繫結來源物件的屬性 （型別 int) `ods`。 繫結是設為使用名為 `AgeRangeRule` 的驗證規則，因此如果使用者輸入非數值字元或小於 21 或大於 130 的值，文字方塊旁邊會出現紅色驚嘆號，並在使用者移動滑鼠到文字方塊上方時出現具有錯誤訊息的工具提示。  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 下列範例示範實作`AgeRangeRule`，該項則繼承自<xref:System.Windows.Controls.ValidationRule>，並覆寫<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法。 Int32.Parse() 方法會針對值呼叫，以確認當中沒有包含任何無效的字元。 <xref:System.Windows.Controls.ValidationRule.Validate%2A>方法會傳回<xref:System.Windows.Controls.ValidationResult>，指出值是否有效根據是否在剖析期間攔截到例外狀況以及年齡值是外部的下限和上限。  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 下列範例顯示的自訂<xref:System.Windows.Controls.ControlTemplate> `validationTemplate` ，會建立紅色驚嘆號，通知使用者的驗證錯誤。 控制項樣板是用於重新定義控制項的外觀。  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 下列範例所示<xref:System.Windows.Controls.ToolTip>所顯示的錯誤訊息會建立名為樣式`textBoxInError`。 如果值<xref:System.Windows.Controls.Validation.HasError%2A>已`true`，觸發程序的工具提示設定目前的<xref:System.Windows.Controls.TextBox>到其第一個驗證錯誤。 <xref:System.Windows.Data.Binding.RelativeSource%2A>設為<xref:System.Windows.Data.RelativeSourceMode.Self>，參照目前的項目。  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 如需完整範例，請參閱[繫結驗證範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159972)。  
  
 請注意，如果您未提供自訂<xref:System.Windows.Controls.Validation.ErrorTemplate%2A>預設錯誤範本會出現驗證錯誤時，提供視覺化回饋給使用者。 如需詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)中的＜資料驗證＞。 除此之外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的內建驗證規則，會攔截繫結來源屬性更新期間所擲回的例外狀況。 如需詳細資訊，請參閱<xref:System.Windows.Controls.ExceptionValidationRule>。  
  
## <a name="see-also"></a>另請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
