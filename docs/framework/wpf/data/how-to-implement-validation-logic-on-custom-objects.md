---
title: 如何：對自訂物件實作驗證邏輯
ms.date: 08/02/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: dbeddb5eb6996d5758717ddd2d4d5af0b6f57f3c
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "33555960"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="3afdc-102">如何：對自訂物件實作驗證邏輯</span><span class="sxs-lookup"><span data-stu-id="3afdc-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="3afdc-103">此範例示範如何對自訂物件實作驗證邏輯，然後再繫結到它。</span><span class="sxs-lookup"><span data-stu-id="3afdc-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3afdc-104">範例</span><span class="sxs-lookup"><span data-stu-id="3afdc-104">Example</span></span>  
 <span data-ttu-id="3afdc-105">您可以提供驗證邏輯的商務層上，如果您的來源物件會實作<xref:System.ComponentModel.IDataErrorInfo>，如下列範例中，以定義`Person`可實作物件<xref:System.ComponentModel.IDataErrorInfo>:</span><span class="sxs-lookup"><span data-stu-id="3afdc-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example, which defines a `Person` object that implements <xref:System.ComponentModel.IDataErrorInfo>:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="3afdc-106">在下列範例中，文字方塊的 text 屬性繫結至`Person.Age`屬性，可透過指定的資源宣告的繫結`x:Key` `data`。</span><span class="sxs-lookup"><span data-stu-id="3afdc-106">In the following example, the text property of the text box binds to the `Person.Age` property, which has been made available for binding through a resource declaration that is given the `x:Key` `data`.</span></span> <span data-ttu-id="3afdc-107"><xref:System.Windows.Controls.DataErrorValidationRule>會檢查所產生之驗證錯誤<xref:System.ComponentModel.IDataErrorInfo>實作。</span><span class="sxs-lookup"><span data-stu-id="3afdc-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 <span data-ttu-id="3afdc-108">或者，而不是使用<xref:System.Windows.Controls.DataErrorValidationRule>，您可以設定<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="3afdc-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3afdc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3afdc-109">See Also</span></span>  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [<span data-ttu-id="3afdc-110">實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="3afdc-110">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="3afdc-111">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="3afdc-111">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
