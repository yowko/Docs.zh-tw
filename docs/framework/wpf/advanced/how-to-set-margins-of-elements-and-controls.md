---
title: HOW TO：設定項目和控制項的邊界
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
ms.openlocfilehash: 3263810806b6b4bbec15eadfd1f1da3a57d12698
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356269"
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>HOW TO：設定項目和控制項的邊界
此範例說明如何設定<xref:System.Windows.FrameworkElement.Margin%2A>屬性，藉由變更任何現有的屬性值的程式碼後置中的邊界。 <xref:System.Windows.FrameworkElement.Margin%2A>屬性是屬性<xref:System.Windows.FrameworkElement>基底項目，並因此會由各種不同的控制項和其他項目繼承。  
  
 此範例中以[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，使用程式碼後置檔案，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]參考。 程式碼後置會顯示在C#和 Microsoft Visual Basic 版本。  
  
## <a name="example"></a>範例  
 [!code-xaml[FEMarginProgrammatic#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
