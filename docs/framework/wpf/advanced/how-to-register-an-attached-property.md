---
title: 如何：註冊附加屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: e6b0b461552811c5b3fca46a11f087f710e3b2e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544072"
---
# <a name="how-to-register-an-attached-property"></a>如何：註冊附加屬性
此範例示範如何註冊附加屬性，以及提供公用存取子，讓您可以透過 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼使用此屬性。 附加屬性是透過 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 所定義的語法概念。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類型的大部分附加屬性也會以相依性屬性的方式實作。 您可以使用相依性屬性上任何<xref:System.Windows.DependencyObject>型別。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用相依性屬性，以註冊附加的屬性<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法。 提供者類別可以選擇提供在另一個類別上使用屬性時所適用屬性的預設中繼資料，除非該類別會覆寫中繼資料。 在此範例中，`IsBubbleSource` 屬性的預設值設定為 `false`。  
  
 附加屬性的提供者類別 (即使未註冊為相依性屬性也是一樣) 必須提供遵循命名慣例 `Set`*[AttachedPropertyName]* 和 `Get`*[AttachedPropertyName]* 的靜態 get 和 set 存取子。 這些存取子是必要的，因此正在處理的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 讀取器可以將該屬性 (property) 辨識為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的屬性 (attribute)，並解析適當的類型。  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.DependencyProperty>  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
