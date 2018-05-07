---
title: 如何：對自訂物件實作驗證邏輯
ms.date: 03/30/2017
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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>如何：對自訂物件實作驗證邏輯
這個範例示範如何實作驗證邏輯的自訂物件，然後再繫結到它。  
  
## <a name="example"></a>範例  
 您可以提供驗證邏輯商務圖層上，如果您的來源物件實作<xref:System.ComponentModel.IDataErrorInfo>，如下列範例所示：  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 在下列範例中，文字方塊的 text 屬性繫結至`Age`屬性`Person`物件，可透過資源宣告，提供的繫結`x:Key``data`。 <xref:System.Windows.Controls.DataErrorValidationRule>會檢查所產生之驗證錯誤<xref:System.ComponentModel.IDataErrorInfo>實作。  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 或者，而不是使用<xref:System.Windows.Controls.DataErrorValidationRule>，您可以設定<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>屬性`true`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [實作繫結驗證](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
