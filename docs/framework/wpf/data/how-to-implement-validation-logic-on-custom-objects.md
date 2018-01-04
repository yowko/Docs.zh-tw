---
title: "如何：對自訂物件實作驗證邏輯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5044339e1d06bddad05151b2db99d5f96d068e77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="198ac-102">如何：對自訂物件實作驗證邏輯</span><span class="sxs-lookup"><span data-stu-id="198ac-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="198ac-103">這個範例示範如何實作驗證邏輯的自訂物件，然後再繫結到它。</span><span class="sxs-lookup"><span data-stu-id="198ac-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="198ac-104">範例</span><span class="sxs-lookup"><span data-stu-id="198ac-104">Example</span></span>  
 <span data-ttu-id="198ac-105">您可以提供驗證邏輯商務圖層上，如果您的來源物件實作<xref:System.ComponentModel.IDataErrorInfo>，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="198ac-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="198ac-106">在下列範例中，文字方塊的 text 屬性繫結至`Age`屬性`Person`物件，可透過資源宣告，提供的繫結`x:Key``data`。</span><span class="sxs-lookup"><span data-stu-id="198ac-106">In the following example, the text property of the text box binds to the `Age` property of the `Person` object, which has been made available for binding through a resource declaration that is given the `x:Key``data`.</span></span> <span data-ttu-id="198ac-107"><xref:System.Windows.Controls.DataErrorValidationRule>會檢查所產生之驗證錯誤<xref:System.ComponentModel.IDataErrorInfo>實作。</span><span class="sxs-lookup"><span data-stu-id="198ac-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 <span data-ttu-id="198ac-108">或者，而不是使用<xref:System.Windows.Controls.DataErrorValidationRule>，您可以設定<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="198ac-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198ac-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="198ac-109">See Also</span></span>  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [<span data-ttu-id="198ac-110">實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="198ac-110">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="198ac-111">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="198ac-111">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
