---
title: HOW TO：對自訂物件實作驗證邏輯
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
ms.openlocfilehash: 8520504757e9e9ec9557b84ca2608b4cb99daf62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085918"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>HOW TO：對自訂物件實作驗證邏輯
此範例示範如何對自訂物件實作驗證邏輯，然後再繫結到它。  
  
## <a name="example"></a>範例  
 您可以提供驗證邏輯的商務層上，如果您的來源物件會實作<xref:System.ComponentModel.IDataErrorInfo>，如下列範例中，以定義`Person`可實作物件<xref:System.ComponentModel.IDataErrorInfo>:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 在下列範例中，文字方塊的 text 屬性繫結至`Person.Age`屬性，可透過指定的資源宣告的繫結`x:Key` `data`。 <xref:System.Windows.Controls.DataErrorValidationRule>會檢查所產生之驗證錯誤<xref:System.ComponentModel.IDataErrorInfo>實作。  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 或者，而不是使用<xref:System.Windows.Controls.DataErrorValidationRule>，您可以設定<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>屬性設`true`。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ExceptionValidationRule>
- [實作繫結驗證](how-to-implement-binding-validation.md)
- [HOW TO 主題](data-binding-how-to-topics.md)
